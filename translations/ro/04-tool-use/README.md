[![Cum să proiectezi agenți AI buni](../../../translated_images/ro/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Faceți clic pe imaginea de mai sus pentru a viziona videoclipul acestei lecții)_

# Tipar de proiectare: Utilizarea instrumentelor

Instrumentele sunt interesante deoarece le permit agenților AI să aibă un spectru mai larg de capabilități. În loc ca agentul să aibă un set limitat de acțiuni pe care le poate realiza, prin adăugarea unui instrument, agentul poate acum executa o gamă largă de acțiuni. În acest capitol, vom analiza Tiparul de proiectare pentru utilizarea instrumentelor, care descrie cum agenții AI pot folosi instrumente specifice pentru a-și atinge obiectivele.

## Introducere

În această lecție, încercăm să răspundem la următoarele întrebări:

- Ce este tiparul de proiectare pentru utilizarea instrumentelor?
- În ce cazuri de utilizare poate fi aplicat?
- Care sunt elementele/blocurile de construcție necesare pentru a implementa tiparul de proiectare?
- Care sunt considerațiile speciale pentru utilizarea Tiparului de proiectare pentru utilizarea instrumentelor pentru a construi agenți AI de încredere?

## Obiective de învățare

După finalizarea acestei lecții, veți putea:

- Defini Tiparul de proiectare pentru utilizarea instrumentelor și scopul său.
- Identifica cazuri de utilizare în care Tiparul de proiectare pentru utilizarea instrumentelor este aplicabil.
- Înțelege elementele cheie necesare pentru a implementa tiparul de proiectare.
- Recunoaște considerațiile pentru asigurarea încrederii în agenții AI care utilizează acest tipar de proiectare.

## Ce este Tiparul de proiectare pentru utilizarea instrumentelor?

Tiparul de proiectare pentru utilizarea instrumentelor se concentrează pe oferirea LLM-urilor (Modele Lingvistice Mari) a capacității de a interacționa cu instrumente externe pentru a atinge scopuri specifice. Instrumentele sunt cod care poate fi executat de un agent pentru a efectua acțiuni. Un instrument poate fi o funcție simplă, cum ar fi un calculator, sau un apel API către un serviciu terț, cum ar fi interogarea prețului unei acțiuni sau prognoza meteo. În contextul agenților AI, instrumentele sunt proiectate pentru a fi executate de agenți ca răspuns la apeluri de funcții generate de model.

## În ce cazuri de utilizare poate fi aplicat?

Agenții AI pot valorifica instrumentele pentru a finaliza sarcini complexe, a recupera informații sau a lua decizii. Tiparul de proiectare pentru utilizarea instrumentelor este adesea folosit în scenarii care necesită interacțiune dinamică cu sisteme externe, cum ar fi baze de date, servicii web sau interpretoare de cod. Această abilitate este utilă pentru o serie de cazuri de utilizare, inclusiv:

- Dynamic Information Retrieval: Agenții pot interoga API-uri externe sau baze de date pentru a obține date actualizate (de ex., interogarea unei baze de date SQLite pentru analiză de date, obținerea prețurilor acțiunilor sau a informațiilor meteo).
- Code Execution and Interpretation: Agenții pot executa cod sau scripturi pentru a rezolva probleme matematice, a genera rapoarte sau a realiza simulări.
- Workflow Automation: Automatizarea fluxurilor de lucru repetitive sau în mai mulți pași prin integrarea unor instrumente precum programatoare de sarcini, servicii de email sau pipeline-uri de date.
- Customer Support: Agenții pot interacționa cu sisteme CRM, platforme de ticketing sau baze de cunoștințe pentru a rezolva cererile utilizatorilor.
- Content Generation and Editing: Agenții pot folosi instrumente precum verificatoare gramaticale, sumarizatoare de text sau evaluatoare de siguranță a conținutului pentru a asista în sarcinile de creare de conținut.

## Care sunt elementele/blocurile de construcție necesare pentru implementarea tiparului de utilizare a instrumentelor?

Aceste blocuri de construcție permit agentului AI să execute o gamă largă de sarcini. Să analizăm elementele cheie necesare pentru implementarea Tiparului de proiectare pentru utilizarea instrumentelor:

- Function/Tool Schemas: Definiții detaliate ale instrumentelor disponibile, inclusiv numele funcției, scopul, parametrii necesari și rezultatele așteptate. Aceste scheme permit LLM-ului să înțeleagă ce instrumente sunt disponibile și cum să construiască cereri valide.

- Function Execution Logic: Guvernează cum și când sunt invocate instrumentele pe baza intenției utilizatorului și a contextului conversației. Aceasta poate include module de planificare, mecanisme de rutare sau fluxuri condiționale care determină utilizarea instrumentelor în mod dinamic.

- Message Handling System: Componente care gestionează fluxul conversațional între intrările utilizatorului, răspunsurile LLM, apelurile către instrumente și rezultatele instrumentelor.

- Tool Integration Framework: Infrastructura care conectează agentul la diverse instrumente, fie că sunt funcții simple sau servicii externe complexe.

- Error Handling & Validation: Mecanisme pentru a gestiona eșecurile în execuția instrumentelor, a valida parametrii și a trata răspunsurile neașteptate.

- State Management: Urmărește contextul conversației, interacțiunile anterioare cu instrumentele și datele persistente pentru a asigura consistența în interacțiunile multi-turn.

Următorul pas, să privim în detaliu Apelarea Funcțiilor/Instrumentelor.
 
### Apelarea Funcțiilor/Instrumentelor

Apelarea funcțiilor este modalitatea principală prin care permitem Modelelor Lingvistice Mari (LLM-urilor) să interacționeze cu instrumentele. Veți vedea adesea 'Function' și 'Tool' folosite interschimbabil deoarece 'funcțiile' (blocuri de cod reutilizabile) sunt 'instrumentele' pe care agenții le folosesc pentru a îndeplini sarcini. Pentru ca codul unei funcții să fie invocat, un LLM trebuie să compare cererea utilizatorului cu descrierea funcțiilor. Pentru aceasta, o schemă care conține descrierile tuturor funcțiilor disponibile este trimisă LLM-ului. LLM-ul selectează apoi funcția cea mai potrivită pentru sarcină și returnează numele și argumentele acesteia. Funcția selectată este invocată, răspunsul ei este trimis înapoi la LLM, care folosește informațiile pentru a răspunde la cererea utilizatorului.

Pentru ca dezvoltatorii să implementeze apelarea funcțiilor pentru agenți, veți avea nevoie de:

1. Un model LLM care suportă apelarea funcțiilor
2. O schemă care conține descrierile funcțiilor
3. Codul pentru fiecare funcție descrisă

Să folosim exemplul obținerii orei curente într-un oraș pentru a ilustra:

1. **Inițializați un LLM care suportă apelarea funcțiilor:**

    Nu toate modelele suportă apelarea funcțiilor, așadar este important să verificați că LLM-ul pe care îl utilizați o acceptă.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> suportă apelarea funcțiilor. Putem începe prin a iniția clientul Azure OpenAI. 

    ```python
    # Inițializează clientul Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Creați o schemă de funcție**:

    În continuare vom defini o schemă JSON care conține numele funcției, descrierea a ceea ce face funcția și numele și descrierile parametrilor funcției.
    Apoi vom prelua această schemă și o vom transmite clientului creat anterior, împreună cu cererea utilizatorului de a afla ora în San Francisco. Ceea ce este important de remarcat este că un **apel la instrument** este ceea ce este returnat, **nu** răspunsul final la întrebare. După cum s-a menționat anterior, LLM-ul returnează numele funcției pe care a selectat-o pentru sarcină și argumentele care vor fi transmise acesteia.

    ```python
    # Descrierea funcției pentru ca modelul să o citească
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # Mesajul inițial al utilizatorului
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Primul apel API: Cere modelului să folosească funcția
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Procesează răspunsul modelului
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Codul funcției necesar pentru a realiza sarcina:**

    Acum că LLM-ul a ales ce funcție trebuie rulată, codul care realizează sarcina trebuie implementat și executat.
    Putem implementa codul pentru a obține ora curentă în Python. De asemenea, va trebui să scriem codul pentru a extrage numele și argumentele din response_message pentru a obține rezultatul final.

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # Gestionează apelurile funcțiilor
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # Al doilea apel API: Obține răspunsul final de la model
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

Apelarea Funcțiilor se află în centrul majorității, dacă nu al tuturor, proiectelor de utilizare a instrumentelor pentru agenți; totuși implementarea de la zero poate fi uneori provocatoare.
Așa cum am învățat în [Lesson 2](../../../02-explore-agentic-frameworks), cadrele agentice ne oferă blocuri de construcție predefinite pentru a implementa utilizarea instrumentelor.
 
## Exemple de utilizare a instrumentelor cu cadre agentice

Iată câteva exemple despre cum puteți implementa Tiparul de proiectare pentru utilizarea instrumentelor folosind diferite cadre agentice:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> este un cadru AI open-source pentru dezvoltatorii .NET, Python și Java care lucrează cu Modele Lingvistice Mari (LLM-uri). Simplifică procesul de utilizare a apelării funcțiilor prin descrierea automată a funcțiilor și a parametrilor acestora pentru model printr-un proces numit <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializare</a>. De asemenea, gestionează comunicarea dus-întors între model și codul dvs. Un alt avantaj al utilizării unui cadru agentic precum Semantic Kernel este că vă permite să accesați instrumente preconstruite precum <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> și <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Diagrama următoare ilustrează procesul de apelare a funcțiilor cu Semantic Kernel:

![function calling](../../../translated_images/ro/functioncalling-diagram.a84006fc287f6014.webp)

În Semantic Kernel, funcțiile/instrumentele sunt numite <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Putem converti funcția `get_current_time` pe care am văzut-o mai devreme într-un plugin transformând-o într-o clasă care conține funcția. De asemenea, putem importa decoratorul `kernel_function`, care preia descrierea funcției. Când creați un kernel cu GetCurrentTimePlugin, kernelul va serializa automat funcția și parametrii acesteia, creând schema care va fi trimisă către LLM în acest proces.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# Creează kernelul
kernel = Kernel()

# Creează pluginul
get_current_time_plugin = GetCurrentTimePlugin(location)

# Adaugă pluginul în kernel
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> este un cadru agentic mai nou, proiectat pentru a permite dezvoltatorilor să construiască, să implementeze și să scaleze în siguranță agenți AI extensibili și de înaltă calitate fără a fi nevoie să gestioneze resursele de calcul și stocare subiacente. Este deosebit de util pentru aplicațiile enterprise, deoarece este un serviciu complet gestionat cu securitate la nivel enterprise.

Comparativ cu dezvoltarea directă cu API-ul LLM, Azure AI Agent Service oferă câteva avantaje, inclusiv:

- Apelare automată a instrumentelor – nu este necesar să analizați un apel la instrument, să invocați instrumentul și să gestionați răspunsul; toate acestea se realizează acum pe server
- Date gestionate în siguranță – în loc să vă gestionați propriul stoc de conversații, vă puteți baza pe threads pentru a stoca toate informațiile de care aveți nevoie
- Instrumente disponibile din cutie – Instrumente pe care le puteți folosi pentru a interacționa cu sursele dvs. de date, cum ar fi Bing, Azure AI Search și Azure Functions.

Instrumentele disponibile în Azure AI Agent Service pot fi împărțite în două categorii:

1. Knowledge Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Action Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service ne permite să folosim aceste instrumente împreună ca un `toolset`. De asemenea, utilizează `threads` care țin evidența istoricului mesajelor dintr-o anumită conversație.

Imaginați-vă că sunteți un agent de vânzări la o companie numită Contoso. Doriți să dezvoltați un agent conversațional care să poată răspunde la întrebări despre datele dvs. de vânzări.

Imaginea următoare ilustrează cum ați putea folosi Azure AI Agent Service pentru a analiza datele de vânzări:

![Agentic Service In Action](../../../translated_images/ro/agent-service-in-action.34fb465c9a84659e.webp)

Pentru a folosi oricare dintre aceste instrumente cu serviciul, putem crea un client și defini un instrument sau un set de instrumente. Pentru a implementa acest lucru practic, putem folosi următorul cod Python. LLM-ul va putea analiza toolset-ul și decide dacă să folosească funcția creată de utilizator, `fetch_sales_data_using_sqlite_query`, sau Code Interpreter-ul preconstruit în funcție de cererea utilizatorului.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # funcția fetch_sales_data_using_sqlite_query care poate fi găsită într-un fișier fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inițializează setul de instrumente
toolset = ToolSet()

# Inițializează agentul de apelare a funcțiilor cu funcția fetch_sales_data_using_sqlite_query și îl adaugă la setul de instrumente
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inițializează instrumentul Code Interpreter și îl adaugă la setul de instrumente.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Care sunt considerațiile speciale pentru utilizarea Tiparului de proiectare pentru utilizarea instrumentelor pentru a construi agenți AI de încredere?

O preocupare comună legată de SQL-ul generat dinamic de LLM-uri este securitatea, în special riscul de injecție SQL sau acțiuni malițioase, cum ar fi ștergerea sau manipularea bazei de date. Deși aceste preocupări sunt valide, ele pot fi atenuate eficient prin configurarea corectă a permisiunilor de acces la baza de date. Pentru majoritatea bazelor de date, aceasta implică configurarea bazei de date ca fiind doar pentru citire. Pentru servicii de baze de date precum PostgreSQL sau Azure SQL, aplicației ar trebui să i se atribuie un rol doar pentru citire (SELECT).

Rularea aplicației într-un mediu securizat sporește în continuare protecția. În scenarii enterprise, datele sunt de obicei extrase și transformate din sistemele operaționale într-o bază de date doar pentru citire sau într-un data warehouse cu un schemă ușor de utilizat. Această abordare asigură că datele sunt securizate, optimizate pentru performanță și accesibilitate și că aplicația are acces restricționat, doar pentru citire.

## Exemple de cod (Sample Codes)
- Python: [Cadru pentru agenți](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Cadru pentru agenți](./code_samples/04-dotnet-agent-framework.md)

## Aveți mai multe întrebări despre modelele de proiectare pentru utilizarea instrumentelor?

Alăturați-vă [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la orele de consultații și a primi răspunsuri la întrebările dvs. despre agenții AI.

## Resurse suplimentare

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Atelier Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Atelier multi-agent Contoso Creative Writer</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Tutorial despre apelarea funcțiilor în Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpreter de cod Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Instrumente Autogen</a>

## Lecția precedentă

[Înțelegerea modelelor de proiectare agentice](../03-agentic-design-patterns/README.md)

## Lecția următoare

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Declinare de responsabilitate:
Acest document a fost tradus folosind serviciul de traducere automată AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original, în limba sa nativă, trebuie considerat sursa autoritară. Pentru informații critice se recomandă o traducere profesională realizată de un traducător uman. Nu ne asumăm nicio răspundere pentru eventualele neînțelegeri sau interpretări greșite care rezultă din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->