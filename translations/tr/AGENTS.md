# AGENTS.md

## Proje Genel Bakış

Bu depo "Yeni Başlayanlar için Yapay Zeka Ajanları" - AI Ajanları oluşturmak için gereken her şeyi öğreten kapsamlı bir eğitim kursu içermektedir. Kurs, temel bilgiler, tasarım kalıpları, frameworkler ve AI ajanlarının üretim ortamına dağıtımını kapsayan 15+ dersten oluşmaktadır.

**Ana Teknolojiler:**
- Python 3.12+
- Etkileşimli öğrenim için Jupyter Notebooks
- AI Frameworkleri: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Servisleri: Microsoft Foundry, Azure AI Agent Service
- GitHub Modeller Marketi (ücretsiz katman mevcut)

**Mimari:**
- Ders tabanlı yapı (00-15+ dizinleri)
- Her ders: README dokümantasyonu, kod örnekleri (Jupyter notebooklar) ve görseller içerir
- Otomatik çeviri sistemi ile çok dilli destek
- Her ders için birden fazla framework seçeneği (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Kurulum Komutları

### Ön Koşullar
- Python 3.12 veya üstü
- GitHub hesabı (GitHub Modelleri için - ücretsiz katman)
- Azure aboneliği (isteğe bağlı, Azure AI servisleri için)

### İlk Kurulum

1. **Depoyu klonlayın veya fork edin:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # VEYA
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Python sanal ortamı oluşturup aktif edin:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Windows'ta: venv\Scripts\activate
   ```

3. **Bağımlılıkları yükleyin:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Ortam değişkenlerini ayarlayın:**
   ```bash
   cp .env.example .env
   # .env dosyasını API anahtarlarınız ve uç noktalarınızla düzenleyin
   ```

### Gerekli Ortam Değişkenleri

**GitHub Modelleri (Ücretsiz)** için:
- `GITHUB_TOKEN` - GitHub’dan alınan kişisel erişim tokenı

**Azure AI Servisleri** için (isteğe bağlı):
- `PROJECT_ENDPOINT` - Microsoft Foundry proje uç noktası
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API anahtarı
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI uç noktası URL'si
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Sohbet modeli için dağıtım adı
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Gömülü modeller için dağıtım adı
- `.env.example` dosyasında gösterilen ek Azure yapılandırmaları

## Geliştirme İş Akışı

### Jupyter Notebooks Çalıştırma

Her ders farklı frameworkler için birden fazla Jupyter notebook içerir:

1. **Jupyter’i başlatın:**
   ```bash
   jupyter notebook
   ```

2. **Bir ders dizinine gidin** (ör. `01-intro-to-ai-agents/code_samples/`)

3. **Notebookları açıp çalıştırın:**
   - `*-semantic-kernel.ipynb` - Semantic Kernel framework kullanımı
   - `*-autogen.ipynb` - AutoGen framework kullanımı
   - `*-python-agent-framework.ipynb` - Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Azure AI Agent Service kullanımı

### Farklı Frameworklerle Çalışma

**Semantic Kernel + GitHub Modelleri:**
- GitHub hesabı ile ücretsiz katman mevcut
- Öğrenme ve denemeler için uygun
- Dosya deseni: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Modelleri:**
- GitHub hesabı ile ücretsiz katman mevcut
- Çoklu ajan orkestrasyon özellikleri
- Dosya deseni: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Microsoft’un en güncel framework’u
- Python ve .NET versiyonları mevcut
- Dosya deseni: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Azure aboneliği gerektirir
- Üretim seviyesi özellikler sunar
- Dosya deseni: `*-azureaiagent.ipynb`

## Test Talimatları

Bu repo otomatik testler içeren üretim kodu değil, örnek kod içeren eğitim amacındadır. Kurulumu ve değişikliklerinizi doğrulamak için:

### Manuel Test

1. **Python ortamını test edin:**
   ```bash
   python --version  # 3.12 ve üzeri olmalıdır
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Notebookların çalışmasını test edin:**
   ```bash
   # Not defterini betiğe dönüştür ve çalıştır (testler için ithalatları kontrol eder)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Ortam değişkenlerini doğrulayın:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Tek Tek Notebook Çalıştırma

Notebookları Jupyter içinde açın ve hücreleri sırasıyla çalıştırın. Her notebook kendi başına yeterlidir ve şunları içerir:
- İçe aktarma ifadeleri
- Yapılandırma yükleme
- Örnek ajan uygulamaları
- Markdown hücrelerinde beklenen çıktılar

## Kod Stili

### Python Konvansiyonları

- **Python Sürümü:** 3.12+
- **Kod Stili:** Standart Python PEP 8 kurallarına uyun
- **Notebooklar:** Kavramları açıklayan açık markdown hücreleri kullanın
- **İçe Aktarmalar:** Standart kütüphane, üçüncü taraf ve yerel içe aktarmaları gruplayın

### Jupyter Notebook Konvansiyonları

- Kod hücrelerinden önce açıklayıcı markdown hücreleri ekleyin
- Notebooklarda referans için çıktı örnekleri ekleyin
- Ders konularına uygun net değişken isimleri kullanın
- Notebook çalıştırma sırasını lineer tutun (hücre 1 → 2 → 3 ...)

### Dosya Organizasyonu

```
<lesson-number>-<lesson-name>/
├── README.md                     # Lesson documentation
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

## Derleme ve Dağıtım

### Dokümantasyon Derleme

Bu depo dokümantasyon için Markdown kullanır:
- Her ders klasöründe README.md dosyası
- Depo kökünde ana README.md
- GitHub Actions ile otomatik çeviri sistemi

### CI/CD Pipeline

`.github/workflows/` içinde yer alır:

1. **co-op-translator.yml** - 50+ dile otomatik çeviri
2. **welcome-issue.yml** - Yeni issue oluşturanları karşılama
3. **welcome-pr.yml** - Yeni pull request katkıcılarını karşılama

### Dağıtım

Bu eğitim amaçlı bir depo olup dağıtım süreci yoktur. Kullanıcılar:
1. Depoyu forklar veya klonlar
2. Notebookları lokal veya GitHub Codespaces’te çalıştırır
3. Örnekleri değiştirerek ve deneyerek öğrenir

## Pull Request Kuralları

### Göndermeden Önce

1. **Değişikliklerinizi test edin:**
   - Etkilenen notebookları tamamen çalıştırın
   - Tüm hücrelerin hata vermeden çalıştığını doğrulayın
   - Çıktıların uygun olduğunu kontrol edin

2. **Dokümantasyon güncellemeleri:**
   - Yeni kavram ekliyorsanız README.md dosyasını güncelleyin
   - Karmaşık kodlar için notebooklarda yorum ekleyin
   - Markdown hücrelerinin amacı açıklamasını sağlayın

3. **Dosya değişiklikleri:**
   - `.env` dosyalarını commit etmeyin ( `.env.example` kullanılmalı)
   - `venv/` veya `__pycache__/` dizinlerini commit etmeyin
   - Kavram gösteren notebook çıktılarını saklayın
   - Geçici dosyaları ve yedek notebookları (`*-backup.ipynb`) kaldırın

### PR Başlık Formatı

Açıklayıcı başlıklar kullanın:
- `[Lesson-XX] <konsept> için yeni örnek ekle`
- `[Fix] lesson-XX README'deki yazım hatasını düzelt`
- `[Update] lesson-XX kod örneğini geliştir`
- `[Docs] kurulum talimatlarını güncelle`

### Gerekli Kontroller

- Notebooklar hatasız çalışmalı
- README dosyaları açık ve doğru olmalı
- Depodaki mevcut kod örneklerine uyumlu olun
- Diğer derslerle tutarlılık sağlanmalı

## Ek Notlar

### Yaygın Sorunlar

1. **Python sürüm uyumsuzluğu:**
   - Python 3.12+ kullanılmalıdır
   - Bazı paketler eski sürümlerle uyumsuz olabilir
   - `python3 -m venv` ile Python sürümü açıkça belirtilmeli

2. **Ortam değişkenleri:**
   - `.env.example` dosyasından `.env` oluşturulmalı
   - `.env` dosyası commit edilmemeli ( `.gitignore` içinde)
   - GitHub token gerekli izinlere sahip olmalı

3. **Paket çakışmaları:**
   - Yeni bir sanal ortam kullanılmalı
   - Paketler tek tek değil, `requirements.txt` üzerinden kurulmalı
   - Bazı notebooklar markdown hücrelerinde ek paketler isteyebilir

4. **Azure servisleri:**
   - Azure AI servisleri için aktif abonelik gerekir
   - Bazı özellikler bölgeye özel olabilir
   - GitHub Modelleri için ücretsiz katman sınırları geçerlidir

### Öğrenme Yolu

Derslerde önerilen sıralama:
1. **00-course-setup** - Ortam kurulumu için başlangıç
2. **01-intro-to-ai-agents** - AI ajanlarının temelleri
3. **02-explore-agentic-frameworks** - Farklı frameworkleri öğrenin
4. **03-agentic-design-patterns** - Temel tasarım kalıpları
5. Numaralandırılmış derslerle sırayla devam edin

### Framework Seçimi

Hedefinize göre framework seçin:
- **Öğrenme/Prototipleme:** Semantic Kernel + GitHub Modeller (ücretsiz)
- **Çoklu ajan sistemleri:** AutoGen
- **En yeni özellikler:** Microsoft Agent Framework (MAF)
- **Üretim dağıtımı:** Azure AI Agent Service

### Yardım Alma

- [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord) sunucusuna katılın
- Ders README dosyalarını inceleyin
- Kurs genel bakışı için ana [README.md](./README.md) dosyasına bakın
- Detaylı kurulum talimatları için [Course Setup](./00-course-setup/README.md) dosyasını inceleyin

### Katkıda Bulunma

Bu açık eğitim projesidir. Katkılar memnuniyetle karşılanır:
- Kod örneklerini geliştirin
- Yazım hatalarını ve hataları düzeltin
- Açıklama yorumları ekleyin
- Yeni ders konuları önerin
- Ek dillere çeviri yapın

Mevcut ihtiyaçlar için [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) sayfasına bakabilirsiniz.

## Proje Özel Bağlam

### Çok Dilli Destek

Bu depo otomatik çeviri sistemi kullanır:
- 50+ dil desteklenir
- Çeviriler `/translations/<lang-code>/` dizinlerinde bulunur
- GitHub Actions iş akışı çeviri güncellemelerini yönetir
- Kaynak dosyalar depo kökünde İngilizce olarak mevcuttur

### Ders Yapısı

Her ders tutarlı bir model takip eder:
1. Bağlantılı video küçük resmi
2. Yazılı ders içeriği (README.md)
3. Birden fazla frameworkte kod örnekleri
4. Öğrenme hedefleri ve ön koşullar
5. Ek öğrenme kaynakları bağlantıları

### Kod Örneği İsimlendirmesi

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - 4. Ders, Semantic Kernel
- `07-autogen.ipynb` - 7. Ders, AutoGen
- `14-python-agent-framework.ipynb` - 14. Ders, MAF Python
- `14-dotnet-agent-framework.ipynb` - 14. Ders, MAF .NET

### Özel Dizinler

- `translated_images/` - Çevirilere ait yerelleştirilmiş görseller
- `images/` - İngilizce içeriğe ait orijinal görseller
- `.devcontainer/` - VS Code geliştirme konteyner yapılandırması
- `.github/` - GitHub Actions iş akışları ve şablonlar

### Bağımlılıklar

`requirements.txt` dosyasındaki ana paketler:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI servisleri
- `azure-search-documents` - Azure AI Search entegrasyonu
- `chromadb` - RAG örnekleri için vektör veritabanı
- `chainlit` - Sohbet UI framework’ü
- `browser_use` - Ajanlar için tarayıcı otomasyonu
- `mcp[cli]` - Model Context Protocol desteği
- `mem0ai` - Ajanlar için bellek yönetimi

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:
Bu belge, AI çeviri servisi [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba sarf etsek de, otomatik çevirilerin hata veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal belge, kendi dilinde yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi tavsiye edilir. Bu çevirinin kullanılmasından kaynaklanan herhangi bir yanlış anlama veya yanlış yorumlamadan sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->