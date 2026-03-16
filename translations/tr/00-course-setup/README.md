# Kurs Kurulumu

## Giriş

Bu ders, bu kursun kod örneklerini nasıl çalıştıracağınızı kapsayacaktır.

## Diğer Öğrenenlere Katılın ve Yardım Alın

Depoyu klonlamaya başlamadan önce, kurulumla ilgili herhangi bir yardım almak, kursla ilgili sorular sormak veya diğer öğrenenlerle bağlantı kurmak için [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) kanalına katılın.

## Bu Depoyu Klonlayın veya Forklayın

Başlamak için lütfen GitHub Deposunu klonlayın veya forklayın. Bu, kurs materyalinin kendi sürümünüzü oluşturacak ve kodu çalıştırıp, test edip, değiştirebilmenizi sağlayacaktır!

Bu, <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">deponun fork'unu oluştur</a> bağlantısına tıklanarak yapılabilir.

Aşağıdaki bağlantıda artık bu dersin kendi forklanmış sürümüne sahip olmalısınız:

![Forklanmış Depo](../../../translated_images/tr/forked-repo.33f27ca1901baa6a.webp)

### Yüzeysel Klon (atölye / Codespaces için önerilir)

  >Tam depo geçmişi ve tüm dosyalar indirildiğinde tüm depo büyük (~3 GB) olabilir. Sadece atölyeye katılıyorsanız veya yalnızca birkaç ders klasörüne ihtiyacınız varsa, yüzeysel bir klon (veya seyrek klon) geçmişi kısaltarak ve/veya blob'ları atlayarak çoğu indirimi önler.

#### Hızlı yüzeysel klon — minimal geçmiş, tüm dosyalar

Aşağıdaki komutlardaki `<your-username>` kısmını fork URL'nizle (veya tercihinizle upstream URL ile) değiştirmeyi unutmayın.

Sadece en son commit geçmişini klonlamak için (küçük indirme):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Belirli bir dalı klonlamak için:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Kısmi (sparse) klon — minimal bloblar + sadece seçili klasörler

Bu, kısmi klon ve sparse-checkout kullanır (Git 2.25+ gerektirir ve kısmi klon desteği olan modern Git önerilir):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Depo klasörüne girin:

```bash|powershell
cd ai-agents-for-beginners
```

Daha sonra hangi klasörleri istediğinizi belirtin (aşağıdaki örnek iki klasörü gösterir):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Klonladıktan ve dosyaları doğruladıktan sonra, yalnızca dosyalara ihtiyaç duyuyorsanız ve alan açmak istiyorsanız (git geçmişi olmadan), lütfen depo meta verilerini silin (💀geri döndürülemez — tüm Git işlevselliğini kaybedeceksiniz: commit, pull, push veya geçmiş erişimi olmayacaktır).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### GitHub Codespaces Kullanımı (yerel büyük indirmelerden kaçınmak için önerilir)

- Bu repo için yeni bir Codespace oluşturmak üzere [GitHub UI](https://github.com/codespaces) üzerinden oluşturun.  

- Yeni oluşturulan codespace'in terminalinde, Codespace çalışma alanına yalnızca ihtiyacınız olan ders klasörlerini getirmek için yukarıdaki yüzeysel/seyrek klon komutlarından birini çalıştırın.
- İsteğe bağlı: Codespaces içinde klonladıktan sonra ekstra alan kurtarmak için .git'i kaldırın (yukarıdaki kaldırma komutlarına bakın).
- Not: Depoyu doğrudan Codespaces içinde açmayı tercih ederseniz (ek bir klon olmadan), Codespaces geliştime konteyner ortamını oluşturacak ve yine de ihtiyacınızdan fazlasını sağlıyor olabilir. Yeni bir Codespace içinde yüzeysel bir kopya klonlamak, disk kullanımı üzerinde daha fazla kontrol sağlar.

#### İpuçları

- Düzenleme/commit yapmak istiyorsanız klon URL'sini her zaman fork'unuzla değiştirin.
- Daha sonra daha fazla geçmişe veya dosyaya ihtiyacınız olursa, bunları getirebilir veya sparse-checkout'u ek klasörleri içerecek şekilde ayarlayabilirsiniz.

## Kodu Çalıştırma

Bu kurs, AI Ajanları oluşturma konusunda uygulamalı deneyim kazanmanız için çalıştırabileceğiniz bir dizi Jupyter Notebooks sunar.

Kod örnekleri aşağıdakilerden birini kullanır:

**GitHub Hesabı Gerektirir - Ücretsiz**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Etiketlenmiş olarak (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Etiketlenmiş olarak (autogen.ipynb)

**Azure Aboneliği Gerektirir**:
3) Azure AI Foundry + Azure AI Agent Service. Etiketlenmiş olarak (azureaiagent.ipynb)

Hangi seçeneği tercih ederseniz edin, bu aşağıdaki kurulum adımlarını hangi şekilde takip etmeniz gerektiğini belirleyecektir:

## Gereksinimler

- Python 3.12+
  - **NOT:** Eğer Python3.12 yüklü değilse, lütfen yükleyin. Ardından requirements.txt dosyasından doğru sürümlerin yüklendiğinden emin olmak için venv'inizi python3.12 ile oluşturun.
  
    >Örnek

    Python venv dizini oluşturun:

    ```bash|powershell
    python -m venv venv
    ```

    Ardından venv ortamını şu şekilde etkinleştirin:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: .NET kullanan örnek kodlar için lütfen [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) veya daha yenisini kurun. Ardından, yüklü .NET SDK sürümünüzü kontrol edin:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Bir GitHub Hesabı - GitHub Models Marketplace'e Erişim için
- Azure Aboneliği - Microsoft Foundry'e Erişim için
- Microsoft Foundry Hesabı - Azure AI Agent Service'e Erişim için

Bu depo kökünde örnek kodları çalıştırmak için gereken tüm Python paketlerini içeren bir `requirements.txt` dosyasını dahil ettik.

Onları depo kökünde terminalinizde aşağıdaki komutu çalıştırarak kurabilirsiniz:

```bash|powershell
pip install -r requirements.txt
```

Herhangi bir çakışma ve sorunu önlemek için bir Python sanal ortamı oluşturmanızı öneririz.

## VSCode Kurulumu

VSCode'da doğru Python sürümünü kullandığınızdan emin olun.

![görsel](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## GitHub Modellerini Kullanan Örnekler İçin Kurulum

### Adım 1: GitHub Kişisel Erişim Jetonunuzu (PAT) Edinin

Bu kurs, AI Ajanları oluşturmak için kullanacağınız Ücretiz erişim sağlayan Large Language Models (LLM'ler) sunan GitHub Models Marketplace'i kullanır.

GitHub Modellerini kullanmak için bir [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) oluşturmanız gerekecektir.

Bu, GitHub hesabınızda <a href="https://github.com/settings/personal-access-tokens" target="_blank">Kişisel Erişim Jetonları ayarları</a> sayfasına gidilerek yapılabilir.

Lütfen jeton oluştururken [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) ilkesine uyun. Bu, jetona bu kursun kod örneklerini çalıştırmak için ihtiyaç duyduğu izinleri vermeniz gerektiği anlamına gelir.

1. Ekranınızın sol tarafında bulunan `Fine-grained tokens` seçeneğini seçerek **Geliştirici ayarları** bölümüne gidin.

   ![Geliştirici ayarları](../../../translated_images/tr/profile_developer_settings.410a859fe749c755.webp)

   Ardından `Generate new token` seçeneğini seçin.

   ![Generate Token](../../../translated_images/tr/fga_new_token.1c1a234afe202ab3.webp)

2. Jetonunuz için amacını yansıtan açıklayıcı bir ad girin, böylece daha sonra kolayca tanımlayabilirsiniz.

    🔐 Token Süre Önerisi

    Önerilen süre: 30 gün
    Daha güvenli bir yaklaşım için 7 gün gibi daha kısa bir süre tercih edebilirsiniz 🛡️
    Bu, kişisel bir hedef belirlemek ve öğrenme ivmeniz yüksekken kursu tamamlamak için harika bir yoldur 🚀.

    ![Token Adı ve Süresi](../../../translated_images/tr/token-name-expiry-date.a095fb0de6386864.webp)

3. Jetonun kapsamını bu deponun fork'una sınırlandırın.

    ![İzin kapsamını fork'lanmış depoya sınırlandırın](../../../translated_images/tr/token_repository_limit.924ade5e11d9d8bb.webp)

4. Jetonun izinlerini kısıtlayın: **İzinler** altında **Hesap** sekmesine tıklayın ve "+ Add permissions" düğmesine tıklayın. Bir açılır menü görünecektir. Lütfen **Modeller** için arama yapın ve kutuyu işaretleyin.

    ![Modeller İzni Ekle](../../../translated_images/tr/add_models_permissions.c0c44ed8b40fc143.webp)

5. Jetonu oluşturmadan önce gerekli izinleri doğrulayın. ![İzinleri Doğrula](../../../translated_images/tr/verify_permissions.06bd9e43987a8b21.webp)

6. Jetonu oluşturmadan önce, jetonu oluşturduktan sonra tekrar gösterilmeyeceği için bir parola yöneticisi kasası gibi güvenli bir yerde saklamaya hazır olduğunuzdan emin olun. ![Token'ı Güvenli Bir Şekilde Saklayın](../../../translated_images/tr/store_token_securely.08ee2274c6ad6caf.webp)

Yeni oluşturduğunuz jetonu kopyalayın. Şimdi bunu bu derste dahil edilen `.env` dosyanıza ekleyeceksiniz.

### Adım 2: `.env` Dosyanızı Oluşturun

`.env` dosyanızı oluşturmak için terminalinizde aşağıdaki komutu çalıştırın.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Bu, örnek dosyayı kopyalayacak ve dizininizde bir `.env` oluşturacak ve ortam değişkenleri için değerleri dolduracağınız yeri sağlayacaktır.

Jetonunuzu kopyaladıktan sonra, favori metin düzenleyicinizde `.env` dosyasını açın ve jetonunuzu `GITHUB_TOKEN` alanına yapıştırın.

![GitHub Token Alanı](../../../translated_images/tr/github_token_field.20491ed3224b5f4a.webp)

Artık bu kursun kod örneklerini çalıştırabiliyor olmanız gerekir.

## Microsoft Foundry ve Azure AI Agent Service Kullanan Örnekler İçin Kurulum

### Adım 1: Azure Proje Uç Noktanızı Alın


Azure AI Foundry'de bir hub ve proje oluşturma adımlarını buradan takip edin: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Projenizi oluşturduktan sonra, projeniz için bağlantı dizesini almanız gerekecektir.

Bu, Microsoft Foundry portalında projenizin **Genel Bakış** sayfasına gidilerek yapılabilir.

![Proje Bağlantı Dizisi](../../../translated_images/tr/project-endpoint.8cf04c9975bbfbf1.webp)

### Adım 2: `.env` Dosyanızı Oluşturun

`.env` dosyanızı oluşturmak için terminalinizde aşağıdaki komutu çalıştırın.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Bu, örnek dosyayı kopyalayacak ve dizininizde bir `.env` oluşturacak ve ortam değişkenleri için değerleri dolduracağınız yeri sağlayacaktır.

Jetonunuzu kopyaladıktan sonra, favori metin düzenleyicinizde `.env` dosyasını açın ve jetonunuzu `PROJECT_ENDPOINT` alanına yapıştırın.

### Adım 3: Azure'a Oturum Açın

Güvenlik açısından en iyi uygulama olarak, Microsoft Entra ID ile Azure OpenAI'ye kimlik doğrulamak için [anahtarsız kimlik doğrulama](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) kullanacağız. 

Sonraki adımda bir terminal açın ve Azure hesabınıza giriş yapmak için `az login --use-device-code` komutunu çalıştırın.

Oturum açtıktan sonra terminalde aboneliğinizi seçin.

## Ek Ortam Değişkenleri - Azure Search ve Azure OpenAI 

Agentic RAG Dersi - Ders 5 için Azure Search ve Azure OpenAI kullanan örnekler bulunmaktadır.

Bu örnekleri çalıştırmak istiyorsanız, `.env` dosyanıza aşağıdaki ortam değişkenlerini eklemeniz gerekecektir:

### Genel Bakış Sayfası (Proje)

- `AZURE_SUBSCRIPTION_ID` - Projenizin **Genel Bakış** sayfasında **Proje ayrıntıları** bölümünü kontrol edin.

- `AZURE_AI_PROJECT_NAME` - Projenizin **Genel Bakış** sayfasının üst kısmına bakın.

- `AZURE_OPENAI_SERVICE` - Bunu **Genel Bakış** sayfasındaki **Dahil edilen yetenekler** sekmesinde **Azure OpenAI Service** için bulun.

### Yönetim Merkezi

- `AZURE_OPENAI_RESOURCE_GROUP` - **Yönetim Merkezi** içindeki **Genel Bakış** sayfasında **Proje özellikleri** bölümüne gidin.

- `GLOBAL_LLM_SERVICE` - **Bağlı kaynaklar** altında **Azure AI Services** bağlantı adını bulun. Listelenmemişse, AI Services kaynak adını kaynak grubunuz altında **Azure portalı**nda kontrol edin.

### Modeller + Uç Noktalar Sayfası

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Gömme modelinizi seçin (ör. `text-embedding-ada-002`) ve model ayrıntılarından **Deployment name** (Dağıtım adı) not edin.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Sohbet modelinizi seçin (ör. `gpt-4o-mini`) ve model ayrıntılarından **Deployment name** not edin.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - **Azure AI services** öğesini arayın, üzerine tıklayın, ardından **Resource Management**, **Keys and Endpoint** bölümüne gidin, "Azure OpenAI endpoints" bölümüne kadar aşağı kaydırın ve "Language APIs" yazan uç noktayı kopyalayın.

- `AZURE_OPENAI_API_KEY` - Aynı ekrandan KEY 1 veya KEY 2'yi kopyalayın.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - **Azure AI Search** kaynağınızı bulun, üzerine tıklayın ve **Genel Bakış** bölümünü görün.

- `AZURE_SEARCH_API_KEY` - Ardından **Ayarlar** ve sonra **Anahtarlar** bölümüne giderek birincil veya ikincil yönetici anahtarını kopyalayın.

### Harici Web Sayfası

- `AZURE_OPENAI_API_VERSION` - **Latest GA API release** başlığı altındaki [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) sayfasını ziyaret edin.

### Anahtarsız kimlik doğrulama kurulumu

Kimlik bilgilerinizi sert kodlamak yerine, Azure OpenAI ile anahtarsız bir bağlantı kullanacağız. Bunu yapmak için `DefaultAzureCredential`'ı içe aktaracağız ve daha sonra kimlik bilgilerini almak için `DefaultAzureCredential` fonksiyonunu çağıracağız.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Bir Yerlerde Takıldınız mı?
Bu kurulumu çalıştırırken herhangi bir sorun yaşıyorsanız, <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> sunucumuza katılın veya <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">bir sorun oluşturun</a>.

## Sonraki Ders

Artık bu kursun kodunu çalıştırmaya hazırsınız. AI Ajanları dünyası hakkında daha fazlasını öğrenirken iyi çalışmalar! 

[AI Ajanlarına Giriş ve Ajan Kullanım Örnekleri](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Feragatname:
Bu belge, [Co-op Translator](https://github.com/Azure/co-op-translator) adlı yapay zeka çeviri hizmeti kullanılarak çevrilmiştir. Doğruluk için çaba göstermemize rağmen, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal belgenin kendi dilindeki versiyonu yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanılması sonucunda ortaya çıkabilecek herhangi bir yanlış anlama veya yanlış yorumlamadan sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->