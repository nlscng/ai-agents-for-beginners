# Thiết lập Khóa học

## Giới thiệu

Bài học này sẽ hướng dẫn cách chạy các ví dụ mã nguồn của khóa học này.

## Tham gia với các học viên khác và Nhận trợ giúp

Trước khi bạn bắt đầu clone repo của mình, hãy tham gia [Kênh Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) để nhận trợ giúp về thiết lập, trả lời bất kỳ câu hỏi nào về khóa học, hoặc kết nối với các học viên khác.

## Sao chép hoặc Fork kho lưu trữ này

Để bắt đầu, hãy clone hoặc fork kho lưu trữ GitHub. Việc này sẽ tạo phiên bản riêng của tài liệu khóa học để bạn có thể chạy, kiểm thử, và điều chỉnh mã!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork kho lưu trữ</a>

Bạn giờ sẽ có phiên bản đã fork của khóa học này tại liên kết sau:

![Kho đã fork](../../../translated_images/vi/forked-repo.33f27ca1901baa6a.webp)

### Sao chép nông (khuyến nghị cho workshop / Codespaces)

  >Kho lưu trữ đầy đủ có thể lớn (~3 GB) khi bạn tải xuống toàn bộ lịch sử và tất cả các tệp. Nếu bạn chỉ tham gia hội thảo hoặc chỉ cần vài thư mục bài học, sao chép nông (hoặc sao chép thưa) sẽ tránh hầu hết việc tải xuống đó bằng cách rút ngắn lịch sử và/hoặc bỏ qua các blob.

#### Sao chép nông nhanh — lịch sử tối thiểu, tất cả tệp

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

Để chỉ clone lịch sử commit mới nhất (tải xuống nhỏ):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Clone một phần (sparse) — blob tối thiểu + chỉ các thư mục đã chọn

This uses partial clone and sparse-checkout (requires Git 2.25+ and recommended modern Git with partial clone support):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Traverse into the repo folder:

```bash|powershell
cd ai-agents-for-beginners
```

Then specify which folders you want (example below shows two folders):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

After cloning and verifying the files, if you only need files and want to free space (no git history), please delete the repository metadata (💀irreversible — you will lose all Git functionality: no commits, pulls, pushes, or history access).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Sử dụng GitHub Codespaces (khuyến nghị để tránh tải xuống lớn trên máy cục bộ)

- Tạo một Codespace mới cho repo này qua [Giao diện GitHub](https://github.com/codespaces).  

- Trong terminal của codespace mới tạo, chạy một trong các lệnh shallow/sparse clone ở trên để chỉ đưa các thư mục bài học bạn cần vào workspace của Codespace.
- Tùy chọn: sau khi clone bên trong Codespaces, xóa .git để thu hồi thêm dung lượng (xem các lệnh xóa ở trên).
- Lưu ý: Nếu bạn muốn mở repo trực tiếp trong Codespaces (không clone thêm), hãy biết rằng Codespaces sẽ xây dựng môi trường devcontainer và có thể vẫn cung cấp nhiều thứ hơn bạn cần. Clone một bản shallow bên trong Codespace mới cho bạn kiểm soát tốt hơn việc sử dụng đĩa.

#### Mẹo

- Luôn thay URL clone bằng fork của bạn nếu bạn muốn chỉnh sửa/commit.
- Nếu bạn sau này cần thêm lịch sử hoặc tệp, bạn có thể fetch chúng hoặc điều chỉnh sparse-checkout để bao gồm các thư mục bổ sung.

## Chạy mã

Khóa học này cung cấp một loạt Jupyter Notebooks mà bạn có thể chạy để có kinh nghiệm thực hành xây dựng các tác nhân AI.

The code samples use either:

**Yêu cầu Tài khoản GitHub - Miễn phí**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Được gắn nhãn là (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Được gắn nhãn là (autogen.ipynb)

**Yêu cầu Đăng ký Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Được gắn nhãn là (azureaiagent.ipynb)

Chúng tôi khuyến khích bạn thử cả ba loại ví dụ để xem loại nào phù hợp nhất với bạn.

Dù bạn chọn lựa nào, nó sẽ quyết định các bước thiết lập mà bạn cần làm theo bên dưới:

## Yêu cầu

- Python 3.12+
  - **LƯU Ý**: Nếu bạn chưa cài Python3.12, hãy cài đặt nó.  Sau đó tạo venv của bạn bằng python3.12 để đảm bảo các phiên bản đúng được cài từ file requirements.txt.
  
    >Ví dụ

    Tạo thư mục venv Python:

    ```bash|powershell
    python -m venv venv
    ```

    Sau đó kích hoạt môi trường venv cho:

    ```bash
    # zsh hoặc bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Đối với ví dụ mã dùng .NET, đảm bảo bạn cài đặt [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) hoặc mới hơn. Sau đó, kiểm tra phiên bản .NET SDK đã cài:

    ```bash|powershell
    dotnet --list-sdks
    ```

- A GitHub Account - For Access to the GitHub Models Marketplace
- Azure Subscription - For Access to Microsoft Foundry
- Microsoft Foundry Account - For Access to the Azure AI Agent Service

Chúng tôi đã bao gồm một file `requirements.txt` ở thư mục gốc của repo này chứa tất cả các gói Python cần thiết để chạy các ví dụ mã.

Bạn có thể cài chúng bằng cách chạy lệnh sau trong terminal tại thư mục gốc của repository:

```bash|powershell
pip install -r requirements.txt
```

Chúng tôi khuyến nghị tạo một môi trường ảo Python để tránh xung đột và sự cố.

## Thiết lập VSCode

Hãy đảm bảo bạn đang dùng đúng phiên bản Python trong VSCode.

![hình ảnh](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Thiết lập cho các mẫu sử dụng GitHub Models 

### Bước 1: Lấy Token Truy cập Cá nhân (PAT) của GitHub

Khóa học này tận dụng GitHub Models Marketplace, cung cấp truy cập miễn phí tới các mô hình ngôn ngữ lớn (LLMs) mà bạn sẽ dùng để xây dựng các tác nhân AI.

Để sử dụng GitHub Models, bạn sẽ cần tạo một [Token Truy cập Cá nhân GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Bạn có thể làm điều này bằng cách vào <a href="https://github.com/settings/personal-access-tokens" target="_blank">Cài đặt Token Truy cập Cá nhân</a> trong tài khoản GitHub của bạn.

Vui lòng tuân thủ [Nguyên tắc Quyền Hạn Tối Thiểu](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) khi tạo token. Điều này có nghĩa bạn chỉ nên cấp cho token các quyền cần thiết để chạy các ví dụ mã trong khóa học này.

1. Select the `Fine-grained tokens` option on the left side of your screen by traversing to the **Developer settings**

   ![Cài đặt Nhà phát triển](../../../translated_images/vi/profile_developer_settings.410a859fe749c755.webp)

   Then select `Generate new token`.

   ![Tạo Token](../../../translated_images/vi/fga_new_token.1c1a234afe202ab3.webp)

2. Enter a descriptive name for your token that reflects its purpose, making it easy to identify later.

    🔐 Khuyến nghị Thời lượng Token

    Thời lượng đề nghị: 30 ngày
    Để an toàn hơn, bạn có thể chọn khoảng thời gian ngắn hơn—ví dụ như 7 ngày 🛡️
    Đây là cách tuyệt vời để đặt mục tiêu cá nhân và hoàn thành khóa học khi động lực học tập của bạn cao 🚀.

    ![Tên Token và Ngày hết hạn](../../../translated_images/vi/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit the token's scope to your fork of this repository.

    ![Giới hạn phạm vi tới kho đã fork](../../../translated_images/vi/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict the token's permissions: Under **Permissions**, click **Account** tab, and click the "+ Add permissions" button. A dropdown will appear. Please search for **Models** and check the box for it.

    ![Thêm Quyền Models](../../../translated_images/vi/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify the permissions required before generating the token. ![Xác minh Quyền](../../../translated_images/vi/verify_permissions.06bd9e43987a8b21.webp)

6. Before generating the token, ensure you are ready to store the token in a secure place like a password manager vault, as it will not be shown again after you create it. ![Lưu Token An toàn](../../../translated_images/vi/store_token_securely.08ee2274c6ad6caf.webp)

Sao chép token mới vừa tạo. Bây giờ bạn sẽ thêm token này vào file `.env` có kèm trong khóa học.

### Bước 2: Tạo file `.env` của bạn

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

Với token đã sao chép, mở file `.env` trong trình soạn thảo ưa thích và dán token vào trường `GITHUB_TOKEN`.

![Trường GitHub Token](../../../translated_images/vi/github_token_field.20491ed3224b5f4a.webp)

Bạn giờ nên có thể chạy các ví dụ mã của khóa học này.

## Thiết lập cho các ví dụ sử dụng Microsoft Foundry và Azure AI Agent Service

### Bước 1: Lấy Endpoint Dự án Azure của bạn


Follow the steps to creating a hub and project in Azure AI Foundry found here: [Tổng quan tài nguyên Hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Microsoft Foundry portal.

![Chuỗi kết nối dự án](../../../translated_images/vi/project-endpoint.8cf04c9975bbfbf1.webp)

### Bước 2: Tạo file `.env` của bạn

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

Với token đã sao chép, mở file `.env` trong trình soạn thảo ưa thích và dán token vào trường `PROJECT_ENDPOINT`.

### Bước 3: Đăng nhập vào Azure

As a security best practice, we'll use [xác thực không dùng khóa (keyless authentication)](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) to authenticate to Azure OpenAI with Microsoft Entra ID. 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## Biến Môi trường Bổ sung - Azure Search và Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

### Trang Tổng quan (Dự án)

- `AZURE_SUBSCRIPTION_ID` - Kiểm tra **Project details** trên trang **Overview** của dự án bạn.

- `AZURE_AI_PROJECT_NAME` - Xem phía trên trang **Overview** của dự án.

- `AZURE_OPENAI_SERVICE` - Tìm mục này trong tab **Included capabilities** cho **Azure OpenAI Service** trên trang **Overview**.

### Trung tâm Quản lý

- `AZURE_OPENAI_RESOURCE_GROUP` - Vào **Project properties** trên trang **Overview** của **Management Center**.

- `GLOBAL_LLM_SERVICE` - Dưới **Connected resources**, tìm tên kết nối **Azure AI Services**. Nếu không thấy, kiểm tra **Azure portal** trong resource group của bạn để biết tên resource AI Services.

### Trang Mô hình + Endpoints

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Chọn embedding model của bạn (ví dụ, `text-embedding-ada-002`) và ghi lại **Deployment name** từ chi tiết mô hình.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Chọn chat model của bạn (ví dụ, `gpt-4o-mini`) và ghi lại **Deployment name** từ chi tiết mô hình.

### Cổng Azure

- `AZURE_OPENAI_ENDPOINT` - Tìm **Azure AI services**, nhấp vào nó, sau đó vào **Resource Management**, **Keys and Endpoint**, cuộn xuống đến "Azure OpenAI endpoints", và sao chép mục ghi "Language APIs".

- `AZURE_OPENAI_API_KEY` - Từ cùng màn hình, sao chép KEY 1 hoặc KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Tìm resource **Azure AI Search** của bạn, nhấp vào nó và xem **Overview**.

- `AZURE_SEARCH_API_KEY` - Sau đó vào **Settings** rồi **Keys** để sao chép primary hoặc secondary admin key.

### Trang Web Ngoài

- `AZURE_OPENAI_API_VERSION` - Visit the [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Thiết lập xác thực không khóa

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Gặp khó khăn?
Nếu bạn gặp bất kỳ vấn đề nào khi chạy thiết lập này, hãy tham gia vào <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord Cộng đồng Azure AI</a> hoặc <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">tạo một issue</a>.

## Bài học tiếp theo

Bây giờ bạn đã sẵn sàng chạy mã cho khóa học này. Chúc bạn học tốt và khám phá thêm về thế giới của các tác nhân AI! 

[Giới thiệu về các tác nhân AI và các trường hợp sử dụng](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Miễn trừ trách nhiệm:
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng bản dịch tự động có thể chứa lỗi hoặc sai sót. Văn bản gốc bằng ngôn ngữ gốc của tài liệu nên được coi là nguồn chính thức. Đối với những thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do người dịch thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->