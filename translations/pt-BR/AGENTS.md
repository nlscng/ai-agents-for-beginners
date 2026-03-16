# AGENTS.md

## Visão Geral do Projeto

Este repositório contém "Agentes de IA para Iniciantes" - um curso educacional abrangente que ensina tudo o que é necessário para construir Agentes de IA. O curso consiste em mais de 15 lições cobrindo fundamentos, padrões de design, frameworks e implantação em produção de agentes de IA.

**Tecnologias Principais:**
- Python 3.12+
- Jupyter Notebooks para aprendizado interativo
- Frameworks de IA: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Serviços Azure AI: Microsoft Foundry, Azure AI Agent Service
- Marketplace de Modelos GitHub (nível gratuito disponível)

**Arquitetura:**
- Estrutura baseada em lições (diretórios 00-15+)
- Cada lição contém: documentação README, exemplos de código (notebooks Jupyter) e imagens
- Suporte multilíngue via sistema automatizado de tradução
- Múltiplas opções de frameworks por lição (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Comandos de Configuração

### Pré-requisitos
- Python 3.12 ou superior
- Conta GitHub (para Modelos GitHub - nível gratuito)
- Assinatura Azure (opcional, para serviços Azure AI)

### Configuração Inicial

1. **Clone ou faça fork do repositório:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # OU
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Crie e ative o ambiente virtual Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # No Windows: venv\Scripts\activate
   ```

3. **Instale as dependências:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure as variáveis de ambiente:**
   ```bash
   cp .env.example .env
   # Edite o .env com suas chaves de API e endpoints
   ```

### Variáveis de Ambiente Necessárias

Para **Modelos GitHub (Gratuito)**:
- `GITHUB_TOKEN` - Token de acesso pessoal do GitHub

Para **Serviços Azure AI** (opcional):
- `PROJECT_ENDPOINT` - Endpoint do projeto Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Chave API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL do endpoint Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Nome da implantação para modelo de chat
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Nome da implantação para embeddings
- Configuração adicional da Azure conforme mostrado no `.env.example`

## Fluxo de Desenvolvimento

### Executando Jupyter Notebooks

Cada lição possui vários notebooks Jupyter para frameworks diferentes:

1. **Inicie o Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navegue até o diretório da lição** (ex.: `01-intro-to-ai-agents/code_samples/`)

3. **Abra e execute os notebooks:**
   - `*-semantic-kernel.ipynb` - Usando o framework Semantic Kernel
   - `*-autogen.ipynb` - Usando o framework AutoGen
   - `*-python-agent-framework.ipynb` - Usando Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Usando Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Usando Azure AI Agent Service

### Trabalhando com Diferentes Frameworks

**Semantic Kernel + Modelos GitHub:**
- Nível gratuito disponível com conta GitHub
- Bom para aprendizado e experimentação
- Padrão de arquivo: `*-semantic-kernel*.ipynb`

**AutoGen + Modelos GitHub:**
- Nível gratuito disponível com conta GitHub
- Capacidades de orquestração multi-agente
- Padrão de arquivo: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Último framework da Microsoft
- Disponível em Python e .NET
- Padrão de arquivo: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Requer assinatura Azure
- Recursos prontos para produção
- Padrão de arquivo: `*-azureaiagent.ipynb`

## Instruções de Teste

Este é um repositório educacional com código exemplo, e não código de produção com testes automatizados. Para verificar sua configuração e mudanças:

### Teste Manual

1. **Teste o ambiente Python:**
   ```bash
   python --version  # Deve ser 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Teste a execução dos notebooks:**
   ```bash
   # Converter notebook para script e executar (testa importações)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verifique as variáveis de ambiente:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Executando Notebooks Individualmente

Abra os notebooks no Jupyter e execute as células sequencialmente. Cada notebook é autocontido e inclui:
- Declarações de importação
- Carregamento de configuração
- Implementações de exemplo de agentes
- Resultados esperados em células markdown

## Estilo de Código

### Convenções Python

- **Versão Python**: 3.12+
- **Estilo de Código**: Siga as convenções padrão Python PEP 8
- **Notebooks**: Use células markdown claras para explicar conceitos
- **Imports**: Agrupe por biblioteca padrão, terceiros e locais

### Convenções de Jupyter Notebooks

- Inclua células markdown descritivas antes das células de código
- Adicione exemplos de saída nos notebooks para referência
- Use nomes de variáveis claros que correspondam aos conceitos da lição
- Mantenha a ordem de execução dos notebooks linear (célula 1 → 2 → 3...)

### Organização de Arquivos

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

## Build e Implantação

### Construindo a Documentação

Este repositório usa Markdown para documentação:
- Arquivos README.md em cada pasta de lição
- README.md principal na raiz do repositório
- Sistema automatizado de tradução via GitHub Actions

### Pipeline CI/CD

Localizado em `.github/workflows/`:

1. **co-op-translator.yml** - Tradução automática para mais de 50 idiomas
2. **welcome-issue.yml** - Recebe novos criadores de issues
3. **welcome-pr.yml** - Recebe novos contribuidores de pull requests

### Implantação

Este é um repositório educacional - sem processo de implantação. Usuários:
1. Fork ou clone o repositório
2. Execute notebooks localmente ou no GitHub Codespaces
3. Aprenda modificando e experimentando exemplos

## Diretrizes de Pull Request

### Antes de Enviar

1. **Teste suas mudanças:**
   - Execute os notebooks afetados completamente
   - Verifique se todas as células executam sem erros
   - Confira se as saídas estão adequadas

2. **Atualizações de documentação:**
   - Atualize README.md se adicionar novos conceitos
   - Adicione comentários nos notebooks para códigos complexos
   - Garanta que as células markdown expliquem o propósito

3. **Alterações de arquivos:**
   - Evite commitar arquivos `.env` (use `.env.example`)
   - Não commite diretórios `venv/` ou `__pycache__/`
   - Mantenha as saídas dos notebooks quando demonstrarem conceitos
   - Remova arquivos temporários e backups de notebooks (`*-backup.ipynb`)

### Formato do Título do PR

Use títulos descritivos:
- `[Lesson-XX] Adiciona novo exemplo para <conceito>`
- `[Fix] Corrige erro de digitação no README da lição-XX`
- `[Update] Melhora exemplo de código na lição-XX`
- `[Docs] Atualiza instruções de configuração`

### Verificações Necessárias

- Notebooks devem executar sem erros
- Arquivos README devem ser claros e precisos
- Siga padrões de código existentes no repositório
- Mantenha consistência com outras lições

## Notas Adicionais

### Armadilhas Comuns

1. **Incompatibilidade de versão Python:**
   - Use Python 3.12+ garantido
   - Alguns pacotes podem não funcionar em versões antigas
   - Use `python3 -m venv` para especificar a versão explicitamente

2. **Variáveis de ambiente:**
   - Sempre crie `.env` a partir de `.env.example`
   - Não commit o arquivo `.env` (está no `.gitignore`)
   - O token GitHub precisa de permissões adequadas

3. **Conflitos de pacotes:**
   - Use ambiente virtual novo
   - Instale a partir de `requirements.txt`, não pacotes individuais
   - Alguns notebooks podem requerer pacotes adicionais mencionados nas células markdown

4. **Serviços Azure:**
   - Serviços Azure AI requerem assinatura ativa
   - Algumas funcionalidades são específicas por região
   - Limitações do nível gratuito se aplicam aos Modelos GitHub

### Caminho de Aprendizado

Progressão recomendada pelas lições:
1. **00-course-setup** - Comece aqui para configuração do ambiente
2. **01-intro-to-ai-agents** - Entenda fundamentos de agentes de IA
3. **02-explore-agentic-frameworks** - Aprenda sobre diferentes frameworks
4. **03-agentic-design-patterns** - Padrões centrais de design
5. Continue sequencialmente pelas lições numeradas

### Seleção de Framework

Escolha o framework com base em seus objetivos:
- **Aprendizado/Prototipagem**: Semantic Kernel + Modelos GitHub (gratuito)
- **Sistemas multi-agente**: AutoGen
- **Últimas funcionalidades**: Microsoft Agent Framework (MAF)
- **Implantação em produção**: Azure AI Agent Service

### Obtendo Ajuda

- Participe do [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Revise os arquivos README das lições para orientações específicas
- Consulte o [README.md](./README.md) principal para visão geral do curso
- Veja [Course Setup](./00-course-setup/README.md) para instruções detalhadas de configuração

### Contribuindo

Este é um projeto educacional aberto. Contribuições são bem-vindas:
- Melhore exemplos de código
- Corrija erros de digitação ou bugs
- Adicione comentários esclarecedores
- Sugira novos tópicos para lições
- Traduza para idiomas adicionais

Veja [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) para necessidades atuais.

## Contexto Específico do Projeto

### Suporte Multilíngue

Este repositório usa sistema automatizado de tradução:
- Suporta mais de 50 idiomas
- Traduções em diretórios `/translations/<lang-code>/`
- Workflow GitHub Actions gerencia atualizações de tradução
- Arquivos fonte estão em inglês na raiz do repositório

### Estrutura da Lição

Cada lição segue um padrão consistente:
1. Miniatura de vídeo com link
2. Conteúdo escrito da lição (README.md)
3. Exemplos de código em múltiplos frameworks
4. Objetivos de aprendizagem e pré-requisitos
5. Recursos extras de aprendizado linkados

### Nomeação de Exemplos de Código

Formato: `<número-da-lição>-<nome-do-framework>.ipynb`
- `04-semantic-kernel.ipynb` - Lição 4, Semantic Kernel
- `07-autogen.ipynb` - Lição 7, AutoGen
- `14-python-agent-framework.ipynb` - Lição 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lição 14, MAF .NET

### Diretórios Especiais

- `translated_images/` - Imagens localizadas para traduções
- `images/` - Imagens originais para conteúdo em inglês
- `.devcontainer/` - Configuração do container de desenvolvimento VS Code
- `.github/` - Workflows e templates GitHub Actions

### Dependências

Principais pacotes do `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - framework AutoGen
- `semantic-kernel` - framework Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - serviços Azure AI
- `azure-search-documents` - integração Azure AI Search
- `chromadb` - banco de dados vetorial para exemplos RAG
- `chainlit` - framework UI para chat
- `browser_use` - automação de navegador para agentes
- `mcp[cli]` - suporte Model Context Protocol
- `mem0ai` - gerenciamento de memória para agentes

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autoritativa. Para informações críticas, recomenda-se a tradução profissional realizada por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->