# Utilização de Protocolos Agenticos (MCP, A2A e NLWeb)

[![Agentic Protocols](../../../translated_images/pt-PT/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Clique na imagem acima para ver o vídeo desta lição)_

À medida que o uso de agentes de IA cresce, também aumenta a necessidade de protocolos que garantam a padronização, segurança e apoiem a inovação aberta. Nesta lição, iremos cobrir 3 protocolos que procuram responder a esta necessidade - Model Context Protocol (MCP), Agent to Agent (A2A) e Natural Language Web (NLWeb).

## Introdução

Nesta lição, iremos abordar:

• Como o **MCP** permite que Agentes de IA acedam a ferramentas externas e dados para concluir tarefas do utilizador.

• Como o **A2A** permite a comunicação e colaboração entre diferentes agentes de IA.

• Como o **NLWeb** traz interfaces em linguagem natural a qualquer site, permitindo que Agentes de IA descubram e interajam com o conteúdo.

## Objetivos de Aprendizagem

• **Identificar** o propósito principal e os benefícios do MCP, A2A e NLWeb no contexto de agentes de IA.

• **Explicar** como cada protocolo facilita a comunicação e interação entre LLMs, ferramentas e outros agentes.

• **Reconhecer** os papéis distintos que cada protocolo desempenha na construção de sistemas agenticos complexos.

## Model Context Protocol

O **Model Context Protocol (MCP)** é um standard aberto que fornece uma forma padronizada para aplicações fornecerem contexto e ferramentas a LLMs. Isto permite um "adaptor universal" para diferentes fontes de dados e ferramentas às quais Agentes de IA podem ligar-se de forma consistente.

Vamos examinar os componentes do MCP, os benefícios comparados com o uso direto de API e um exemplo de como agentes de IA podem usar um servidor MCP.

### Componentes Principais do MCP

O MCP opera numa **arquitetura cliente-servidor** e os componentes principais são:

• **Hosts** são aplicações LLM (por exemplo, um editor de código como o VSCode) que iniciam as ligações a um Servidor MCP.

• **Clients** são componentes dentro da aplicação host que mantêm ligações um-a-um com servidores.

• **Servers** são programas leves que expõem capacidades específicas.

Incluídas no protocolo estão três primitivas principais que são as capacidades de um Servidor MCP:

• **Tools**: Estas são ações ou funções discretas que um agente de IA pode invocar para executar uma ação. Por exemplo, um serviço meteorológico pode expor uma ferramenta "obter tempo" ou um servidor de comércio eletrónico pode expor uma ferramenta "comprar produto". Os servidores MCP anunciam o nome, descrição e esquema de entrada/saída de cada ferramenta na sua lista de capacidades.

• **Resources**: Estes são dados ou documentos só de leitura que um servidor MCP pode fornecer, e os clientes podem recuperá-los conforme a necessidade. Exemplos incluem conteúdos de ficheiros, registos de bases de dados ou ficheiros de log. Os recursos podem ser texto (como código ou JSON) ou binários (como imagens ou PDFs).

• **Prompts**: São templates predefinidos que fornecem prompts sugeridos, permitindo workflows mais complexos.

### Benefícios do MCP

O MCP oferece vantagens significativas para Agentes de IA:

• **Descoberta Dinâmica de Ferramentas**: Os agentes podem receber dinamicamente uma lista de ferramentas disponíveis de um servidor, juntamente com descrições das suas funções. Isto contrasta com APIs tradicionais, que frequentemente requerem codificação estática para integrações, implicando que qualquer mudança na API requer atualizações de código. O MCP oferece uma abordagem de "integrar uma vez", levando a maior adaptabilidade.

• **Interoperabilidade Entre LLMs**: O MCP funciona com diferentes LLMs, proporcionando flexibilidade para trocar modelos principais para melhor desempenho.

• **Segurança Padronizada**: O MCP inclui um método padrão de autenticação, melhorando a escalabilidade ao adicionar acesso a servidores MCP adicionais. Isto é mais simples do que gerir diferentes chaves e tipos de autenticação para várias APIs tradicionais.

### Exemplo de MCP

![MCP Diagram](../../../translated_images/pt-PT/mcp-diagram.e4ca1cbd551444a1.webp)

Imagine que um utilizador quer reservar um voo usando um assistente de IA alimentado por MCP.

1. **Ligação**: O assistente de IA (o cliente MCP) liga-se a um servidor MCP fornecido por uma companhia aérea.

2. **Descoberta de Ferramentas**: O cliente pergunta ao servidor MCP da companhia aérea, "Que ferramentas têm disponíveis?" O servidor responde com ferramentas como "pesquisar voos" e "reservar voos".

3. **Invocação da Ferramenta**: O utilizador pede então ao assistente de IA, "Por favor, pesquisa um voo de Portland para Honolulu." O assistente de IA, usando o seu LLM, identifica que precisa invocar a ferramenta "pesquisar voos" e passa os parâmetros relevantes (origem, destino) ao servidor MCP.

4. **Execução e Resposta**: O servidor MCP, atuando como um invólucro, faz a chamada real à API interna da companhia aérea. Depois recebe a informação do voo (por exemplo, dados JSON) e devolve-a ao assistente de IA.

5. **Interação Adicional**: O assistente de IA apresenta as opções de voo. Quando o utilizador seleciona um voo, o assistente pode invocar a ferramenta "reservar voo" no mesmo servidor MCP, completando a reserva.

## Protocolo Agent-to-Agent (A2A)

Enquanto o MCP foca em ligar LLMs a ferramentas, o **protocolo Agent-to-Agent (A2A)** vai um passo além ao permitir comunicação e colaboração entre diferentes agentes de IA. O A2A conecta agentes de IA em diferentes organizações, ambientes e tecnologias para completar uma tarefa compartilhada.

Analisaremos os componentes e benefícios do A2A, assim como um exemplo de aplicação na nossa aplicação de viagens.

### Componentes Principais do A2A

O A2A foca em permitir comunicação entre agentes e fazê-los trabalhar juntos para completar uma subtarefa do utilizador. Cada componente do protocolo contribui para isto:

#### Agent Card

Tal como um servidor MCP partilha uma lista de ferramentas, uma Agent Card tem:
- O Nome do Agente.
- Uma **descrição das tarefas gerais** que executa.
- Uma **lista de competências específicas** com descrições para ajudar outros agentes (ou até utilizadores humanos) a entender quando e porquê querer invocar esse agente.
- O **URL do Endpoint atual** do agente.
- A **versão** e as **capacidades** do agente, como respostas em streaming e notificações push.

#### Agent Executor

O Agent Executor é responsável por **passar o contexto do chat do utilizador para o agente remoto**, o agente remoto precisa disto para entender a tarefa a realizar. Num servidor A2A, um agente usa o seu próprio Large Language Model (LLM) para analisar pedidos recebidos e executar tarefas usando as suas próprias ferramentas internas.

#### Artifact

Uma vez que um agente remoto completa a tarefa solicitada, o seu produto de trabalho é criado como um artifact. Um artifact **contém o resultado do trabalho do agente**, uma **descrição do que foi concluído**, e o **contexto texto** que é enviado através do protocolo. Depois de o artifact ser enviado, a ligação com o agente remoto é fechada até ser necessária novamente.

#### Event Queue

Este componente é usado para **gerir atualizações e passar mensagens**. É particularmente importante em produção para sistemas agenticos evitar que a ligação entre agentes seja fechada antes da tarefa estar completa, especialmente quando o tempo para concluir tarefas pode ser longo.

### Benefícios do A2A

• **Colaboração Melhorada**: Permite que agentes de diferentes fornecedores e plataformas interajam, partilhem contexto e trabalhem juntos, facilitando automação fluida entre sistemas tradicionalmente desconectados.

• **Flexibilidade na Seleção do Modelo**: Cada agente A2A pode decidir qual LLM usar para atender aos seus pedidos, permitindo modelos otimizados ou aprimorados por agente, diferente de uma única ligação LLM em alguns cenários MCP.

• **Autenticação Integrada**: A autenticação está integrada diretamente no protocolo A2A, providenciando um quadro de segurança robusto para interações entre agentes.

### Exemplo de A2A

![A2A Diagram](../../../translated_images/pt-PT/A2A-Diagram.8666928d648acc26.webp)

Vamos expandir o nosso cenário de reserva de viagens, mas desta vez usando A2A.

1. **Pedido do Utilizador a Múltiplos Agentes**: Um utilizador interage com um cliente/agente A2A chamado "Agente de Viagens", talvez dizendo, "Por favor, reserva toda a viagem para Honolulu para a próxima semana, incluindo voos, hotel e aluguer de carro".

2. **Orquestração pelo Agente de Viagens**: O Agente de Viagens recebe este pedido complexo. Usa o seu LLM para raciocinar sobre a tarefa e determinar que precisa interagir com outros agentes especializados.

3. **Comunicação Entre Agentes**: O Agente de Viagens usa o protocolo A2A para conectar-se a agentes downstream, como um "Agente de Companhia Aérea", "Agente de Hotel" e "Agente de Aluguer de Carro", criados por diferentes empresas.

4. **Execução Delegada da Tarefa**: O Agente de Viagens envia tarefas específicas a estes agentes especializados (por exemplo, "Encontrar voos para Honolulu," "Reservar um hotel," "Alugar um carro"). Cada um desses agentes especializados, executando o seu próprio LLM e utilizando as suas próprias ferramentas (que podem ser servidores MCP), realiza a sua parte da reserva.

5. **Resposta Consolidada**: Uma vez que todos os agentes downstream completam as suas tarefas, o Agente de Viagens compila os resultados (detalhes do voo, confirmação do hotel, reserva do carro) e envia uma resposta completa, em estilo chat, de volta ao utilizador.

## Natural Language Web (NLWeb)

Os websites têm sido há muito tempo a principal forma para utilizadores acederem a informação e dados na internet.

Vamos ver os diferentes componentes do NLWeb, os benefícios do NLWeb e um exemplo de como nosso NLWeb funciona olhando para a nossa aplicação de viagens.

### Componentes do NLWeb

- **Aplicação NLWeb (Código do Serviço Core)**: O sistema que processa perguntas em linguagem natural. Liga as diferentes partes da plataforma para criar respostas. Pode ser visto como o **motor que alimenta as funcionalidades de linguagem natural** de um site.

- **Protocolo NLWeb**: Este é um **conjunto básico de regras para interação em linguagem natural** com um site. Envia respostas em formato JSON (frequentemente usando Schema.org). O seu objetivo é criar uma base simples para a “Web de IA”, da mesma forma que o HTML permitiu partilhar documentos online.

- **Servidor MCP (Endpoint do Model Context Protocol)**: Cada configuração NLWeb também funciona como um **servidor MCP**. Isto significa que pode **partilhar ferramentas (como o método "ask") e dados** com outros sistemas de IA. Na prática, isto torna o conteúdo e as capacidades do website utilizáveis por agentes de IA, permitindo que o site faça parte do ecossistema mais amplo de agentes.

- **Modelos de Embedding**: Estes modelos são usados para **converter o conteúdo do site em representações numéricas chamadas vetores** (embeddings). Estes vetores capturam significado de uma forma que os computadores podem comparar e pesquisar. São armazenados numa base de dados especial e os utilizadores podem escolher qual modelo de embedding querem usar.

- **Base de Dados Vetorial (Mecanismo de Recuperação)**: Esta base de dados **armazena os embeddings do conteúdo do website**. Quando alguém faz uma pergunta, o NLWeb verifica a base de dados vetorial para encontrar rapidamente a informação mais relevante. Fornece uma lista rápida de respostas possíveis, ordenadas por similaridade. O NLWeb funciona com diferentes sistemas de armazenamento vetorial, como Qdrant, Snowflake, Milvus, Azure AI Search e Elasticsearch.

### NLWeb por Exemplo

![NLWeb](../../../translated_images/pt-PT/nlweb-diagram.c1e2390b310e5fe4.webp)

Considere novamente o nosso website de reserva de viagens, mas agora alimentado por NLWeb.

1. **Ingestão de Dados**: Os catálogos de produtos existentes do website de viagens (por exemplo, listagens de voos, descrições de hotéis, pacotes turísticos) são formatados usando Schema.org ou carregados via feeds RSS. As ferramentas do NLWeb ingerem estes dados estruturados, criam embeddings e armazenam-nos numa base de dados vetorial local ou remota.

2. **Consulta em Linguagem Natural (Humano)**: Um utilizador visita o site e, em vez de navegar por menus, escreve numa interface de chat: "Encontra um hotel familiar em Honolulu com piscina para a próxima semana".

3. **Processamento NLWeb**: A aplicação NLWeb recebe esta consulta. Envia a consulta para um LLM para interpretação e simultaneamente pesquisa na sua base de dados vetorial listagens de hotéis relevantes.

4. **Resultados Precisos**: O LLM ajuda a interpretar os resultados da pesquisa na base de dados, identificando as melhores correspondências baseado nos critérios "familiar," "piscina" e "Honolulu", e depois formata uma resposta em linguagem natural. O importante é que a resposta refere-se a hotéis reais do catálogo do site, evitando informação inventada.

5. **Interação com Agente IA**: Como o NLWeb funciona como um servidor MCP, um agente externo de viagens de IA também pode ligar-se a esta instância NLWeb do site. O agente IA pode então usar o método `ask` do MCP para consultar diretamente o site: `ask("Existem restaurantes vegan-friendly na área de Honolulu recomendados pelo hotel?")`. A instância NLWeb processaria isto, aproveitando a sua base de dados de informação sobre restaurantes (se carregada), e devolveria uma resposta JSON estruturada.

### Quer Saber Mais sobre MCP/A2A/NLWeb?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para conhecer outros aprendizes, participar em horas de atendimento e obter respostas às suas perguntas sobre Agentes de IA.

## Recursos

- [MCP para Iniciantes](https://aka.ms/mcp-for-beginners)  
- [Documentação MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repositório NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Guias Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos por garantir a precisão, por favor tenha em consideração que traduções automáticas podem conter erros ou imprecisões. O documento original na sua língua nativa deverá ser considerado a fonte autorizada. Para informações críticas, recomenda-se a tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações erradas decorrentes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->