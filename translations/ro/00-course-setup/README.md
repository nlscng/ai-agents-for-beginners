# Configurarea Cursului

## Introducere

Această lecție va acoperi cum să rulați exemplele de cod ale acestui curs.

## Alăturați-vă altor cursanți și primiți ajutor

Înainte de a începe să clonați repo-ul, alăturați-vă [canalului Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) pentru a primi orice ajutor legat de configurare, întrebări despre curs sau pentru a vă conecta cu alți cursanți.

## Clonați sau Faceți Fork la acest Repo

Pentru a începe, vă rog să clonați sau să faceți fork la Repositorul GitHub. Aceasta va crea propria dvs. versiune a materialului de curs astfel încât să puteți rula, testa și modifica codul!

Acest lucru se poate face făcând clic pe linkul <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">faceți fork la repo</a>

Acum ar trebui să aveți propria versiune fork-uită a acestui curs la linkul următor:

![Forked Repo](../../../translated_images/ro/forked-repo.33f27ca1901baa6a.webp)

### Clonare superficială (recomandată pentru workshop / Codespaces)

  > Repositorul complet poate fi mare (~3 GB) când descărcați istoricul complet și toate fișierele. Dacă participați doar la workshop sau aveți nevoie doar de câteva foldere cu lecții, o clonare superficială (sau clonare rară) evită majoritatea acestei descărcări prin trunchierea istoricului și/sau sărind peste blobs.

#### Clonare superficială rapidă — istoric minim, toate fișierele

Înlocuiți `<your-username>` în comenzile de mai jos cu URL-ul fork-ului dvs. (sau URL-ul upstream dacă preferați).

Pentru a clona doar istoricul ultimului commit (descărcare mică):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Pentru a clona o anumită ramură:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Clonare parțială (rară) — blobs minime + doar foldere selectate

Aceasta folosește clonarea parțială și sparse-checkout (necesită Git 2.25+ și este recomandat Git modern cu suport pentru clonare parțială):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Intrați în folderul repo:

```bash|powershell
cd ai-agents-for-beginners
```

Apoi specificați ce foldere doriți (exemplul de mai jos arată două foldere):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

După clonare și verificarea fișierelor, dacă aveți nevoie doar de fișiere și vreți să eliberați spațiu (fără istoric git), vă rugăm să ștergeți meta-datele repository-ului (💀 ireversibil — veți pierde toată funcționalitatea Git: nu veți mai putea face commituri, pull-uri, push-uri sau acces istoricul).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Folosind GitHub Codespaces (recomandat pentru a evita descărcări mari locale)

- Creați un nou Codespace pentru acest repo prin [interfața GitHub UI](https://github.com/codespaces).  

- În terminalul noului codespace creat, rulați una dintre comenzile shallow/sparse clone de mai sus pentru a aduce doar folderele lecțiilor de care aveți nevoie în spațiul de lucru Codespace.
- Opțional: după clonare în Codespaces, eliminați folderul .git pentru a recupera spațiu suplimentar (vedeți comenzile de ștergere de mai sus).
- Notă: Dacă preferați să deschideți repo-ul direct în Codespaces (fără clonare suplimentară), fiți conștienți că Codespaces va construi mediul devcontainer și poate provisiona mai mult decât aveți nevoie. Clonarea unei copii superficiale într-un Codespace nou vă oferă mai mult control asupra utilizării discului.

#### Sfaturi

- Înlocuiți întotdeauna URL-ul de clonare cu fork-ul dvs. dacă doriți să editați/commitați.
- Dacă aveți nevoie mai târziu de mai mult istoric sau fișiere, puteți să le recuperați sau să ajustați sparse-checkout pentru a include foldere suplimentare.

## Rularea Codului

Acest curs oferă o serie de Jupyter Notebooks pe care le puteți rula pentru a obține experiență practică în construirea de Agenți AI.

Exemplele de cod folosesc fie:

**Necesită cont GitHub - Gratuit**:

1) Framework Semantic Kernel Agent + GitHub Models Marketplace. Etichetat ca (semantic-kernel.ipynb)
2) Framework AutoGen + GitHub Models Marketplace. Etichetat ca (autogen.ipynb)

**Necesită abonament Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Etichetat ca (azureaiagent.ipynb)

Vă încurajăm să încercați toate cele trei tipuri de exemple pentru a vedea care funcționează cel mai bine pentru dvs.

Oricare opțiune alegeți, aceasta va determina pașii de configurare pe care trebuie să-i urmați mai jos:

## Cerințe

- Python 3.12+
  - **NOTĂ**: Dacă nu aveți instalat Python3.12, asigurați-vă că îl instalați. Apoi creați mediul virtual folosind python3.12 pentru a vă asigura că versiunea corectă este instalată din fișierul requirements.txt.
  
    >Exemplu

    Creați directorul pentru mediul virtual Python:

    ```bash|powershell
    python -m venv venv
    ```

    Apoi activați mediul virtual pentru:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Pentru codurile de exemplu care folosesc .NET, asigurați-vă că instalați [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) sau o versiune mai recentă. Apoi verificați versiunea SDK .NET instalată:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Un cont GitHub - Pentru acces la GitHub Models Marketplace
- Un abonament Azure - Pentru acces la Microsoft Foundry
- Cont Microsoft Foundry - Pentru acces la Azure AI Agent Service

Am inclus un fișier `requirements.txt` în rădăcina acestui repository care conține toate pachetele Python necesare pentru a rula exemplele de cod.

Le puteți instala rulând comanda următoare în terminal, în rădăcina repository-ului:

```bash|powershell
pip install -r requirements.txt
```

Recomandăm crearea unui mediu virtual Python pentru a evita conflicte și probleme.

## Configurarea VSCode

Asigurați-vă că folosiți versiunea corectă de Python în VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Configurarea pentru Exemplele care folosesc GitHub Models 

### Pasul 1: Obțineți Token-ul Personal de Acces GitHub (PAT)

Acest curs folosește GitHub Models Marketplace, oferind acces gratuit la Large Language Models (LLMs) pe care le veți folosi pentru a construi Agenți AI.

Pentru a folosi GitHub Models, va trebui să creați un [Token Personal de Acces GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Acest lucru se face accesând <a href="https://github.com/settings/personal-access-tokens" target="_blank">setările Token-urilor Personale de Acces</a> în contul dvs. GitHub.

Vă rugăm să urmați [Principiul cel mai mic privilegiu](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) când creați token-ul. Aceasta înseamnă că ar trebui să acordați token-ului doar permisiunile necesare pentru rularea exemplelor de cod din acest curs.

1. Selectați opțiunea `Fine-grained tokens` pe partea stângă a ecranului accesând **Developer settings**

   ![Developer settings](../../../translated_images/ro/profile_developer_settings.410a859fe749c755.webp)

   Apoi selectați `Generate new token`.

   ![Generate Token](../../../translated_images/ro/fga_new_token.1c1a234afe202ab3.webp)

2. Introduceți un nume descriptiv pentru token-ul dvs. care să reflecte scopul său, pentru a-l putea identifica ușor ulterior.

    🔐 Recomandare Durată Token

    Durată recomandată: 30 zile
    Pentru o poziție mai sigură, puteți opta pentru o perioadă mai scurtă — cum ar fi 7 zile 🛡️
    Este o metodă excelentă pentru a vă seta un obiectiv personal și a finaliza cursul în timp ce sunteți motivați 🚀.

    ![Token Name and Expiration](../../../translated_images/ro/token-name-expiry-date.a095fb0de6386864.webp)

3. Limitați domeniul token-ului la fork-ul acestui repository.

    ![Limit scope to fork repository](../../../translated_images/ro/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restricționați permisiunile token-ului: Sub **Permissions**, faceți clic pe fila **Account** și apăsați butonul "+ Add permissions". Va apărea un meniu dropdown. Căutați **Models** și bifați caseta.

    ![Add Models Permission](../../../translated_images/ro/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verificați permisiunile necesare înainte de generarea token-ului. ![Verify Permissions](../../../translated_images/ro/verify_permissions.06bd9e43987a8b21.webp)

6. Înainte de generarea token-ului asigurați-vă că sunteți pregătit să îl depozitați într-un loc sigur, cum ar fi un manager de parole, deoarece acesta nu va mai fi afișat după crearea sa. ![Store Token Securely](../../../translated_images/ro/store_token_securely.08ee2274c6ad6caf.webp)

Copiați token-ul nou creat. Acum îl veți adăuga în fișierul `.env` inclus în acest curs.

### Pasul 2: Creați fișierul `.env`

Pentru a crea fișierul `.env`, rulați comanda următoare în terminal:

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Aceasta va copia fișierul exemplu și va crea un `.env` în directorul dvs. unde veți completa valorile variabilelor de mediu.

Cu token-ul copiat, deschideți fișierul `.env` în editorul dvs. preferat și lipiți token-ul în câmpul `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/ro/github_token_field.20491ed3224b5f4a.webp)

Ar trebui acum să puteți rula exemplele de cod ale acestui curs.

## Configurarea pentru Exemplele care folosesc Microsoft Foundry și Azure AI Agent Service

### Pasul 1: Obțineți Endpoint-ul Proiectului Azure


Urmăriți pașii pentru crearea unui hub și a unui proiect în Azure AI Foundry descriși aici: [Prezentare generală resurse hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Odată ce ați creat proiectul, va trebui să obțineți string-ul de conexiune pentru proiectul dvs.

Acest lucru se face accesând pagina **Overview** (Prezentare generală) a proiectului dvs. în portalul Microsoft Foundry.

![Project Connection String](../../../translated_images/ro/project-endpoint.8cf04c9975bbfbf1.webp)

### Pasul 2: Creați fișierul `.env`

Pentru a crea fișierul `.env`, rulați comanda următoare în terminal:

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Aceasta va copia fișierul exemplu și va crea un `.env` în directorul dvs. unde veți completa valorile variabilelor de mediu.

Cu token-ul copiat, deschideți fișierul `.env` în editorul dvs. preferat și lipiți token-ul în câmpul `PROJECT_ENDPOINT`.

### Pasul 3: Autentificați-vă în Azure

Ca o practică recomandată de securitate, vom folosi [autentificare fără cheie](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) pentru autentificarea la Azure OpenAI cu Microsoft Entra ID.

Apoi, deschideți un terminal și rulați `az login --use-device-code` pentru a vă conecta la contul dvs. Azure.

După autentificare, selectați abonamentul în terminal.

## Variabile de Mediu Suplimentare - Azure Search și Azure OpenAI

Pentru Lecția Agentic RAG - Lecția 5 - există exemple care folosesc Azure Search și Azure OpenAI.

Dacă doriți să rulați aceste exemple, va trebui să adăugați următoarele variabile de mediu în fișierul `.env`:

### Pagina Overview (Proiect)

- `AZURE_SUBSCRIPTION_ID` - Verificați **Detalii proiect** pe pagina **Overview** a proiectului dvs.

- `AZURE_AI_PROJECT_NAME` - Uitați-vă în partea de sus a paginii **Overview** a proiectului.

- `AZURE_OPENAI_SERVICE` - Găsiți în fila **Capabilități incluse** pentru **Azure OpenAI Service** pe pagina **Overview**.

### Centrul de Management

- `AZURE_OPENAI_RESOURCE_GROUP` - Accesați **Proprietăți proiect** pe pagina **Overview** a **Management Center**.

- `GLOBAL_LLM_SERVICE` - Sub **Resurse conectate**, găsiți numele conexiunii **Azure AI Services**. Dacă nu este listat, verificați în **portalul Azure** în grupul dvs. de resurse pentru numele resursei AI Services.

### Pagina Modele + Endpoint-uri

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Selectați modelul embedding (ex. `text-embedding-ada-002`) și notați **Numele implementării** din detaliile modelului.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Selectați modelul chat (ex. `gpt-4o-mini`) și notați **Numele implementării** din detaliile modelului.

### Portal Azure

- `AZURE_OPENAI_ENDPOINT` - Căutați **Azure AI services**, faceți clic pe el, apoi mergeți la **Resource Management**, **Chei și Endpoint**, derulați până la "endpoint-urile Azure OpenAI" și copiați cel care spune "Language APIs".

- `AZURE_OPENAI_API_KEY` - Din aceeași pagină, copiați CHEIA 1 sau CHEIA 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Găsiți resursa **Azure AI Search**, faceți clic pe ea și vedeți **Overview**.

- `AZURE_SEARCH_API_KEY` - Apoi mergeți la **Settings** și apoi **Keys** pentru a copia cheia principală sau secundară de administrator.

### Pagină web externă

- `AZURE_OPENAI_API_VERSION` - Vizitați pagina [ciclului de viață al versiunii API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) la secțiunea **Cea mai recentă versiune GA a API-ului**.

### Configurarea autentificării fără cheie

În loc să hardcodați acreditările, vom folosi o conexiune fără cheie cu Azure OpenAI. Pentru aceasta vom importa `DefaultAzureCredential` și mai târziu vom apela funcția `DefaultAzureCredential` pentru a obține acreditările.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Blocare Undeva?
Dacă întâmpinați probleme la rularea acestei configurații, intrați în <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord-ul Comunității Azure AI</a> sau <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">creați un issue</a>.

## Lecția următoare

Acum sunteți gata să rulați codul pentru acest curs. Spor la învățat mai multe despre lumea Agenților AI!

[Introducere în Agenții AI și Cazurile de Utilizare ale Agenților](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:  
Acest document a fost tradus folosind serviciul de traducere automată AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original, în limba sa nativă, trebuie considerat sursa autorizată. Pentru informații critice, se recomandă traducerea profesională realizată de un specialist uman. Nu ne asumăm răspunderea pentru orice neînțelegeri sau interpretări greșite ce pot rezulta din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->