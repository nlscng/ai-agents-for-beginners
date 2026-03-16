# Kurzus beállítása

## Bevezetés

Ez az óra arról fog szólni, hogyan futtathatod a tanfolyam kódmintáit.

## Csatlakozz más tanulókhoz és kérj segítséget

Mielőtt elkezdenéd klónozni a tárolódat, csatlakozz az [AI Agents For Beginners Discord csatornához](https://aka.ms/ai-agents/discord), hogy segítséget kapj a beállítással kapcsolatban, kérdéseket tehess fel a tanfolyammal kapcsolatban, vagy kapcsolatba léphess más tanulókkal.

## Klónozd vagy forkold ezt a tárolót

Az első lépésként kérjük, klónozd vagy forkold a GitHub-tárolót. Ezáltal saját verziót kapsz a tanfolyam anyagából, így futtathatod, tesztelheted és módosíthatod a kódot!

Ezt megteheted a következő linkre kattintva: <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">forkold a tárolót</a>

Most már meg kell, hogy legyen a saját forkolt verziód erről a tanfolyamról az alábbi linken:

![Forkolt tároló](../../../translated_images/hu/forked-repo.33f27ca1901baa6a.webp)

### Sekély klónozás (ajánlott workshophoz / Codespaces-hez)

> A teljes tároló nagy is lehet (~3 GB), ha letöltöd a teljes előzményt és az összes fájlt. Ha csak a workshopra mész vagy csak néhány leckefájlt szeretnél, egy sekély klónozás (vagy szelektív klónozás) elkerüli a nagy letöltést az előzmények lerövidítésével és/vagy blobok kihagyásával.

#### Gyors sekély klónozás — minimális előzmény, minden fájl

Cseréld ki a `<your-username>`-t az alábbi parancsokban a saját fork URL-edre (vagy az upstream URL-re, ha úgy szeretnéd).

Csak az utolsó commit előzmény clónozásához (kis letöltés):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Egy adott ág klónozásához:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Részleges (sparse) klónozás — minimális blob + csak kiválasztott mappák

Ez részleges klónozást és sparse-checkout használatát igényli (Git 2.25+ és ajánlott modern Git részleges klónozással):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Lépj be a tároló mappába:

```bash|powershell
cd ai-agents-for-beginners
```

Ezután add meg, mely mappákat szeretnéd (példa lent két mappát mutat):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

A klónozás és fájlok ellenőrzése után, ha csak a fájlokat szeretnéd és helyet akarsz felszabadítani (nem kell git előzmény), töröld a tároló metaadatait (💀visszafordíthatatlan — elveszted az összes Git funkciót: nem lesz commit, pull, push vagy előzmény elérés).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### GitHub Codespaces használata (ajánlott a nagy helyi letöltések elkerülésére)

- Hozz létre új Codespace-et ehhez a tárolóhoz a [GitHub UI](https://github.com/codespaces) segítségével.  

- A frissen létrehozott Codespace termináljában futtasd az egyik sekély vagy szelektív klónozó parancsot fent, hogy csak a szükséges leckemappákat töltsd be a Codespace munkaterületére.
- Opcionális: a Codespaces-ben klónozás után töröld a `.git` mappát a hely visszanyeréséhez (lásd fent a törlési parancsokat).
- Megjegyzés: Ha közvetlenül a Codespaces-ben nyitod meg a tárolót (klónozás nélkül), vedd figyelembe, hogy a Codespaces felépíti a devcontainer környezetet, ami több erőforrást fog igénybe venni. Egy sekély klónozás friss Codespace-ben nagyobb ellenőrzést ad a lemezhasználat felett.

#### Tippek

- Mindig cseréld ki a klón URL-jét a saját forkodra, ha szerkeszteni vagy commitolni szeretnél.
- Ha szükséged van később több előzményre vagy fájlra, lehúzhatod őket vagy állíthatod a sparse-checkout beállításokat további mappák felvételéhez.

## A kód futtatása

Ez a tanfolyam egy sor Jupyter Notebookot kínál, amelyekkel gyakorolhatod az AI ügynökök építését.

A kódminták a következőket használják:

**GitHub-fiókot igényel - ingyenes**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. (autogen.ipynb)

**Azure előfizetést igényel**:
3) Azure AI Foundry + Azure AI Agent Service. (azureaiagent.ipynb)

Javasoljuk, hogy próbáld ki mindhárom példatípust, hogy lásd, melyik működik a legjobban számodra.

Bármelyik lehetőséget is választod, az dönti el, mely beállítási lépéseket kell követned alább:

## Követelmények

- Python 3.12+
  - **MEGJEGYZÉS**: Ha nincs telepítve Python 3.12, akkor telepítsd azt. Ezután hozd létre a virtuális környezetet python3.12-vel, hogy biztos a requirements.txt-ből a megfelelő verziók települjenek.
  
    >Példa

    Python virtuális környezet létrehozása:

    ```bash|powershell
    python -m venv venv
    ```

    Ezután aktiváld a virtuális környezetet:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: A .NET-et használó mintakódokhoz telepítsd a [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) vagy újabbat. Ellenőrizd telepített .NET SDK verziódat:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub fiók - a GitHub Models Marketplace eléréséhez
- Azure előfizetés - a Microsoft Foundry eléréséhez
- Microsoft Foundry fiók - az Azure AI Agent Service eléréséhez

Egy `requirements.txt` fájlt is mellékeltünk a tároló gyökerébe, ami tartalmazza az összes szükséges Python csomagot a kódminták futtatásához.

Telepítheted őket a következő parancs futtatásával a terminálodban, a tároló gyökerében:

```bash|powershell
pip install -r requirements.txt
```

Javasoljuk, hogy hozz létre Python virtuális környezetet az esetleges ütközések és problémák elkerülése érdekében.

## VSCode beállítása

Győződj meg róla, hogy a VSCode-ban a megfelelő Python verziót használod.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Beállítás GitHub Models használatával készült mintákhoz

### 1. lépés: Szerezd meg a GitHub személyes hozzáférési tokenedet (PAT)

Ez a tanfolyam a GitHub Models Marketplace-et használja, amely ingyenes hozzáférést biztosít Nagy Nyelvi Modellekhez (LLM-ek), amiket AI ügynökök építéséhez használsz.

A GitHub Models használatához létre kell hoznod egy [GitHub személyes hozzáférési tokent](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Ezt a <a href="https://github.com/settings/personal-access-tokens" target="_blank">Személyes hozzáférési token beállítások</a> menüpontban teheted meg GitHub fiókodban.

Kérjük, kövesd a [legkisebb jogosultság elvét](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) a token létrehozásakor. Ez azt jelenti, hogy csak azokat a jogosultságokat adj a tokennek, amelyekre szükség van a tanfolyam kódmintáinak futtatásához.

1. Válaszd ki a képernyőd bal oldalán a `Fine-grained tokens` opciót a **Fejlesztői beállítások** menüponton keresztül

   ![Fejlesztői beállítások](../../../translated_images/hu/profile_developer_settings.410a859fe749c755.webp)

   Ezután kattints a `Új token generálása` gombra.

   ![Token generálása](../../../translated_images/hu/fga_new_token.1c1a234afe202ab3.webp)

2. Adj egy leíró nevet a tokennek, ami tükrözi a célját, hogy később könnyen be tudd azonosítani.

    🔐 Token lejárati javaslat

    Ajánlott időtartam: 30 nap  
    Biztonságosabb megközelítésként választhatsz rövidebb időszakot—például 7 napot 🛡️  
    Ez egy nagyszerű mód személyes célkitűzés beállítására, és arra, hogy a tanfolyamot végigcsináld, amíg nagy a tanulási lendület 🚀.

    ![Token név és lejárat](../../../translated_images/hu/token-name-expiry-date.a095fb0de6386864.webp)

3. Limitáld a token hatókörét a tárolód által forkolt verzióra.

    ![Hatókör limitálása fork tárolóra](../../../translated_images/hu/token_repository_limit.924ade5e11d9d8bb.webp)

4. Szűkítsd a token jogosultságait: a **Jogosultságok** alatt kattints a **Fiók** fülre, majd a "+ Jogosultság hozzáadása" gombra. Megjelenik egy legördülő lista. Keresd meg a **Models** jogosultságot és pipáld ki.

    ![Models jogosultság hozzáadása](../../../translated_images/hu/add_models_permissions.c0c44ed8b40fc143.webp)

5. Ellenőrizd a szükséges jogosultságokat mielőtt generálod a tokent.

    ![Jogosultságok ellenőrzése](../../../translated_images/hu/verify_permissions.06bd9e43987a8b21.webp)

6. A token generálása előtt győződj meg róla, hogy tudod biztonságos helyen tárolni (például jelszókezelőben), mert a létrehozás után nem fog többet megjelenni.

    ![Token biztonságos tárolása](../../../translated_images/hu/store_token_securely.08ee2274c6ad6caf.webp)

Másold ki az újonnan létrehozott tokent. Ezt most be kell illesztened a tanfolyamhoz tartozó `.env` fájlba.

### 2. lépés: Hozd létre a `.env` fájlodat

A `.env` fájl létrehozásához futtasd a következő parancsot a terminálodban.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ez lemásolja a példa fájlt és létrehozza a `.env`-t a könyvtáradban, ahol kitöltheted a környezeti változók értékeit.

Miután kimásoltad a tokent, nyisd meg a `.env` fájlt kedvenc szövegszerkesztődben, és illeszd be a `GITHUB_TOKEN` mezőbe.

![GitHub Token mező](../../../translated_images/hu/github_token_field.20491ed3224b5f4a.webp)

Most már futtathatod a tanfolyam kódmintáit.

## Beállítás Microsoft Foundry és Azure AI Agent Service használatával készült mintákhoz

### 1. lépés: Szerezd meg Azure projekted végpontját

Kövessük az Azure AI Foundry-ben történő hub és projekt létrehozás lépéseit itt: [Hub erőforrások áttekintése](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

Miután létrehoztad a projektet, le kell kérned a projekt kapcsolati karakterláncát.

Ezt a projekted **Áttekintés** oldalán teheted meg a Microsoft Foundry portálon.

![Projekt kapcsolati karakterlánc](../../../translated_images/hu/project-endpoint.8cf04c9975bbfbf1.webp)

### 2. lépés: Hozd létre `.env` fájlodat

A `.env` fájl létrehozásához futtasd a következő parancsot a terminálodban.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ez lemásolja a példa fájlt és létrehozza a `.env`-t a könyvtáradban, ahol kitöltheted a környezeti változók értékeit.

Miután beillesztetted az adatokat, nyisd meg a `.env` fájlt és illeszd be a `PROJECT_ENDPOINT` mezőbe a kapcsolat karakterláncot.

### 3. lépés: Jelentkezz be az Azure-ba

Biztonsági jó gyakorlatként használunk [kulcs nélküli hitelesítést](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) az Azure OpenAI-hoz Microsoft Entra ID-val.

Ezt követően nyiss meg egy terminált és futtasd az `az login --use-device-code` parancsot az Azure fiókodba való bejelentkezéshez.

Bejelentkezés után válaszd ki az előfizetésedet a terminálban.

## További környezeti változók - Azure Search és Azure OpenAI

Az Agentic RAG lecke - 5. lecke - tartalmaz olyan mintákat, amelyek Azure Search-et és Azure OpenAI-t használnak.

Ha ezeket a mintákat szeretnéd futtatni, akkor az alábbi környezeti változókat kell hozzáadnod a `.env` fájlodhoz:

### Áttekintő oldal (Projekt)

- `AZURE_SUBSCRIPTION_ID` - Nézd meg a **Projekt részletek** részt a projekt **Áttekintő** oldalán.

- `AZURE_AI_PROJECT_NAME` - Nézd meg a projekt **Áttekintő** oldalának tetején.

- `AZURE_OPENAI_SERVICE` - A projekt **Áttekintő** oldalán a **Tartalmazott képességek** fül alatt az **Azure OpenAI Szolgáltatás**.

### Menedzsment központ

- `AZURE_OPENAI_RESOURCE_GROUP` - A **Menedzsment központ** projekt **Áttekintő** oldalán a **Projekt tulajdonságok** között.

- `GLOBAL_LLM_SERVICE` - A **Kapcsolt erőforrások** alatt az **Azure AI Services** kapcsolati név. Ha nincs ott, nézd meg az **Azure portálon** a megfelelő erőforrás csoporton belül az AI Szolgáltatások erőforrás nevét.

### Modellek + végpontok oldal

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Válassz egy beágyazási modellt (pl. `text-embedding-ada-002`), és jegyezd fel a **Telepítési név** értékét a modell részleteiben.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Válassz egy chat modellt (pl. `gpt-4o-mini`), és jegyezd fel a **Telepítési név** értékét a modell részleteiben.

### Azure portál

- `AZURE_OPENAI_ENDPOINT` - Keresd meg az **Azure AI szolgáltatásokat**, kattints rá, majd a **Erőforráskezelés**, **Kulcsok és végpont** résznél görgess le az "Azure OpenAI végpontok"-hoz és másold ki a "Language APIs" végpontot.

- `AZURE_OPENAI_API_KEY` - Ugyanitt a képernyőn másold ki az 1-es vagy 2-es kulcsot (KEY 1 vagy KEY 2).

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Keresd meg az **Azure AI Search** erőforrást, kattints rá, és nézd meg az **Áttekintést**.

- `AZURE_SEARCH_API_KEY` - Ezután menj a **Beállítások** → **Kulcsok** részhez és másold ki az elsődleges vagy másodlagos admin kulcsot.

### Külső weboldal

- `AZURE_OPENAI_API_VERSION` - Látogasd meg az [API verzió életciklus](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) oldalát a **Legfrissebb GA API kiadás** alatt.

### Kulcs nélküli hitelesítés beállítása

Ahelyett, hogy a hitelesítő adataidat kódba írnánk, kulcs nélküli kapcsolatot használunk az Azure OpenAI-hoz. Ehhez importáljuk a `DefaultAzureCredential`-t, és később meghívjuk ezt a függvényt a hitelesítő adatok megszerzéséhez.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Elakadtál valahol?
Ha bármilyen problémád adódik a beállítás futtatása során, csatlakozz az <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> csoporthoz, vagy <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">hozz létre egy hibabejelentést</a>.

## Következő lecke

Most készen állsz arra, hogy futtasd a kurzus kódját. Sok sikert az AI ügynökök világának további felfedezéséhez!

[Bevezetés az AI ügynökökbe és az ügynökök használati eseteibe](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Nyilatkozat**:  
Ezt a dokumentumot az AI fordítási szolgáltatás, a [Co-op Translator](https://github.com/Azure/co-op-translator) segítségével fordítottuk le. Bár igyekszünk pontosak lenni, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum annak anyanyelvén tekintendő hiteles forrásnak. Fontos információk esetén professzionális emberi fordítást javaslunk. Nem vállalunk felelősséget az ebből az átiratból eredő félreértésekért vagy helytelen értelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->