[![AI agentų karkasų tyrinėjimas](../../../translated_images/lt/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Spustelėkite aukščiau esančią nuotrauką, kad peržiūrėtumėte pamokos vaizdo įrašą)_

# Tyrinėkite AI agentų karkasus

AI agentų karkasai yra programinės įrangos platformos, sukurtos supaprastinti AI agentų kūrimą, diegimą ir valdymą. Šios karkasai suteikia kūrėjams iš anksto paruoštus komponentus, abstrakcijas ir įrankius, kurie pagreitina sudėtingų AI sistemų kūrimą.

Šie karkasai padeda kūrėjams susitelkti į savo programų unikalius aspektus, siūlydami standartizuotus sprendimus bendroms AI agentų kūrimo problemoms. Jie pagerina mastelį, prieinamumą ir efektyvumą kuriant AI sistemas.

## Įvadas 

Ši pamoka apims:

- Kas yra AI agentų karkasai ir ką jie leidžia kūrėjams pasiekti?
- Kaip komandos gali juos naudoti greitam prototipavimui, iteracijoms ir agento galimybių tobulinimui?
- Kuo skiriasi Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> ir <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> sukurtos karkasai ir įrankiai?
- Ar galiu tiesiogiai integruoti esamus Azure ekosistemos įrankius, ar man reikalingi atskiri sprendimai?
- Kas yra Azure AI Agents paslauga ir kaip ji man padeda?

## Mokymosi tikslai

Šios pamokos tikslas yra padėti jums suprasti:

- AI agentų karkasų vaidmenį AI kūrime.
- Kaip pasinaudoti AI agentų karkasais, kad sukurtumėte intelektualius agentus.
- Pagrindines galimybes, kurias suteikia AI agentų karkasai.
- Skirtumus tarp AutoGen, Semantic Kernel ir Azure AI Agent Service.

## Kas yra AI agentų karkasai ir ką jie leidžia kūrėjams daryti?

Tradiciniai AI karkasai gali padėti integruoti AI į jūsų programas ir pagerinti jas šiais būdais:

- **Personalizavimas**: AI gali analizuoti vartotojo elgseną ir pageidavimus, kad pateiktų suasmenintas rekomendacijas, turinį ir patirtis.
Pavyzdys: transliacijos paslaugos, tokios kaip Netflix, naudoja AI siūlyti filmus ir laidas pagal peržiūros istoriją, didindamos vartotojų įsitraukimą ir pasitenkinimą.
- **Automatizavimas ir efektyvumas**: AI gali automatizuoti pasikartojančias užduotis, supaprastinti darbo eigas ir pagerinti veiklos efektyvumą.
Pavyzdys: klientų aptarnavimo programos naudoja AI varomus pokalbių robotus, kad išspręstų dažniausiai užduodamus klausimus, sumažintų atsakymų laiką ir atlaisvintų žmogiškuosius agentus sudėtingesnėms užduotims.
- **Pagerinta vartotojo patirtis**: AI gali pagerinti bendrą vartotojo patirtį, suteikdama intelektualias funkcijas, tokias kaip balso atpažinimas, natūralios kalbos apdorojimas ir prognozuojantis tekstas.
Pavyzdys: virtualūs asistentai, tokie kaip Siri ir Google Assistant, naudoja AI suprasti ir atsakyti į balso komandas, palengvindami vartotojų sąveiką su įrenginiais.

### Viskas skamba puikiai, ar ne? Tai kodėl mums reikalingas AI agentų karkasas?

AI agentų karkasai reiškia daugiau nei tik AI karkasai. Jie yra sukurti tam, kad leistų kurti intelektualius agentus, galinčius bendrauti su vartotojais, kitais agentais ir aplinka, siekiant konkrečių tikslų. Šie agentai gali būti autonomiški, priimti sprendimus ir prisitaikyti prie besikeičiančių sąlygų. Pažvelkime į keletą pagrindinių galimybių, kurias suteikia AI agentų karkasai:

- **Agentų bendradarbiavimas ir koordinacija**: leidžia kurti kelis AI agentus, kurie gali bendradarbiauti, komunikuoti ir koordinuoti veiksmus sprendžiant sudėtingas užduotis.
- **Užduočių automatizavimas ir valdymas**: teikia mechanizmus daugialypių darbo eigų automatizavimui, užduočių delegavimui ir dinaminiam užduočių valdymui tarp agentų.
- **Kontekstinis supratimas ir adaptacija**: aprūpina agentus gebėjimu suprasti kontekstą, prisitaikyti prie besikeičiančios aplinkos ir priimti sprendimus remiantis realaus laiko informacija.

Apibendrinant, agentai leidžia nuvesti automatizavimą į kitą lygmenį — kurti protingesnes sistemas, kurios gali prisitaikyti ir mokytis iš savo aplinkos.

## Kaip greitai prototipuoti, iteruoti ir tobulinti agento galimybes?

Tai greitai besikeičianti sritis, tačiau daugelyje AI agentų karkasų yra bendrų elementų, kurie padeda greitai prototipuoti ir iteruoti — tai moduliai, bendradarbiavimo įrankiai ir realaus laiko mokymasis. Panagrinėkime juos:

- **Naudokite modulius**: AI SDK siūlo iš anksto paruoštus komponentus, tokius kaip AI ir atminties jungtys, funkcijų iškvietimas naudojant natūralią kalbą arba kodo papildinius, užduočių šablonus ir kt.
- **Panaudokite bendradarbiavimo įrankius**: kurkite agentus su specifinėmis rolėmis ir užduotimis, leidžiančias išbandyti ir tobulinti bendradarbiavimo darbo eigas.
- **Mokykitės realiu laiku**: įgyvendinkite atsiliepimų ciklus, kuriuose agentai mokosi iš sąveikų ir dinamiškai koreguoja savo elgesį.

### Naudokite modulius

SDK, tokie kaip Microsoft Semantic Kernel ir LangChain, siūlo iš anksto paruoštus komponentus, tokius kaip AI jungtys, užuominų šablonai ir atminties valdymas.

**Kaip komandos gali tai naudoti**: Komandos gali greitai sukomponuoti šiuos komponentus, kad sukurtų funkcionalų prototipą be reikalo pradėti nuo nulio, taip leidžiant greitai eksperimentuoti ir iteruoti.

**Kaip tai veikia praktikoje**: Galite naudoti iš anksto paruoštą analizatorių, kad išgautumėte informaciją iš vartotojo įvesties, atminties modulį duomenų saugojimui ir gavimui bei užuominų generatorių vartotojo sąveikai — visa tai be būtinybės kurti šiuos komponentus nuo nulio.

**Pavyzdžių kodas**. Pažiūrėkime pavyzdžius, kaip galite naudoti iš anksto paruoštą AI jungtį su Semantic Kernel Python ir .Net, kuri naudoja automatinį funkcijų iškvietimą, kad modelis atsakytų į vartotojo įvestį:

``` python
# Semantic Kernel Python pavyzdys

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Apibrėžkite ChatHistory objektą, kuris saugo pokalbio kontekstą
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Apibrėžkite pavyzdinį papildinį, kuriame yra funkcija kelionei rezervuoti
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Sukurkite Kernel
kernel = Kernel()

# Pridėkite pavyzdinį papildinį prie Kernel objekto
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Apibrėžkite Azure OpenAI AI jungtį
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Apibrėžkite užklausos nustatymus, kad būtų sukonfigūruotas modelis su automatinio funkcijų kvietimo galimybe
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Atlikite užklausą modeliui su nurodytu pokalbio istorijos ir užklausos nustatymais
    # Kernel saugo pavyzdį, kurį modelis kvies vykdyti
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Pavyzdinė AI modelio atsakymas: `Jūsų skrydis į Niujorką 2025 m. sausio 1 d. buvo sėkmingai rezervuotas. Saugios kelionės! ✈️🗽`

    # Pridėkite modelio atsakymą prie mūsų pokalbio istorijos konteksto
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

Iš šio pavyzdžio matyti, kaip galite pasinaudoti iš anksto paruoštu analizatoriumi, kad išgautumėte pagrindinę informaciją iš vartotojo įvesties, pvz., skrydžio užsakymo užklausos kilmę, tikslą ir datą. Šis modulinis požiūris leidžia susitelkti į aukšto lygio logiką.

### Panaudokite bendradarbiavimo įrankius

Karkasai, tokie kaip CrewAI, Microsoft AutoGen ir Semantic Kernel, palengvina kelių agentų, galinčių dirbti kartu, kūrimą.

**Kaip komandos gali tai naudoti**: Komandos gali sukurti agentus su konkrečiomis rolėmis ir užduotimis, leidžiančias išbandyti ir tobulinti bendradarbiavimo darbo eigas bei pagerinti bendrą sistemos efektyvumą.

**Kaip tai veikia praktikoje**: Galite sukurti agentų komandą, kur kiekvienas agentas turi specializuotą funkciją, pvz., duomenų gavimą, analizę ar sprendimų priėmimą. Šie agentai gali komunikuoti ir dalintis informacija, kad pasiektų bendrą tikslą, pvz., atsakyti į vartotojo užklausą arba atlikti užduotį.

**Pavyzdžių kodas (AutoGen)**:

```python
# kuriami agentai, tada sukuriamas round robin grafikas, kuriame jie gali dirbti kartu, šiuo atveju paeiliui

# Duomenų gavimo agentas
# Duomenų analizės agentas
# Sprendimų priėmimo agentas

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# pokalbis baigiasi, kai vartotojas pasako "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Naudokite asyncio.run(...), kai vykdoma skripte.
await Console(stream)
```

Iš ankstesnio kodo matyti, kaip galite sukurti užduotį, kurioje keli agentai dirba kartu duomenų analizei. Kiekvienas agentas atlieka specifinę funkciją, o užduotis vykdoma koordinuojant agentus siekiant norimo rezultato. Kuriant skirtus agentus su specializuotomis rolėmis, galima pagerinti užduoties efektyvumą ir veikimą.

### Mokykitės realiu laiku

Pažangūs karkasai suteikia galimybes realaus laiko konteksto supratimui ir adaptacijai.

**Kaip komandos gali tai naudoti**: Komandos gali įgyvendinti atsiliepimų ciklus, kuriuose agentai mokosi iš sąveikų ir dinamiškai koreguoja savo elgesį, kas lemia nuolatinį gebėjimų tobulinimą ir rafinavimą.

**Kaip tai veikia praktikoje**: Agentai gali analizuoti vartotojų atsiliepimus, aplinkos duomenis ir užduoties rezultatus, kad atnaujintų savo žinių bazę, koreguotų sprendimų priėmimo algoritmus ir laikui bėgant pagerintų veikimą. Šis iteratyvus mokymosi procesas leidžia agentams prisitaikyti prie besikeičiančių sąlygų ir vartotojų pageidavimų, didinant sistemų efektyvumą.

## Kokie yra skirtumai tarp AutoGen, Semantic Kernel ir Azure AI Agent Service?

Yra daug būdų palyginti šiuos karkasus, bet pažvelkime į keletą pagrindinių skirtumų jų dizaino, galimybių ir tikslinių naudojimo atvejų požiūriu:

## AutoGen

AutoGen yra atviro kodo karkasas, sukurtas Microsoft Research AI Frontiers laboratorijos. Jis orientuotas į įvykių varomas, išskirstytas agentines programas, leidžiančias naudoti kelis LLM ir SLM modelius, įrankius ir pažangius daugiaagentinės architektūros šablonus.

AutoGen yra sukurtas aplink pagrindinę agentų sąvoką — tai autonominės savybės, galinčios suvokti savo aplinką, priimti sprendimus ir imtis veiksmų siekiant konkrečių tikslų. Agentai bendrauja asinchroninėmis žinutėmis, leidžiančiomis jiems veikti nepriklausomai ir lygiagrečiai, taip pagerinant sistemos mastelį ir reagavimo greitį.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agentai paremti aktorių modeliu</a>. Remiantis Vikipedija, aktorius yra _pagrindinis lygiagretios skaičiavimo konstrukcinis elementas. Gavęs pranešimą, aktorius gali: priimti vietinius sprendimus, sukurti daugiau aktorių, siųsti daugiau pranešimų ir nuspręsti, kaip atsakyti į kitą gautą pranešimą_.

**Panaudojimo atvejai**: automatizuotas kodo generavimas, duomenų analizės užduotys ir specialių agentų kūrimas planavimo bei tyrimų funkcijoms.

Štai keletas svarbių AutoGen pagrindinių sąvokų:

- **Agentai**. Agentas yra programinės įrangos subjektas, kuris:
  - **Bendrauja per žinutes**, šios žinutės gali būti sinchroninės arba asinchroninės.
  - **Išlaiko savo būseną**, kuri gali būti keičiama gaunamomis žinutėmis.
  - **Atlieka veiksmus** reaguodamas į gautas žinutes arba būsenos pokyčius. Šie veiksmai gali modifikuoti agento būseną ir sukelti išorinius efektus, pvz., atnaujinti pranešimų žurnalus, siųsti naujas žinutes, vykdyti kodą arba atlikti API užklausas.
    
  Čia turite trumpą kodo fragmentą, kuriame kuriate savo agentą su pokalbio galimybėmis:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    Ankstesniame kode `MyAgent` buvo sukurtas ir paveldi iš `RoutedAgent`. Jis turi pranešimų tvarkytuvą, kuris atspausdina pranešimo turinį, o tada siunčia atsakymą naudodamas delegatą `AssistantAgent`. Ypač atkreipkite dėmesį į tai, kaip priskiriame `self._delegate` `AssistantAgent` egzempliorių — tai iš anksto paruoštas agentas, galintis apdoroti pokalbių užbaigimus.


    Leiskime AutoGen sužinoti apie šio agento tipą ir paleiskime programą taip:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Pradėti žinučių apdorojimą foniniu režimu.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Ankstesniame kode agentai yra užregistruoti vykdymo aplinkoje, o tada agentui siunčiamas pranešimas, dėl kurio gaunamas toks išvesties rezultatas:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Daugiagentė sistema**. AutoGen palaiko kelių agentų kūrimą, kurie gali dirbti kartu siekiant sudėtingų užduočių. Agentai gali komunikuoti, dalintis informacija ir koordinuoti savo veiksmus sprendžiant problemas efektyviau. Norint sukurti daugiagentę sistemą, galite apibrėžti skirtingų tipų agentus su specializuotomis funkcijomis ir rolėmis, pavyzdžiui, duomenų gavimas, analizė, sprendimų priėmimas ir vartotojo sąveika. Pažiūrėkime, kaip toks kūrimas atrodo, kad susidarytume vaizdą:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Agent'o deklaravimo pavyzdys
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Naudojamas tema tipo kaip agento tipas.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="JŪSŲ_API_RAKTAS",
        ),
        ),
    )

    # likusios deklaracijos sutrumpintos trumpumui

    # Grupinis pokalbis
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="JŪSŲ_API_RAKTAS",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    Ankstesniame kode turime `GroupChatManager`, kuris yra užregistruotas vykdymo aplinkoje. Šis valdytojas atsakingas už skirtingų agentų tipų, tokių kaip rašytojai, iliustratoriai, redaktoriai ir vartotojai, sąveikų koordinavimą.

- **Agentų vykdymo aplinka**. Karkasas suteikia vykdymo aplinką, leidžiančią vykdyti komunikaciją tarp agentų, valdyti jų tapatybes ir gyvavimo ciklus bei užtikrinti saugumo ir privatumo ribas. Tai reiškia, kad galite paleisti savo agentus saugioje ir kontroliuojamoje aplinkoje, užtikrindami saugų ir efektyvų jų tarpusavio bendradarbiavimą. Yra dvi vykdymo aplinkos, į kurias verta atkreipti dėmesį:
  - **Atskiras vykdymo laikas**. Tai geras pasirinkimas vieno proceso programoms, kur visos agentų implementacijos yra vienoje programavimo kalboje ir veikia tame pačiame procese. Štai iliustracija, kaip tai veikia:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Atskiras vykdymo laikas</a>   
Programų sluoksnis

    *agentai bendrauja per žinutes per vykdymo aplinką, o vykdymo aplinka valdo agentų gyvavimo ciklą*

  - **Išskirstytas vykdymo laikas**, tinka daugiaprocesėms programoms, kur agentai gali būti įgyvendinti skirtingomis programavimo kalbomis ir veikti skirtinguose kompiuteriuose. Štai iliustracija, kaip tai veikia:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Išskirstytas vykdymo laikas</a>

## Semantic Kernel + agentų karkasas

Semantic Kernel yra įmonėms pritaikytas AI orkestracijos SDK. Jis susideda iš AI ir atminties jungčių bei Agentų karkaso.

Pirmiausia aptarkime keletą pagrindinių komponentų:

- **AI jungtys**: Tai sąsaja su išorinėmis AI paslaugomis ir duomenų šaltiniais, skirta naudoti tiek Python, tiek C#.

  ```python
  # Semantinis branduolio Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Čia pateiktas paprastas pavyzdys, kaip sukurti kernelį ir pridėti pokalbio užbaigimo paslaugą. Semantic Kernel sukuria jungtį su išorine AI paslauga, šiuo atveju Azure OpenAI Chat Completion.

- **Papildiniai (Plugins)**: Jie apgaubia funkcijas, kurias programa gali naudoti. Yra paruoštų papildinių ir tokių, kuriuos galite susikurti patys. Susijusi sąvoka yra „užuominų funkcijos“. Vietoje natūralios kalbos užuominų funkcijų iškvietimui, tam tikros funkcijos transliuojamos modeliui. Remdamasis esamu pokalbio kontekstu, modelis gali pasirinkti iškviesti vieną iš šių funkcijų, kad užbaigtų užklausą ar atliktų paiešką. Štai pavyzdys:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Čia pirmiausia turite šabloninę užuominą `skPrompt`, kuri palieka vietos vartotojui įvesti tekstą, `$userInput`. Tada sukuriate kernelio funkciją `SummarizeText` ir importuojate ją į kernelį su papildinio pavadinimu `SemanticFunctions`. Atkreipkite dėmesį į funkcijos pavadinimą, kuris padeda Semantic Kernel suprasti, ką funkcija daro ir kada ją reikėtų iškviesti.

- **Gimtine funkcija**: Yra ir gimtųjų funkcijų, kurias karkasas gali kviestis tiesiogiai, kad atliktų užduotį. Štai pavyzdys funkcijos, kuri gauna turinį iš failo:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Atmintis**: abstrahuoja ir supaprastina konteksto valdymą AI programoms. Idėja su atmintimi yra ta, kad tai yra informacija, kurią LLM turėtų žinoti. Šią informaciją galite saugoti vektorių saugykloje, kuri gali būti atmintinė duomenų bazė, vektorinė duomenų bazė ar panašiai. Štai labai supaprastinto scenarijaus pavyzdys, kai į atmintį pridedami *faktai*:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    Šie faktai tada saugomi atminties kolekcijoje `SummarizedAzureDocs`. Tai labai supaprastintas pavyzdys, bet galite pamatyti, kaip galite saugoti informaciją atmintyje, kad LLM galėtų ją naudoti.

Taigi tai yra Semantic Kernel karkaso pagrindai — o kaip dėl Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service yra naujesnis priedas, pristatytas Microsoft Ignite 2024. Jis leidžia kurti ir diegti AI agentus su lankstesniais modeliais, pavyzdžiui tiesiogiai kviečiant atvirojo kodo LLM'us, tokius kaip Llama 3, Mistral ir Cohere.

Azure AI Agent Service suteikia stipresnes įmonėms skirtas saugumo priemones ir duomenų saugojimo metodus, todėl tinka įmoninėms programoms. 

Jis veikia iš karto su daugagentėmis orkestravimo sistemomis, tokiomis kaip AutoGen ir Semantic Kernel.

Ši paslauga šiuo metu yra viešajame peržiūroje (Public Preview) ir palaiko Python bei C# agentų kūrimui.

Naudodami Semantic Kernel Python galime sukurti Azure AI Agent su vartotojo apibrėžtu įskiepiu:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Apibrėžkite pavyzdinį priedą pavyzdžiui
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Sukurkite agento apibrėžimą
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Sukurkite AzureAI agentą naudodami apibrėžtą klientą ir agento apibrėžimą
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Sukurkite giją pokalbio palaikymui
        # Jei gija nepateikta, bus
        # sukurta nauja gija ir grąžintas pradinys atsakymas
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Iškvieskite agentą nurodytai gijai
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Pagrindinės sąvokos

Azure AI Agent Service turi šias pagrindines sąvokas:

- **Agentas**. Azure AI Agent Service integruojasi su Microsoft Foundry. AI Foundry viduje AI agentas veikia kaip „išmanus“ mikropaslauga, kuri gali būti naudojama klausimams atsakyti (RAG), vykdyti veiksmus arba visiškai automatizuoti darbo srautus. Tai pasiekiama derinant generatyviųjų AI modelių galią su įrankiais, leidžiančiais jam pasiekti ir sąveikauti su realaus pasaulio duomenų šaltiniais. Štai pavyzdys agente:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Šiame pavyzdyje agentas sukuriamas su modeliu `gpt-4o-mini`, vardu `my-agent` ir instrukcijomis `You are helpful agent`. Agentas aprūpintas įrankiais ir ištekliais kodo interpretacijos užduotims atlikti.

- **Gija ir žinutės**. Gija yra kita svarbi sąvoka. Ji reiškia pokalbį arba sąveiką tarp agento ir vartotojo. Gijas galima naudoti stebėti pokalbio eigą, saugoti kontekstinę informaciją ir valdyti sąveikos būseną. Štai pavyzdys gijos:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    Ankstesniame kode sukurta gija. Vėliau į giją išsiunčiama žinutė. Iškvietus `create_and_process_run`, agentui prašoma atlikti darbą su gija. Galiausiai žinutės yra gaunamos ir įrašomos, kad būtų matomas agento atsakymas. Žinutės atspindi pokalbio tarp vartotojo ir agento eigą. Taip pat svarbu suprasti, kad žinutės gali būti skirtingų tipų, pavyzdžiui tekstas, vaizdas arba failas — agento darbas gali duoti, pavyzdžiui, vaizdą ar teksto atsakymą. Kaip kūrėjas, tuomet galite naudoti šią informaciją tolimesniam atsakymo apdorojimui ar jo pateikimui vartotojui.

- **Integracija su kitais AI karkasais**. Azure AI Agent Service gali sąveikauti su kitais karkasais, tokiais kaip AutoGen ir Semantic Kernel, tai reiškia, kad galite sukurti dalį savo programos viename iš šių karkasų ir, pavyzdžiui, naudoti Agent Service kaip orkestratorių arba galite sukurti viską Agent Service aplinkoje.

**Panaudojimo atvejai**: Azure AI Agent Service yra skirta įmoninėms programoms, kurioms reikalingas saugus, mastomas ir lankstus AI agentų diegimas.

## What's the difference between these frameworks?
 
Gali pasirodyti, kad tarp šių karkasų yra daug sutapimų, bet yra keletas pagrindinių skirtumų pagal jų dizainą, galimybes ir taikymo sritis:
 
- **AutoGen**: Eksperimentių karkasas, orientuotas į pažangius daugiagentės sistemos tyrimus. Tai geriausia vieta eksperimentuoti ir kurti sudėtingų daugagentinių sistemų prototipus.
- **Semantic Kernel**: Produkcijai paruošta agentų biblioteka įmoniniams agentiniams sprendimams kurti. Orientuota į įvykių valdomas, paskirstytas agentines programas, leidžiančias naudoti kelis LLM ir SLM, įrankius bei vieno/daug agentų dizaino šablonus.
- **Azure AI Agent Service**: Platforma ir diegimo paslauga Azure Foundry agentams. Ji siūlo ryšio su Azure palaikomomis paslaugomis, tokiomis kaip Azure OpenAI, Azure AI Search, Bing Search ir kodo vykdymas, integraciją.
 
Vis dar nesate tikri, kurį pasirinkti?

### Use Cases
 
Pažiūrėkime, ar galime padėti, pereidami per kelis dažniausius panaudojimo atvejus:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>
>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.
>
> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.
>
>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?
>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Apibendrinsime pagrindinius skirtumus lentelėje:

| Framework | Fokusas | Pagrindinės sąvokos | Panaudojimo atvejai |
| --- | --- | --- | --- |
| AutoGen | Įvykių valdomos, paskirstytos agentinės programos | Agentai, asmenybės, funkcijos, duomenys | Kodo generavimas, duomenų analizės užduotys |
| Semantic Kernel | Žmogaus kalbai panašaus teksto supratimas ir generavimas | Agentai, modulinės dalys, bendradarbiavimas | Natūralios kalbos supratymas, turinio generavimas |
| Azure AI Agent Service | Lankstūs modeliai, įmoninis saugumas, kodo generavimas, įrankių iškvietimas | Moduliarumas, bendradarbiavimas, procesų orkestracija | Saugus, mastomas ir lankstus AI agentų diegimas |

What's the ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Atsakymas — taip: galite tiesiogiai integruoti esamus Azure ekosistemos įrankius, ypač su Azure AI Agent Service, nes jis sukurtas sklandžiai veikti su kitomis Azure paslaugomis. Pavyzdžiui, galite integruoti Bing, Azure AI Search ir Azure Functions. Taip pat yra glaudi integracija su Microsoft Foundry.

AutoGen ir Semantic Kernel atveju taip pat galite integruotis su Azure paslaugomis, tačiau tai gali reikalauti kvietimų į Azure paslaugas iš jūsų kodo. Kitas integracijos būdas — naudoti Azure SDK, kad agentai bendrautų su Azure paslaugomis. Be to, kaip minėta, galite naudoti Azure AI Agent Service kaip orkestratorių savo AutoGen arba Semantic Kernel sukurtoms agentų sistemoms, kas suteiktų paprastą prieigą prie Azure ekosistemos.

## Pavyzdiniai kodai

- Python: [Agentų karkasas](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agentų karkasas](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Prisijunkite prie [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), susitikite su kitais besimokančiais, dalyvaukite konsultacijose ir gaukite atsakymus į savo AI agentų klausimus.

## Nuorodos

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel ir AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent paslauga</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Previous Lesson

[Įvadas į AI agentus ir jų panaudojimo atvejus](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Agentinio dizaino šablonų supratimas](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Atsakomybės apribojimas:
Šis dokumentas išverstas naudojant dirbtinio intelekto vertimo paslaugą Co-op Translator (https://github.com/Azure/co-op-translator). Nors stengiamės užtikrinti tikslumą, atkreipkite dėmesį, kad automatizuoti vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas jo gimtąja kalba turi būti laikomas autoritetingu šaltiniu. Kritinės informacijos atveju rekomenduojama kreiptis į profesionalų vertėją. Mes neatsakome už jokius nesusipratimus ar neteisingus aiškinimus, kilusius dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->