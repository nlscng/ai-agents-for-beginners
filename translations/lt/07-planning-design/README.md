[![Planuojamo dizaino šablonas](../../../translated_images/lt/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Spustelėkite aukščiau esantį paveikslėlį norėdami peržiūrėti šios pamokos vaizdo įrašą)_

# Planuojamas dizainas

## Įvadas

Ši pamoka apims

* Aiškaus bendro tikslo apibrėžimą ir sudėtingos užduoties padalijimą į valdomas užduotis.
* Struktūruoto išvesties naudojimą patikimesnėms ir mašinai suprantamoms atsakymams gauti.
* Įvykių valdomo požiūrio taikymą dinaminėms užduotims ir netikėtiems įėjimams valdyti.

## Mokymosi tikslai

Baigę šią pamoką suprasite:

* Nustatyti ir apibrėžti bendrą tikslą AI agentui, užtikrinant, kad jis aiškiai žinotų, ką reikia pasiekti.
* Sudėtingą užduotį suskaidyti į valdomas sub-užduotis ir jas organizuoti į logišką seką.
* Aprūpinti agentus tinkamais įrankiais (pvz., paieškos ar duomenų analizės įrankiais), nuspręsti kada ir kaip jie naudojami, bei valdyti netikėtas situacijas.
* Įvertinti sub-užduočių rezultatus, matuoti našumą ir tobulinti veiksmus geresniam galutiniam rezultatui.

## Bendro tikslo apibrėžimas ir užduoties padalijimas

![Tikslo ir užduočių apibrėžimas](../../../translated_images/lt/defining-goals-tasks.d70439e19e37c47a.webp)

Daugelis realių užduočių yra per daug sudėtingos, kad jas būtų galima išspręsti vienu žingsniu. AI agentui reikia glausto tikslo, kuris nukreiptų jo planavimą ir veiksmus. Pavyzdžiui, apsvarstykite tikslą:

    "Sukurti 3 dienų kelionės maršrutą."

Nors tai paprasta suformuluoti, vis tiek reikalingas patikslinimas. Kuo aiškesnis tikslas, tuo geriau agentas (ir bet kurie žmonių partneriai) gali susitelkti į teisingo rezultato pasiekimą, kaip visapusiško maršruto su skrydžių galimybėmis, viešbučių rekomendacijomis ir veiklų pasiūlymais sukūrimą.

### Užduoties suskaidymas

Didelės ar sudėtingos užduotys tampa lengviau valdomos, kai jos padalijamos į mažesnes, tikslui skirtas sub-užduotis.  
Kelionės maršruto pavyzdžiui galima suskaidyti tikslą į:

* Skrydžių rezervavimas  
* Viešbučių rezervavimas  
* Automobilio nuoma  
* Personalizavimas  

Kiekvieną sub-užduotį tada gali spręsti paskirti agentai ar procesai. Vienas agentas gali specializuotis geriausių skrydžių paieškoje, kitas – viešbučių rezervavime ir t.t. Koordinuojantis arba „žemyn tekančio“ agentas gali sujungti šiuos rezultatus į vientisą maršrutą galutiniam vartotojui.

Šis modulinis požiūris leidžia ir palaipsniui tobulinti. Pavyzdžiui, galite pridėti specializuotus agentus maisto rekomendacijoms ar vietos veikloms ir laikui bėgant tobulinti maršrutą.

### Struktūruota išvestis

Dideli kalbos modeliai (LLM) gali generuoti struktūruotą išvestį (pvz., JSON), kuri yra lengviau analizuojama ir apdorojama žemyn tekantiems agentams ar paslaugoms. Tai ypač naudinga daugiaagentiniame kontekste, kai užduotys gali būti vykdomos gavus planavimo išvestį. Trumpą apžvalgą rasite šiame <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">tinklaraščio įraše</a>.

Žemiau pateiktas Python kodo fragmentas demonstruoja paprastą planavimo agentą, kuris skaido tikslą į sub-užduotis ir generuoja struktūruotą planą:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Kelionės poskelbimo modelis
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # Norime priskirti užduotį agentui

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Norėdami autentifikuotis su modeliu, turite sukurti asmeninį prieigos žetoną (PAT) savo GitHub nustatymuose.
    # Sukurkite savo PAT žetoną sekdami instrukcijas čia: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Apibrėžkite vartotojo žinutę
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Užtikrinkite, kad atsakymo turinys būtų galiojantis JSON eilutė prieš ją įkeliant
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# jei response_content yra None:
#     padidinkite ValueError("Atsakymo turinys nėra galiojanti JSON eilutė")

# # Išspausdinkite atsakymo turinį po JSON įkėlimo
# pprint(json.loads(response_content))

# Patikrinkite atsakymo turinį su MathReasoning modeliu
# TravelPlan.model_validate(json.loads(response_content))
```

### Planavimo agentas su daugiaagentine koordinacija

Šiame pavyzdyje Semantikos maršrutizatoriaus agentas gauna vartotojo užklausą (pvz., "Man reikia viešbučio plano mano kelionei.").

Planavimo agentas:

* Gaukite viešbučio planą: Planavimo agentas gauna vartotojo žinutę ir, remdamasis sistemos užklausa (įskaitant prieinamus agentus), sukuria struktūruotą kelionės planą.
* Išvardina agentus ir jų įrankius: Agentų registras laiko agentų sąrašą (pvz., skrydžio, viešbučių, automobilių nuomos ir veiklų) kartu su jų siūlomomis funkcijomis arba įrankiais.
* Nukreipia planą atitinkamiems agentams: Priklausomai nuo sub-užduočių skaičiaus, planuotojas arba tiesiogiai siunčia žinutę dedicikotiems agentams (vienos užduoties atvejais), arba koordinuoja per grupės pokalbių valdymą daugiaagentiniam bendradarbiavimui.
* Apibendrina rezultatą: Galiausiai planuotojas apibendrina sukurtą planą aiškumui.
Žemiau pateiktas Python kodo pavyzdys iliustruoja šiuos veiksmus:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Kelionės pagalužduoties modelis

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # norime priskirti užduotį agentui

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Sukurkite klientą su tipo tikrinamais aplinkos kintamaisiais

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Apibrėžkite naudotojo pranešimą

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Užtikrinkite, kad atsakymo turinys būtų galiojantis JSON eilutė prieš jį įkeliant

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Atspausdinkite atsakymo turinį po įkėlimo kaip JSON

pprint(json.loads(response_content))
```

Toliau pateikiama ankstesnio kodo rezultatas, kurį galite naudoti struktūruotai išvestiai nukreipti į `assigned_agent` ir apibendrinti kelionės planą galutiniam vartotojui.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Pavyzdinė užrašinė su ankstesniu kodo pavyzdžiu yra prieinama [čia](07-autogen.ipynb).

### Iteratyvus planavimas

Kai kurios užduotys reikalauja eiga atgal arba perplanavimo, kai vienos sub-užduoties rezultatas įtakoja kitą. Pavyzdžiui, jei agentas aptinka netikėtą duomenų formatą rezervuojant skrydžius, jam gali reikėti pakeisti strategiją prieš pradedant viešbučių rezervavimą.

Taip pat vartotojo atsiliepimai (pvz., kai žmogus nusprendžia, kad nori anksčiau skristi) gali sukelti dalinį perplanavimą. Šis dinamiškas, iteratyvus požiūris užtikrina, kad galutinis sprendimas atitiktų realaus pasaulio apribojimus ir kintančius vartotojo pageidavimus.

pvz. pavyzdinis kodas

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. tas pats kaip ankstesniame kode ir perduoti vartotojo istoriją, dabartinį planą
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. pertvarkyti planą ir siųsti užduotis atitinkamiems agentams
```

Dėl išsamesnio planavimo žr. Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Tinklaraščio įrašą</a> apie sudėtingų užduočių sprendimą.

## Santrauka

Šiame straipsnyje aptarėme pavyzdį, kaip kurti planuotoją, kuris dinamiškai pasirenka apibrėžtus agentus. Planavimo išvestis suskaido užduotis ir paskiria agentus jų vykdymui. Daroma prielaida, kad agentai turi prieigą prie reikalingų funkcijų/įrankių užduočiai atlikti. Be agentų, galite pridėti kitus modelius, tokius kaip refleksija, santraukų kūrėjas ir round-robin pokalbis, kad dar labiau pritaikytumėte procesą.

## Papildomi ištekliai

AutoGen Magnetic One – universalus daugiaagentis sistema sudėtingų užduočių sprendimui, pasiekusi įspūdingų rezultatų keliuose sudėtinguose agentų testuose. Nuoroda: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Šiame įgyvendinime koordinuojantis komponentas kuria užduočiai specifinį planą ir deleguoja užduotis prieinamoms agentų grupėms. Be planavimo, koordinuojantysis taip pat naudoja stebėjimo mechanizmą užduoties progresui sekti ir būtinybės atveju planuoti iš naujo.

### Turite daugiau klausimų apie planavimo dizaino šabloną?

Prisijunkite prie [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kad susitikti su kitais besimokančiaisiais, dalyvauti konsultacijose ir gauti atsakymus į savo AI agentų klausimus.

## Ankstesnė pamoka

[Statome patikimus AI agentus](../06-building-trustworthy-agents/README.md)

## Kitoji pamoka

[Daugiaagentinis dizaino šablonas](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors siekiame tikslumo, prašome atkreipti dėmesį, kad automatiniai vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Svarbiai informacijai rekomenduojamas profesionalus žmogaus atliktas vertimas. Mes neprisiimame atsakomybės už bet kokius nesusipratimus ar neteisingus aiškinimus, kylantį iš šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->