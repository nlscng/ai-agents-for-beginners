# Configuração do Curso

## Introdução

Esta lição irá abordar como executar os exemplos de código deste curso.

## Junte-se a Outros Estudantes e Obtenha Ajuda

Antes de começar a clonar o seu repositório, junte-se ao [canal Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) para obter ajuda com a configuração, esclarecer dúvidas sobre o curso ou para se conectar com outros alunos.

## Clonar ou Fazer Fork deste Repositório

Para começar, por favor clone ou faça fork do Repositório GitHub. Isto irá criar a sua própria versão do material do curso para que possa executar, testar e ajustar o código!

Isto pode ser feito clicando no link para <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fazer fork do repositório</a>

Deverá agora ter a sua própria versão forkada deste curso no seguinte link:

![Forked Repo](../../../translated_images/pt-PT/forked-repo.33f27ca1901baa6a.webp)

### Clone Raso (recomendado para workshop / Codespaces)

  >O repositório completo pode ser grande (~3 GB) quando descarregar todo o histórico e todos os ficheiros. Se só vai assistir ao workshop ou só precisa de algumas pastas das lições, um clone raso (ou clone esparso) evita a maior parte desse download ao truncar o histórico e/ou pular blobs.

#### Clone raso rápido — histórico mínimo, todos os ficheiros

Substitua `<your-username>` nos comandos abaixo pelo URL do seu fork (ou pelo URL upstream, se preferir).

Para clonar apenas o histórico do último commit (download pequeno):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Para clonar um ramo específico:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Clone parcial (esparso) — blobs mínimos + só pastas selecionadas

Isto utiliza clone parcial e sparse-checkout (requere Git 2.25+ e Git moderno recomendado com suporte a clone parcial):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Entre na pasta do repositório:

```bash|powershell
cd ai-agents-for-beginners
```

Depois especifique as pastas que deseja (exemplo abaixo mostra duas pastas):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Após clonar e verificar os ficheiros, se só precisar dos ficheiros e quiser libertar espaço (sem histórico git), por favor apague os metadados do repositório (💀 irreversível — irá perder toda a funcionalidade Git: sem commits, pulls, pushes ou acesso ao histórico).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Usar GitHub Codespaces (recomendado para evitar downloads grandes locais)

- Crie um novo Codespace para este repositório através da [interface GitHub UI](https://github.com/codespaces).  

- No terminal do Codespace recém criado, execute um dos comandos de clone rasos / esparsos acima para trazer apenas as pastas de lições que precisa para o espaço de trabalho do Codespace.
- Opcional: após clonar dentro dos Codespaces, remova .git para recuperar espaço extra (ver comandos de remoção acima).
- Nota: Se preferir abrir o repositório diretamente no Codespaces (sem um clone extra), tenha em mente que o Codespaces irá construir o ambiente devcontainer e poderá ainda assim provisionar mais do que precisa. Clonar uma cópia rasa dentro de um Codespace novo dá mais controlo sobre o uso do disco.

#### Dicas

- Substitua sempre o URL de clone pelo seu fork se quiser editar/fazer commit.
- Se precisar depois de mais histórico ou ficheiros, pode fetch ou ajustar o sparse-checkout para incluir pastas adicionais.

## Execução do Código

Este curso oferece uma série de Jupyter Notebooks que pode executar para ganhar experiência prática a criar Agentes de IA.

Os exemplos de código utilizam:

**Requer Conta GitHub - Gratuito**:

1) Framework Semantic Kernel Agent + GitHub Models Marketplace. Identificado como (semantic-kernel.ipynb)
2) Framework AutoGen + GitHub Models Marketplace. Identificado como (autogen.ipynb)

**Requer Subscrição Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Identificado como (azureaiagent.ipynb)

Encorajamos a experimentar os três tipos de exemplos para ver qual funciona melhor para si.

Qualquer que seja a opção que escolher, irá determinar quais os passos de configuração que deve seguir abaixo:

## Requisitos

- Python 3.12+
  - **NOTA**: Se não tem Python3.12 instalado, assegure-se que o instala. Depois crie o seu ambiente virtual venv usando python3.12 para garantir as versões corretas são instaladas do ficheiro requirements.txt.
  
    >Exemplo

    Criar diretoria venv Python:

    ```bash|powershell
    python -m venv venv
    ```

    Depois ative o ambiente venv para:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Para os exemplos que usam .NET, certifique-se de instalar o [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) ou superior. Depois, verifique a versão do SDK .NET instalado:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Conta GitHub - Para acesso ao GitHub Models Marketplace
- Subscrição Azure - Para acesso ao Microsoft Foundry
- Conta Microsoft Foundry - Para acesso ao Azure AI Agent Service

Incluímos um ficheiro `requirements.txt` na raiz deste repositório que contém todos os pacotes Python necessários para executar os exemplos.

Pode instalá-los executando o seguinte comando no terminal na raiz do repositório:

```bash|powershell
pip install -r requirements.txt
```

Recomendamos criar um ambiente virtual Python para evitar conflitos e problemas.

## Configurar VSCode

Assegure-se de que está a usar a versão correta do Python no VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Configuração para Exemplos usando GitHub Models

### Passo 1: Recupere o Seu Token Pessoal de Acesso do GitHub (PAT)

Este curso utiliza o GitHub Models Marketplace, proporcionando acesso gratuito a Modelos de Linguagem Extensa (LLMs) que irá utilizar para construir Agentes de IA.

Para usar os GitHub Models, será necessário criar um [Token Pessoal de Acesso do GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Isto pode ser feito indo às <a href="https://github.com/settings/personal-access-tokens" target="_blank">configurações de Tokens Pessoais de Acesso</a> na sua conta GitHub.

Por favor siga o [Princípio do Menor Privilégio](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) ao criar o token. Isto significa que deve apenas dar ao token as permissões necessárias para executar os exemplos de código neste curso.

1. Selecione a opção `Fine-grained tokens` no lado esquerdo do seu ecrã, navegando até às **Configurações do desenvolvedor**

   ![Developer settings](../../../translated_images/pt-PT/profile_developer_settings.410a859fe749c755.webp)

   Depois selecione `Gerar novo token`.

   ![Generate Token](../../../translated_images/pt-PT/fga_new_token.1c1a234afe202ab3.webp)

2. Introduza um nome descritivo para o seu token que reflita o seu propósito, para que seja fácil identificá-lo mais tarde.

    🔐 Recomendação da duração do token

    Duração recomendada: 30 dias  
    Para maior segurança, pode optar por um período mais curto — como 7 dias 🛡️  
    É uma ótima forma de estabelecer uma meta pessoal e completar o curso enquanto o seu ímpeto de aprendizagem está elevado 🚀.

    ![Token Name and Expiration](../../../translated_images/pt-PT/token-name-expiry-date.a095fb0de6386864.webp)

3. Limite o âmbito do token ao seu fork deste repositório.

    ![Limit scope to fork repository](../../../translated_images/pt-PT/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrinja as permissões do token: Sob **Permissões**, clique no separador **Conta** e clique no botão "+ Adicionar permissões". Aparecerá um menu dropdown. Procure por **Models** e assinale a caixa correspondente.

    ![Add Models Permission](../../../translated_images/pt-PT/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verifique as permissões requeridas antes de gerar o token. ![Verify Permissions](../../../translated_images/pt-PT/verify_permissions.06bd9e43987a8b21.webp)

6. Antes de gerar o token, assegure-se de que está pronto para guardar o token num local seguro, como um cofre de gestor de passwords, pois não será mostrado novamente após a sua criação. ![Store Token Securely](../../../translated_images/pt-PT/store_token_securely.08ee2274c6ad6caf.webp)

Copie o seu novo token que acabou de criar. Agora irá adicioná-lo ao seu ficheiro `.env` incluído neste curso.

### Passo 2: Crie o Seu Ficheiro `.env`

Para criar o seu ficheiro `.env` execute o seguinte comando no terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Isto irá copiar o ficheiro exemplo e criar um `.env` na sua diretoria onde preencherá os valores das variáveis de ambiente.

Com o seu token copiado, abra o ficheiro `.env` no seu editor de texto favorito e cole o seu token no campo `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/pt-PT/github_token_field.20491ed3224b5f4a.webp)

Deverá agora conseguir executar os exemplos de código deste curso.

## Configuração para Exemplos usando Microsoft Foundry e Azure AI Agent Service

### Passo 1: Recupere o Endpoint do Seu Projeto Azure

Siga os passos para criar um hub e projeto no Azure AI Foundry encontrados aqui: [Visão geral dos recursos do Hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

Uma vez criado o seu projeto, deverá recuperar a string de conexão do projeto.

Isto pode ser feito indo à página **Overview** do seu projeto no portal Microsoft Foundry.

![Project Connection String](../../../translated_images/pt-PT/project-endpoint.8cf04c9975bbfbf1.webp)

### Passo 2: Crie o Seu Ficheiro `.env`

Para criar o seu ficheiro `.env` execute o seguinte comando no terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Isto irá copiar o ficheiro exemplo e criar um `.env` na sua diretoria onde preencherá os valores das variáveis de ambiente.

Com a sua string de conexão copiada, abra o ficheiro `.env` no editor de texto favorito e cole-a no campo `PROJECT_ENDPOINT`.

### Passo 3: Iniciar Sessão no Azure

Como boa prática de segurança, vamos usar [autenticação sem chave](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) para autenticar no Azure OpenAI com Microsoft Entra ID.

Abra um terminal e execute `az login --use-device-code` para iniciar sessão na sua conta Azure.

Depois de iniciar sessão, selecione a sua subscrição no terminal.

## Variáveis de Ambiente Adicionais - Azure Search e Azure OpenAI

Para a Lição Agentic RAG - Lição 5 - existem exemplos que usam Azure Search e Azure OpenAI.

Se quiser executar estes exemplos, terá de adicionar as seguintes variáveis de ambiente ao seu ficheiro `.env`:

### Página de Visão Geral (Projeto)

- `AZURE_SUBSCRIPTION_ID` - Verifique os **Detalhes do Projeto** na página **Overview** do seu projeto.

- `AZURE_AI_PROJECT_NAME` - Consulte o topo da página **Overview** do seu projeto.

- `AZURE_OPENAI_SERVICE` - Encontre este na aba **Included capabilities** para **Azure OpenAI Service** na página **Overview**.

### Centro de Gestão

- `AZURE_OPENAI_RESOURCE_GROUP` - Vá às **Propriedades do Projeto** na página **Overview** do **Management Center**.

- `GLOBAL_LLM_SERVICE` - Sob **Recursos Conectados**, encontre o nome da ligação **Azure AI Services**. Se não estiver listado, consulte o **portal Azure** na sua resource group para o nome do recurso AI Services.

### Página de Modelos + Endpoints

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Selecione o seu modelo de embedding (ex.: `text-embedding-ada-002`) e anote o **Nome do Deployment** nos detalhes do modelo.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Selecione o seu modelo de chat (ex.: `gpt-4o-mini`) e anote o **Nome do Deployment** nos detalhes do modelo.

### Portal Azure

- `AZURE_OPENAI_ENDPOINT` - Procure por **Azure AI services**, clique, vá a **Gestão de Recursos**, **Chaves e Endpoint**, desça até aos "Azure OpenAI endpoints" e copie o que diz "APIs de Linguagem".

- `AZURE_OPENAI_API_KEY` - Na mesma página, copie a CHAVE 1 ou CHAVE 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Encontre o seu recurso **Azure AI Search**, clique e veja **Overview**.

- `AZURE_SEARCH_API_KEY` - Depois vá a **Configurações** e depois **Chaves** para copiar a chave admin primária ou secundária.

### Página Web Externa

- `AZURE_OPENAI_API_VERSION` - Visite a página [ciclo de vida da versão API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) sob **Mais recente lançamento GA da API**.

### Configurar autenticação sem chave

Em vez de codificar as credenciais, vamos usar uma ligação sem chave com Azure OpenAI. Para isso, vamos importar `DefaultAzureCredential` e mais tarde chamar a função `DefaultAzureCredential` para obter as credenciais.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Ficou Preso em Algum Lado?
Se tiver algum problema a executar esta configuração, entre no nosso <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord da Comunidade Azure AI</a> ou <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">crie um problema</a>.

## Próxima Aula

Está agora pronto para executar o código deste curso. Bom aprendizado sobre o mundo dos Agentes de IA!

[Introdução aos Agentes de IA e Casos de Uso de Agentes](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos pela precisão, tenha em atenção que traduções automáticas podem conter erros ou imprecisões. O documento original no seu idioma nativo deve ser considerado a fonte autoritária. Para informações críticas, recomenda-se tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->