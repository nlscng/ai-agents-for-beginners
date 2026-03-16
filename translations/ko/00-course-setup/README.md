# 과정 설정

## 소개

이 수업에서는 이 과정의 코드 샘플을 실행하는 방법을 다룹니다.

## 다른 학습자와 함께 참여하고 도움 받기

저장소를 복제(clone)하기 전에 [AI Agents For Beginners Discord 채널](https://aka.ms/ai-agents/discord)에 참여하여 설정 관련 도움이나 과정에 대한 질문, 또는 다른 학습자와 소통할 수 있습니다.

## 이 저장소 복제 또는 포크하기

먼저 GitHub 저장소를 복제하거나 포크하세요. 이렇게 하면 과정 자료의 자신만의 버전을 만들어 코드를 실행, 테스트, 수정할 수 있습니다!

<a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">저장소 포크하기</a> 링크를 클릭해 진행할 수 있습니다.

아래 링크에서 포크된 이 과정의 자신만의 버전을 확인할 수 있어야 합니다:

![Forked Repo](../../../translated_images/ko/forked-repo.33f27ca1901baa6a.webp)

### 얕은 복제 (워크숍 / Codespaces에 권장)

  >전체 저장소는 전체 이력과 모든 파일을 다운로드하면 상당히 클 수 있습니다(~3GB). 워크숍에 참석하거나 일부 수업 폴더만 필요할 경우, 얕은 복제(shallow clone)나 부분 복제(sparse clone)를 사용하면 대부분 이력을 생략하거나 특정 폴더만 받아 다운로드를 줄일 수 있습니다.

#### 빠른 얕은 복제 — 최소 이력, 모든 파일

아래 명령에서 `<your-username>`를 자신의 포크 URL(또는 업스트림 URL)로 바꾸세요.

최신 커밋 이력만 복제하기 (다운로드 용량 적음):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

특정 브랜치만 복제하기:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### 부분 (스패어스) 복제 — 최소 블롭 + 선택한 폴더만

이 방법은 부분 복제와 sparse-checkout을 사용합니다 (Git 2.25 이상, partial clone 지원이 포함된 최신 Git 권장):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

저장소 폴더로 이동하기:

```bash|powershell
cd ai-agents-for-beginners
```

필요한 폴더 지정하기 (아래 예시는 두 폴더):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

복제 후 파일을 확인하고, 파일만 필요하거나 공간을 비워야 할 경우 (git 이력이 필요 없을 때) 저장소 메타데이터를 삭제하세요 (💀돌이킬 수 없음 — 모든 Git 기능 소실: 커밋, 풀, 푸시, 이력 접근 불가).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# 파워셸
Remove-Item -Recurse -Force .git
```

#### GitHub Codespaces 사용하기 (로컬 대용량 다운로드 회피 권장)

- [GitHub UI](https://github.com/codespaces)에서 이 저장소용 새 Codespace를 만드세요.

- 새로 생성된 Codespace 터미널에서 위 얕은/스패어스 복제 명령 중 하나를 실행해 필요한 수업 폴더만 가져오세요.
- 선택 사항: Codespaces 내 복제 완료 후 .git 제거하여 공간 확보 (위 제거 명령 참고).
- 참고: 저장소를 Codespaces에서 직접 열 경우(devcontainer 환경이 구성되고 필요한 것 이상이 프로비저닝될 수 있음), 새 Codespace 내에서 얕은 복제로 복제하는 것이 디스크 사용 제어에 더 좋습니다.

#### 팁

- 편집/커밋하려면 복제 URL을 항상 자신의 포크로 변경하세요.
- 나중에 더 많은 이력이나 파일이 필요하면 펫치하거나 sparse-checkout 설정을 조정해 추가 폴더를 포함할 수 있습니다.

## 코드 실행하기

이 과정은 AI 에이전트를 직접 만들어보는 실습으로, 일련의 Jupyter 노트북을 제공합니다.

코드 샘플은 다음 중 하나를 사용합니다:

**GitHub 계정 필요 - 무료**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. (autogen.ipynb)

**Azure 구독 필요**:
3) Azure AI Foundry + Azure AI Agent Service. (azureaiagent.ipynb)

세 가지 예제 모두 시험해보고 자신에게 맞는 유형을 찾아보시기 바랍니다.

어느 옵션을 선택하든 아래 설정 단계가 달라집니다.

## 요구 사항

- Python 3.12 이상
  - **참고**: Python3.12가 없다면 설치하세요. 그 후 python3.12로 venv를 만들어 requirements.txt의 올바른 버전이 설치되도록 합니다.

    >예시

    Python venv 디렉터리 생성:

    ```bash|powershell
    python -m venv venv
    ```

    다음으로 venv 환경 활성화:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10 이상: .NET을 사용하는 샘플 코드의 경우 [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) 이상을 설치하세요. 설치 후 SDK 버전 확인:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub 계정 - GitHub Models Marketplace 접근용
- Azure 구독 - Microsoft Foundry 접근용
- Microsoft Foundry 계정 - Azure AI Agent Service 접근용

저장소 루트에 코드 샘플 실행에 필요한 Python 패키지 목록이 담긴 `requirements.txt`가 포함되어 있습니다.

터미널에서 아래 명령어로 설치하세요:

```bash|powershell
pip install -r requirements.txt
```

충돌과 문제 방지를 위해 Python 가상환경 사용을 권장합니다.

## VSCode 설정

VSCode에서 올바른 Python 버전을 사용 중인지 확인하세요.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## GitHub Models 사용하는 샘플 설정

### 1단계: GitHub 개인 액세스 토큰 (PAT) 받기

이 과정은 GitHub Models Marketplace를 활용해 LLM(대형언어모델)을 무료로 이용할 수 있게 합니다.

GitHub Models 사용을 위해 [GitHub 개인 액세스 토큰](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)을 생성해야 합니다.

<a href="https://github.com/settings/personal-access-tokens" target="_blank">GitHub 계정의 개인 액세스 토큰 설정</a>에서 진행할 수 있습니다.

[최소 권한 원칙](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely)에 따라 토큰에 필요한 권한만 부여하세요.

1. 화면 왼쪽의 **개발자 설정**에서 `세밀한 토큰(Fine-grained tokens)` 옵션 선택

   ![Developer settings](../../../translated_images/ko/profile_developer_settings.410a859fe749c755.webp)

   그 후 `새 토큰 생성(Generate new token)` 선택.

   ![Generate Token](../../../translated_images/ko/fga_new_token.1c1a234afe202ab3.webp)

2. 토큰 용도를 잘 알 수 있도록 설명 이름 입력.

    🔐 토큰 기간 권장

    권장 기간: 30일
    보안을 강화하려면 7일과 같이 짧은 기간도 가능 🛡️
    학습 모멘텀이 있을 때 과정을 끝내기에 좋습니다 🚀.

    ![Token Name and Expiration](../../../translated_images/ko/token-name-expiry-date.a095fb0de6386864.webp)

3. 토큰 권한을 본 저장소 포크로 제한.

    ![Limit scope to fork repository](../../../translated_images/ko/token_repository_limit.924ade5e11d9d8bb.webp)

4. 토큰 권한 제한: **권한(Permissions)**에서 **계정(Account)** 탭을 선택 후 "+ 권한 추가" 버튼 클릭. 드롭다운이 뜨면 **Models**를 찾아 선택.

    ![Add Models Permission](../../../translated_images/ko/add_models_permissions.c0c44ed8b40fc143.webp)

5. 토큰 생성 전에 권한을 다시 확인. ![Verify Permissions](../../../translated_images/ko/verify_permissions.06bd9e43987a8b21.webp)

6. 생성 후 토큰은 다시 보이지 않으므로 안전한 장소(비밀번호 관리자 등)에 저장하세요. ![Store Token Securely](../../../translated_images/ko/store_token_securely.08ee2274c6ad6caf.webp)

방금 생성한 토큰을 복사하세요. 이후 이 과정의 `.env` 파일에 추가할 예정입니다.

### 2단계: `.env` 파일 만들기

터미널에서 아래 명령어를 실행해 `.env` 파일을 생성하세요.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# 파워셸
Copy-Item .env.example .env
```

예제 파일을 복사해 `.env` 파일을 생성하고 환경 변수 값을 기입할 수 있습니다.

복사한 토큰을 `.env` 파일의 `GITHUB_TOKEN` 필드에 붙여넣으세요.

![GitHub Token Field](../../../translated_images/ko/github_token_field.20491ed3224b5f4a.webp)

이제 이 과정의 코드 샘플을 실행할 수 있습니다.

## Microsoft Foundry 및 Azure AI Agent Service 사용하는 샘플 설정

### 1단계: Azure 프로젝트 엔드포인트 가져오기

Azure AI Foundry에서 허브와 프로젝트를 만드는 단계는 여기서 확인하세요: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

프로젝트 생성 후, Microsoft Foundry 포털 내 프로젝트 **개요(Overview)** 페이지에서 연결 문자열을 확인하세요.

![Project Connection String](../../../translated_images/ko/project-endpoint.8cf04c9975bbfbf1.webp)

### 2단계: `.env` 파일 만들기

터미널에서 아래 명령어를 실행해 `.env` 파일을 생성하세요.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# 파워셸
Copy-Item .env.example .env
```

예제 파일을 복사해 `.env` 파일을 생성하고 환경 변수 값을 기입할 수 있습니다.

복사한 값을 `.env` 파일의 `PROJECT_ENDPOINT` 필드에 붙여넣으세요.

### 3단계: Azure 로그인

보안상 이유로 Microsoft Entra ID를 사용한 [키리스(keyless) 인증](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst)을 통해 Azure OpenAI에 인증합니다.

터미널을 열고 `az login --use-device-code` 명령을 실행해 Azure 계정에 로그인하세요.

로그인 후 터미널에서 사용할 구독을 선택하세요.

## 추가 환경 변수 - Azure Search 및 Azure OpenAI

Agentic RAG 수업 - 5강에서는 Azure Search와 Azure OpenAI를 사용하는 샘플이 있습니다.

해당 샘플 실행 시 `.env` 파일에 다음 환경 변수를 추가해야 합니다:

### 개요 페이지 (프로젝트)

- `AZURE_SUBSCRIPTION_ID` - 프로젝트 **개요** 페이지의 **프로젝트 세부 정보**에서 확인.

- `AZURE_AI_PROJECT_NAME` - 프로젝트 **개요** 페이지 상단에서 확인.

- `AZURE_OPENAI_SERVICE` - **개요** 페이지의 **포함된 기능(Included capabilities)** 탭 내 **Azure OpenAI Service**에서 확인.

### 관리 센터

- `AZURE_OPENAI_RESOURCE_GROUP` - **관리 센터**의 **개요** 페이지 내 **프로젝트 속성**에서 확인.

- `GLOBAL_LLM_SERVICE` - **연결된 리소스**에서 **Azure AI Services** 연결 이름 확인. 없다면 Azure 포털 내 해당 리소스 그룹에서 AI Services 리소스 이름 체크.

### 모델 + 엔드포인트 페이지

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 임베딩 모델(예: `text-embedding-ada-002`) 선택 후 모델 상세 정보에서 **배포 이름(Deployment name)** 확인.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - 채팅 모델(예: `gpt-4o-mini`) 선택 후 모델 상세 정보에서 **배포 이름** 확인.

### Azure 포털

- `AZURE_OPENAI_ENDPOINT` - **Azure AI 서비스** 항목 클릭 후 **리소스 관리 > 키 및 엔드포인트**로 이동, "Azure OpenAI endpoints" 항목에서 "Language APIs" 엔드포인트 복사.

- `AZURE_OPENAI_API_KEY` - 같은 화면에서 키 1 또는 키 2 복사.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Azure AI Search 리소스 선택 후 **개요** 확인.

- `AZURE_SEARCH_API_KEY` - **설정 > 키**에서 기본 또는 보조 관리자 키 복사.

### 외부 웹페이지

- `AZURE_OPENAI_API_VERSION` - [API 버전 수명 주기](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) 페이지의 **Latest GA API release** 확인.

### 키리스 인증 설정

자격 증명을 하드코딩하지 않고 Azure OpenAI에 키리스 연결을 사용합니다. `DefaultAzureCredential`를 가져와 나중에 해당 함수를 호출해 인증 정보를 얻습니다.

```python
# 파이썬
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## 어디서 막히셨나요?
이 설정을 실행하는 데 문제가 있으면 <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a>에 참여하거나 <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">이슈를 생성</a>하세요.

## 다음 수업

이제 이 과정의 코드를 실행할 준비가 되었습니다. AI 에이전트의 세계에 대해 더 많이 배우며 즐거운 학습 되세요!

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**면책 조항**:  
이 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 노력하고 있으나, 자동 번역에는 오류나 부정확성이 포함될 수 있음을 양지해 주시기 바랍니다. 원문 문서는 해당 언어의 권위 있는 자료로 간주되어야 합니다. 중요한 정보에 대해서는 전문적인 인간 번역을 권장합니다. 본 번역 사용으로 인한 오해나 잘못된 해석에 대해 당사는 어떠한 책임도 지지 않습니다.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->