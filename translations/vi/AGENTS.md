# AGENTS.md

## Tổng quan dự án

Kho lưu trữ này chứa "Các tác nhân AI cho người mới bắt đầu" - một khóa học giáo dục toàn diện dạy mọi thứ cần thiết để xây dựng các tác nhân AI. Khóa học gồm hơn 15 bài học bao gồm các kiến thức cơ bản, mẫu thiết kế, framework và triển khai sản xuất các tác nhân AI.

**Công nghệ chính:**
- Python 3.12+
- Jupyter Notebooks cho học tương tác
- Các Framework AI: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Dịch vụ AI Azure: Microsoft Foundry, Azure AI Agent Service
- Thị trường mô hình GitHub (có tầng miễn phí)

**Kiến trúc:**
- Cấu trúc theo bài học (thư mục 00-15+)
- Mỗi bài học bao gồm: tài liệu README, ví dụ mã (Jupyter notebooks), và hình ảnh
- Hỗ trợ đa ngôn ngữ qua hệ thống dịch tự động
- Nhiều lựa chọn framework cho mỗi bài học (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Lệnh thiết lập

### Yêu cầu trước

- Python 3.12 trở lên
- Tài khoản GitHub (cho các mô hình GitHub - tầng miễn phí)
- Đăng ký Azure (tùy chọn, cho dịch vụ AI Azure)

### Thiết lập ban đầu

1. **Sao chép hoặc fork kho lưu trữ:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # HOẶC
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Tạo và kích hoạt môi trường ảo Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Trên Windows: venv\Scripts\activate
   ```

3. **Cài đặt các phụ thuộc:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Cấu hình biến môi trường:**
   ```bash
   cp .env.example .env
   # Chỉnh sửa .env với các khóa API và điểm cuối của bạn
   ```


### Biến môi trường cần thiết

Đối với **Mô hình GitHub (Miễn phí)**:
- `GITHUB_TOKEN` - Mã truy cập cá nhân từ GitHub

Đối với **Dịch vụ AI Azure** (tùy chọn):
- `PROJECT_ENDPOINT` - Điểm cuối dự án Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Khóa API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL điểm cuối Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Tên triển khai mô hình chat
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Tên triển khai mô hình embeddings
- Cấu hình Azure bổ sung như trong `.env.example`

## Quy trình phát triển

### Chạy Jupyter Notebooks

Mỗi bài học có nhiều notebook cho các framework khác nhau:

1. **Khởi động Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Đi tới thư mục bài học** (ví dụ: `01-intro-to-ai-agents/code_samples/`)

3. **Mở và chạy notebooks:**
   - `*-semantic-kernel.ipynb` - Sử dụng framework Semantic Kernel
   - `*-autogen.ipynb` - Sử dụng framework AutoGen
   - `*-python-agent-framework.ipynb` - Sử dụng Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Sử dụng Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Sử dụng Azure AI Agent Service

### Làm việc với các Framework khác nhau

**Semantic Kernel + Mô hình GitHub:**
- Tầng miễn phí có sẵn với tài khoản GitHub
- Phù hợp cho học tập và thử nghiệm
- Mẫu file: `*-semantic-kernel*.ipynb`

**AutoGen + Mô hình GitHub:**
- Tầng miễn phí có sẵn với tài khoản GitHub
- Hỗ trợ điều phối đa tác nhân
- Mẫu file: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Framework mới nhất từ Microsoft
- Có sẵn cho Python và .NET
- Mẫu file: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Cần đăng ký Azure
- Tính năng sẵn sàng cho sản xuất
- Mẫu file: `*-azureaiagent.ipynb`

## Hướng dẫn kiểm tra

Kho lưu trữ này là kho giáo dục có mã ví dụ, không phải mã sản xuất với kiểm tra tự động. Để xác minh thiết lập và thay đổi của bạn:

### Kiểm tra thủ công

1. **Kiểm tra môi trường Python:**
   ```bash
   python --version  # Nên là 3.12 trở lên
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Kiểm tra chạy notebook:**
   ```bash
   # Chuyển đổi notebook thành script và chạy (kiểm tra các import)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Kiểm tra biến môi trường:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```


### Chạy các notebook riêng biệt

Mở notebook trong Jupyter và thực hiện các ô lần lượt. Mỗi notebook độc lập và bao gồm:
- Các câu lệnh import
- Tải cấu hình
- Ví dụ triển khai tác nhân
- Kết quả dự kiến trong các ô markdown

## Phong cách mã

### Quy ước Python

- **Phiên bản Python**: 3.12+
- **Phong cách mã**: Tuân thủ chuẩn PEP 8 của Python
- **Notebooks**: Dùng ô markdown rõ ràng để giải thích khái niệm
- **Imports**: Nhóm theo thư viện chuẩn, thư viện bên thứ ba, imports địa phương

### Quy ước Jupyter Notebook

- Bao gồm ô markdown mô tả trước ô code
- Thêm ví dụ kết quả trong notebook để tham khảo
- Dùng tên biến rõ ràng phù hợp khái niệm bài học
- Giữ thứ tự chạy notebook tuyến tính (ô 1 → 2 → 3...)

### Tổ chức file

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


## Xây dựng và Triển khai

### Xây dựng tài liệu

Kho dùng Markdown làm tài liệu:
- File README.md trong mỗi thư mục bài học
- README.md chính ở thư mục gốc kho lưu trữ
- Hệ thống dịch tự động qua GitHub Actions

### Pipeline CI/CD

Có trong `.github/workflows/`:

1. **co-op-translator.yml** - Dịch tự động sang hơn 50 ngôn ngữ
2. **welcome-issue.yml** - Chào mừng người tạo issue mới
3. **welcome-pr.yml** - Chào mừng người đóng góp pull request mới

### Triển khai

Đây là kho giáo dục - không có quy trình triển khai. Người dùng:
1. Fork hoặc sao chép kho lưu trữ
2. Chạy notebooks tại máy hoặc trong GitHub Codespaces
3. Học bằng cách sửa đổi và thử nghiệm ví dụ

## Hướng dẫn Pull Request

### Trước khi gửi

1. **Kiểm tra thay đổi:**
   - Chạy đầy đủ các notebook liên quan
   - Đảm bảo các ô chạy không lỗi
   - Kiểm tra kết quả đầu ra phù hợp

2. **Cập nhật tài liệu:**
   - Cập nhật README.md nếu thêm khái niệm mới
   - Thêm chú thích trong notebook cho đoạn mã phức tạp
   - Đảm bảo ô markdown giải thích rõ mục đích

3. **Thay đổi file:**
   - Tránh commit file `.env` (dùng `.env.example`)
   - Không commit thư mục `venv/` hoặc `__pycache__/`
   - Giữ kết quả đầu ra notebook khi minh họa khái niệm
   - Xóa file tạm và backup notebook (`*-backup.ipynb`)

### Định dạng tiêu đề PR

Dùng tiêu đề mô tả:
- `[Lesson-XX] Thêm ví dụ mới cho <khái niệm>`
- `[Fix] Sửa lỗi chính tả trong README bài học-XX`
- `[Update] Cải thiện ví dụ mã trong bài học-XX`
- `[Docs] Cập nhật hướng dẫn thiết lập`

### Kiểm tra bắt buộc

- Các notebook chạy không lỗi
- README rõ ràng và chính xác
- Tuân thủ mẫu mã có sẵn trong kho
- Duy trì sự thống nhất với các bài học khác

## Ghi chú bổ sung

### Các lỗi phổ biến

1. **Không khớp phiên bản Python:**
   - Đảm bảo dùng Python 3.12+
   - Một số gói không hoạt động với phiên bản cũ
   - Dùng `python3 -m venv` để chỉ định phiên bản Python rõ ràng

2. **Biến môi trường:**
   - Luôn tạo `.env` từ `.env.example`
   - Không commit file `.env` (đã có trong `.gitignore`)
   - Token GitHub cần quyền phù hợp

3. **Xung đột gói:**
   - Sử dụng môi trường ảo mới
   - Cài đặt từ `requirements.txt` thay vì từng gói riêng lẻ
   - Một số notebook yêu cầu thêm các gói được ghi trong ô markdown của chúng

4. **Dịch vụ Azure:**
   - Dịch vụ AI Azure yêu cầu đăng ký hoạt động
   - Một số tính năng chỉ dành cho vùng địa lý nhất định
   - Giới hạn tầng miễn phí áp dụng cho Mô hình GitHub

### Lộ trình học

Đề xuất học theo thứ tự:
1. **00-course-setup** - Bắt đầu với thiết lập môi trường
2. **01-intro-to-ai-agents** - Hiểu kiến thức cơ bản về tác nhân AI
3. **02-explore-agentic-frameworks** - Tìm hiểu các framework khác nhau
4. **03-agentic-design-patterns** - Các mẫu thiết kế chính
5. Tiếp tục theo thứ tự số bài học

### Lựa chọn Framework

Chọn framework dựa theo mục tiêu:
- **Học/Prototype**: Semantic Kernel + Mô hình GitHub (miễn phí)
- **Hệ thống đa tác nhân**: AutoGen
- **Tính năng mới nhất**: Microsoft Agent Framework (MAF)
- **Triển khai sản xuất**: Azure AI Agent Service

### Tìm trợ giúp

- Tham gia [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Xem file README của từng bài học để hướng dẫn cụ thể
- Tham khảo [README.md chính](./README.md) cho tổng quan khóa học
- Xem [Course Setup](./00-course-setup/README.md) để biết hướng dẫn chi tiết

### Đóng góp

Đây là dự án giáo dục mở. Hoan nghênh đóng góp:
- Cải thiện ví dụ mã
- Sửa lỗi chính tả hoặc lỗi
- Thêm chú thích giải thích
- Đề xuất chủ đề bài học mới
- Dịch sang ngôn ngữ khác

Xem [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) để biết các nhu cầu hiện tại.

## Bối cảnh dự án

### Hỗ trợ đa ngôn ngữ

Kho dùng hệ thống dịch tự động:
- Hơn 50 ngôn ngữ được hỗ trợ
- Bản dịch nằm trong thư mục `/translations/<mã-ngôn-ngữ>/`
- Workflow GitHub Actions xử lý cập nhật bản dịch
- File gốc bằng tiếng Anh ở thư mục gốc kho

### Cấu trúc bài học

Mỗi bài học theo mẫu nhất quán:
1. Hình thu nhỏ video có liên kết
2. Nội dung bài học viết (README.md)
3. Ví dụ mã với nhiều framework
4. Mục tiêu học và yêu cầu trước
5. Tài nguyên học thêm liên kết

### Đặt tên ví dụ mã

Định dạng: `<số-bài-học>-<tên-framework>.ipynb`
- `04-semantic-kernel.ipynb` - Bài 4, Semantic Kernel
- `07-autogen.ipynb` - Bài 7, AutoGen
- `14-python-agent-framework.ipynb` - Bài 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Bài 14, MAF .NET

### Thư mục đặc biệt

- `translated_images/` - Hình ảnh được bản địa hóa cho bản dịch
- `images/` - Hình ảnh gốc cho nội dung tiếng Anh
- `.devcontainer/` - Cấu hình container phát triển VS Code
- `.github/` - Workflow và mẫu GitHub Actions

### Các phụ thuộc

Các gói chính trong `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - Framework AutoGen
- `semantic-kernel` - Framework Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Dịch vụ AI Azure
- `azure-search-documents` - Tích hợp tìm kiếm Azure AI
- `chromadb` - Cơ sở dữ liệu vector cho các ví dụ RAG
- `chainlit` - Framework giao diện trò chuyện
- `browser_use` - Tự động hóa trình duyệt cho tác nhân
- `mcp[cli]` - Hỗ trợ Model Context Protocol
- `mem0ai` - Quản lý bộ nhớ cho tác nhân

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tuyên bố từ chối trách nhiệm**:  
Tài liệu này đã được dịch sử dụng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc sự không chính xác. Tài liệu gốc bằng ngôn ngữ ban đầu nên được coi là nguồn thông tin chính thức. Đối với những thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu nhầm hoặc giải thích sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->