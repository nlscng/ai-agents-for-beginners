# Kurso nustatymas

## Įvadas

Ši pamoka apims, kaip paleisti šio kurso kodo pavyzdžius.

## Prisijunk prie kitų besimokančiųjų ir gauk pagalbą

Prieš pradėdami klonuoti savo saugyklą, prisijunkite prie [AI Agents For Beginners Discord kanalas](https://aka.ms/ai-agents/discord), kad gautumėte pagalbą diegiant, užduotumėte klausimus apie kursą arba susisiektumėte su kitais besimokančiaisiais.

## Klonuoti arba atšakoti (fork) šią saugyklą

Norėdami pradėti, klonuokite arba atšakokite GitHub saugyklą. Tai sukurs jūsų versiją su kurso medžiaga, kad galėtumėte paleisti, testuoti ir koreguoti kodą!

Tai galima padaryti spustelėjus nuorodą į <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">sukurti fork'ą saugyklos</a>

Dabar turėtumėte turėti savo fork'intą šio kurso versiją šioje nuorodoje:

![Forkinta saugyklos versija](../../../translated_images/lt/forked-repo.33f27ca1901baa6a.webp)

### Paviršinis klonavimas (rekomenduojama dirbtuvėms / Codespaces)

  >Visa saugykla gali būti didelė (~3 GB), kai atsisiunčiate visą istoriją ir visus failus. Jei dalyvaujate tik dirbtuvėse arba jums reikia tik kelių pamokų aplankų, paviršinis klonavimas (arba retas klonavimas) išvengs didžiosios dalies atsisiuntimo, trumpindamas istoriją ir/ar praleisdamas blob'us.

#### Greitas paviršinis klonavimas — minimalus istorijos kiekis, visi failai

Pakeiskite `<your-username>` žemiau esančiuose komandose savo fork URL (arba upstream URL, jei pageidaujate).

Norėdami nuklonuoti tik naujausią commit istoriją (mažas atsisiuntimas):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Norėdami nuklonuoti konkretų šaką:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Dalinis (sparse) klonavimas — minimalūs blob'ai + tik pasirinkti aplankai

Tai naudoja dalinį klonavimą ir sparse-checkout (reikalauja Git 2.25+ ir rekomenduojamas šiuolaikinis Git su dalinio klonavimo palaikymu):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Pereikite į saugyklos aplanką:

```bash|powershell
cd ai-agents-for-beginners
```

Tada nurodykite, kuriuos aplankus norite (žemiau pateiktas pavyzdys rodo du aplankus):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Po klonavimo ir failų patikrinimo, jei jums reikalingi tik failai ir norite atlaisvinti vietos (nebeprireiks git istorijos), ištrinkite saugyklos metaduomenis (💀negrįžtama — prarasite visą Git funkcionalumą: nebegalėsite commit'inti, pull'inti, push'inti ar pasiekti istorijos).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Naudojant GitHub Codespaces (rekomenduojama, kad išvengtumėte didelių vietinių atsisiuntimų)

- Sukurkite naują Codespace šiai saugyklai per [GitHub UI](https://github.com/codespaces).  

- Naujoje Codespace terminale paleiskite vieną iš aukščiau pateiktų paviršinio / sparse klonavimo komandų, kad į Codespace darbo vietą parsiųstumėte tik reikiamus pamokų aplankus.
- Pasirinktinai: po klonavimo Codespaces viduje pašalinkite .git, kad susigrąžintumėte papildomos vietos (žr. pašalinimo komandas aukščiau).
- Pastaba: jei norite atidaryti saugyklą tiesiogiai Codespaces (be papildomo klonavimo), žinokite, kad Codespaces sukurs devcontainer aplinką ir vis tiek gali paruošti daugiau, nei jums reikia. Paviršinis klonas tuščioje Codespace suteikia daugiau kontrolės dėl disko naudojimo.

#### Patarimai

- Visada pakeiskite klono URL į savo fork'ą, jei norite redaguoti/commit'inti.
- Jei vėliau reikės daugiau istorijos ar failų, galite juos atsisiųsti (fetch) arba pakeisti sparse-checkout, kad įtrauktumėte papildomus aplankus.

## Kodo paleidimas

Šis kursas siūlo seriją Jupyter užrašų knygelių (Notebooks), kuriuos galite paleisti, kad įgytumėte praktinės patirties kuriant AI agentus.

Kodo pavyzdžiai naudoja vieną iš šių:

**Reikalinga GitHub paskyra – nemokama**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Pažymėta kaip (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Pažymėta kaip (autogen.ipynb)

**Reikalinga Azure prenumerata**:
3) Azure AI Foundry + Azure AI Agent Service. Pažymėta kaip (azureaiagent.ipynb)

Raginu jus išbandyti visus tris pavyzdžių tipus, kad pamatytumėte, kuris jums tinka geriausiai.

Kuris pasirinkimas bekristų, jis nulems, kuriuos diegimo žingsnius turite atlikti toliau:

## Reikalavimai

- Python 3.12+
  - **PASTABA**: Jei neturite įdiegto Python3.12, įsitikinkite, kad jį įdiegėte. Tada sukurkite savo venv naudodami python3.12, kad būtų įdiegti teisingi reikalavimų failo paketai.
  
    >Pavyzdys

    Sukurkite Python venv katalogą:

    ```bash|powershell
    python -m venv venv
    ```

    Tada suaktyvinkite venv aplinką:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Pavyzdžių kodams, naudojantiems .NET, įsitikinkite, kad įdiegėte [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) arba naujesnę versiją. Tada patikrinkite savo įdiegtą .NET SDK versiją:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub paskyra - prieigai prie GitHub Models Marketplace
- Azure prenumerata - prieigai prie Microsoft Foundry
- Microsoft Foundry paskyra - prieigai prie Azure AI Agent Service

Šioje saugykloje esančiame šakniniame kataloge įtraukėme `requirements.txt` failą, kuriame yra visi reikalingi Python paketai kodo pavyzdžiams paleisti.

Juos galite įdiegti paleisdami šią komandą terminale, būdami saugyklos šaknyje:

```bash|powershell
pip install -r requirements.txt
```

Rekomenduojame sukurti Python virtualią aplinką, kad išvengtumėte konfliktų ir problemų.

## VSCode nustatymas

Įsitikinkite, kad VSCode naudojate tinkamą Python versiją.

![vaizdas](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Nustatymas pavyzdžiams, naudojantiems GitHub modelius

### 1 žingsnis: Gaukite savo GitHub asmeninį prieigos raktą (PAT)

Šis kursas naudoja GitHub Models Marketplace, suteikdamas nemokamą prieigą prie didelių kalbos modelių (LLM), kuriuos naudosite kurdami AI agentus.

Norėdami naudoti GitHub modelius, turėsite sukurti [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Tai galite padaryti nueidami į savo <a href="https://github.com/settings/personal-access-tokens" target="_blank">Asmeninių prieigos raktų nustatymus</a> savo GitHub paskyroje.

Prašome laikytis [Mažiausių teisių principo](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) kuriant savo raktą. Tai reiškia, kad turėtumėte suteikti token'ui tik tas teises, kurios reikalingos paleisti kodo pavyzdžius šiame kurse.

1. Kairėje ekrano pusėje pasirinkite parinktį `Fine-grained tokens`, pereidami į **Kūrėjo nustatymai**

   ![Kūrėjo nustatymai](../../../translated_images/lt/profile_developer_settings.410a859fe749c755.webp)

   Tada pasirinkite `Generate new token`.

2. Įveskite aprašomą pavadinimą savo token'ui, kad vėliau būtų lengva atpažinti jo paskirtį.

    🔐 Rakto galiojimo rekomendacija

    Rekomenduojamas galiojimo laikas: 30 dienų
    Dėl saugesnės politikos galite pasirinkti trumpesnį laikotarpį — pavyzdžiui, 7 dienas 🛡️
    Tai puikus būdas sau nustatyti asmeninį tikslą ir baigti kursą, kol mokymosi motyvacija yra aukšta 🚀.

    ![Rakto pavadinimas ir galiojimo laikas](../../../translated_images/lt/token-name-expiry-date.a095fb0de6386864.webp)

3. Apribokite rakto sritį iki jūsų fork'intos šios saugyklos.

    ![Apriboti sritį iki fork saugyklos](../../../translated_images/lt/token_repository_limit.924ade5e11d9d8bb.webp)

4. Apribokite rakto leidimus: skiltyje **Permissions** spustelėkite skirtuką **Account**, tada paspauskite mygtuką "+ Pridėti teises". Atsidarys išskleidžiamasis langas. Prašome surasti **Models** ir pažymėti laukelį prie jo.

    ![Pridėti Models leidimą](../../../translated_images/lt/add_models_permissions.c0c44ed8b40fc143.webp)

5. Patikrinkite reikiamus leidimus prieš generuodami raktą. ![Patikrinti leidimus](../../../translated_images/lt/verify_permissions.06bd9e43987a8b21.webp)

6. Prieš generuodami raktą, įsitikinkite, kad esate pasiruošę saugiai jį saugoti, pavyzdžiui, slaptažodžių tvarkyklėje, nes po sukūrimo jis nebus dar kartą rodomas. ![Saugiai saugokite raktą](../../../translated_images/lt/store_token_securely.08ee2274c6ad6caf.webp)

Nukopijuokite ką tik sukurtą raktą. Dabar jį pridėsite į `.env` failą, įtrauktą į šį kursą.

### 2 žingsnis: Sukurkite savo `.env` failą

Norėdami sukurti savo `.env` failą, terminale paleiskite šią komandą.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Tai nukopijuos pavyzdinį failą ir sukurs `.env` jūsų kataloge, kuriame užpildysite aplinkos kintamųjų reikšmes.

Nukopijavę savo raktą, atidarykite `.env` failą savo mėgstamame teksto redaktoriuje ir įklijuokite raktą į lauką `GITHUB_TOKEN`.

![GitHub rakto laukas](../../../translated_images/lt/github_token_field.20491ed3224b5f4a.webp)

Dabar turėtumėte sugebėti paleisti šio kurso kodo pavyzdžius.

## Nustatymas pavyzdžiams, naudojantiems Microsoft Foundry ir Azure AI Agent Service

### 1 žingsnis: Gaukite savo Azure projekto galinio taško adresą

Sekite žingsnius, kaip sukurti hub'ą ir projektą Azure AI Foundry čia: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

Sukūrę projektą, turėsite gauti savo projekto prisijungimo eilutę.

Tai galite padaryti nueidami į savo projekto **Apžvalgos** puslapį Microsoft Foundry portale.

![Projekto prisijungimo eilutė](../../../translated_images/lt/project-endpoint.8cf04c9975bbfbf1.webp)

### 2 žingsnis: Sukurkite savo `.env` failą

Norėdami sukurti savo `.env` failą, terminale paleiskite šią komandą.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Tai nukopijuos pavyzdinį failą ir sukurs `.env` jūsų kataloge, kuriame užpildysite aplinkos kintamųjų reikšmes.

Nukopijavę savo token'ą, atidarykite `.env` failą mėgstamame teksto redaktoriuje ir įklijuokite token'ą į lauką `PROJECT_ENDPOINT`.

### 3 žingsnis: Prisijunkite prie Azure

Laikydamiesi geros saugumo praktikos, naudosime [be raktų autentifikavimą](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) autentifikuotis Azure OpenAI naudojant Microsoft Entra ID. 

Tada atidarykite terminalą ir paleiskite `az login --use-device-code`, kad prisijungtumėte prie savo Azure paskyros.

Prisijungę pasirinkite savo prenumeratą terminale.

## Papildomi aplinkos kintamieji - Azure paieška ir Azure OpenAI

Agentic RAG pamokai - Pamoka 5 - yra pavyzdžių, kurie naudoja Azure Search ir Azure OpenAI.

Jei norite paleisti šiuos pavyzdžius, turėsite pridėti šiuos aplinkos kintamuosius į savo `.env` failą:

### Apžvalgos puslapis (projektas)

- `AZURE_SUBSCRIPTION_ID` - Patikrinkite **Projekto duomenis** **Apžvalgos** puslapyje savo projekte.

- `AZURE_AI_PROJECT_NAME` - Žiūrėkite viršuje ant **Apžvalgos** puslapio savo projekto pavadinimą.

- `AZURE_OPENAI_SERVICE` - Suraskite tai **Included capabilities** skirtuke už **Azure OpenAI Service** ant **Apžvalgos** puslapio.

### Valdymo centras

- `AZURE_OPENAI_RESOURCE_GROUP` - Eikite į **Projekto savybės** ant **Apžvalgos** puslapio **Valdymo centro**.

- `GLOBAL_LLM_SERVICE` - Skiltyje **Connected resources** raskite **Azure AI Services** prisijungimo pavadinimą. Jei nerodoma, patikrinkite **Azure portalą** savo resursų grupėje AI Services resurso pavadinimui.

### Modeliai + Galiniai taškai

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Pasirinkite savo embedding modelį (pvz., `text-embedding-ada-002`) ir užsirašykite **Deployment name** iš modelio informacijos.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Pasirinkite savo chat modelį (pvz., `gpt-4o-mini`) ir užsirašykite **Deployment name** iš modelio informacijos.

### Azure portalas

- `AZURE_OPENAI_ENDPOINT` - Ieškokite **Azure AI services**, spustelėkite jį, tada eikite į **Resource Management**, **Keys and Endpoint**, nuslinkite žemyn iki "Azure OpenAI endpoints" ir nukopijuokite tą, kuris sako "Language APIs".

- `AZURE_OPENAI_API_KEY` - Toje pačioje ekrane nukopijuokite KEY 1 arba KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Suraskite savo **Azure AI Search** resursą, spustelėkite jį ir peržiūrėkite **Apžvalgą**.

- `AZURE_SEARCH_API_KEY` - Tada eikite į **Settings**, o po to į **Keys**, kad nukopijuotumėte pagrindinį arba antrinį administratoriaus raktą.

### Išorinis tinklalapis

- `AZURE_OPENAI_API_VERSION` - Apsilankykite puslapyje apie [API versijų gyvavimo ciklą](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) skiltyje **Latest GA API release**.

### Nustatykite be raktų autentifikaciją

Vietoj to, kad koduotumėme savo kredencialus, naudosime be raktų prisijungimą su Azure OpenAI. Tam importuosime `DefaultAzureCredential` ir vėliau iškviesime `DefaultAzureCredential` funkciją, kad gautume kredencialą.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Užstrigote kažkur?
Jei kyla problemų vykdant šią sąranką, užsukite į mūsų <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI bendruomenės Discord</a> arba <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">pateikite problemą</a>.

## Kita pamoka

Dabar esate pasirengę paleisti šio kurso kodą. Linkime malonaus mokymosi ir daugiau sužinoti apie AI agentų pasaulį! 

[Įvadas į AI agentus ir jų panaudojimo atvejai](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors stengiamės užtikrinti tikslumą, atkreipkite dėmesį, kad automatizuoti vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas jo gimtąja kalba turi būti laikomas autoritetingu šaltiniu. Svarbios informacijos atveju rekomenduojamas profesionalus žmogaus atliktas vertimas. Mes neatsakome už jokius nesusipratimus ar neteisingas interpretacijas, kylančias dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->