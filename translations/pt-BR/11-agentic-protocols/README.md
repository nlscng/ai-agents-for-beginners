# Usando Protocolos de Agentes (MCP, A2A e NLWeb)

[![Protocolos de Agentes](../../../translated_images/pt-BR/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Clique na imagem acima para ver o vídeo desta aula)_

À medida que o uso de agentes de IA cresce, também cresce a necessidade de protocolos que garantam padronização, segurança e fomentem a inovação aberta. Nesta lição, abordaremos 3 protocolos que buscam atender a essa necessidade - Model Context Protocol (MCP), Agent to Agent (A2A) e Natural Language Web (NLWeb).

## Introdução

Nesta lição, abordaremos:

• Como **MCP** permite que Agentes de IA acessem ferramentas e dados externos para concluir tarefas do usuário.

• Como **A2A** possibilita comunicação e colaboração entre diferentes agentes de IA.

• Como **NLWeb** traz interfaces em linguagem natural para qualquer site, permitindo que Agentes de IA descubram e interajam com o conteúdo.

## Objetivos de Aprendizagem

• **Identificar** o propósito central e os benefícios do MCP, A2A e NLWeb no contexto de agentes de IA.

• **Explicar** como cada protocolo facilita a comunicação e interação entre LLMs, ferramentas e outros agentes.

• **Reconhecer** os papéis distintos que cada protocolo desempenha na construção de sistemas agentivos complexos.

## Model Context Protocol

O **Model Context Protocol (MCP)** é um padrão aberto que fornece uma maneira padronizada para aplicações fornecerem contexto e ferramentas para LLMs. Isso possibilita um "adaptador universal" para diferentes fontes de dados e ferramentas às quais Agentes de IA podem se conectar de maneira consistente.

Vamos ver os componentes do MCP, os benefícios em comparação com o uso direto de APIs e um exemplo de como agentes de IA podem usar um servidor MCP.

### Componentes Principais do MCP

O MCP opera em uma **arquitetura cliente-servidor** e os componentes principais são:

• **Hosts** são aplicações LLM (por exemplo um editor de código como o VSCode) que iniciam as conexões com um Servidor MCP.

• **Clients** são componentes dentro da aplicação host que mantêm conexões um-a-um com servidores.

• **Servers** são programas leves que expõem capacidades específicas.

Incluídos no protocolo estão três primitivos centrais, que são as capacidades de um Servidor MCP:

• **Ferramentas**: São ações ou funções discretas que um agente de IA pode chamar para executar uma ação. Por exemplo, um serviço meteorológico pode expor uma ferramenta "obter clima", ou um servidor de e-commerce pode expor uma ferramenta "comprar produto". Servidores MCP anunciam o nome de cada ferramenta, descrição e o esquema de entrada/saída em sua lista de capacidades.

• **Recursos**: Itens de dados ou documentos somente leitura que um servidor MCP pode fornecer, e que os clientes podem recuperar sob demanda. Exemplos incluem conteúdos de arquivos, registros de banco de dados ou arquivos de log. Recursos podem ser texto (como código ou JSON) ou binário (como imagens ou PDFs).

• **Prompts**: São modelos predefinidos que fornecem sugestões de prompts, permitindo fluxos de trabalho mais complexos.

### Benefícios do MCP

O MCP oferece vantagens significativas para Agentes de IA:

• **Descoberta Dinâmica de Ferramentas**: Agentes podem receber dinamicamente uma lista de ferramentas disponíveis de um servidor junto com descrições do que elas fazem. Isso contrasta com APIs tradicionais, que frequentemente exigem codificação estática para integrações, significando que qualquer alteração na API exige atualizações de código. O MCP oferece uma abordagem de "integre uma vez", levando a maior adaptabilidade.

• **Interoperabilidade entre LLMs**: O MCP funciona com diferentes LLMs, fornecendo flexibilidade para alternar modelos centrais para avaliar melhor desempenho.

• **Segurança Padronizada**: O MCP inclui um método padrão de autenticação, melhorando a escalabilidade ao adicionar acesso a servidores MCP adicionais. Isso é mais simples do que gerenciar chaves e tipos de autenticação diferentes para várias APIs tradicionais.

### Exemplo do MCP

![Diagrama MCP](../../../translated_images/pt-BR/mcp-diagram.e4ca1cbd551444a1.webp)

Imagine que um usuário quer reservar um voo usando um assistente de IA com suporte do MCP.

1. **Conexão**: O assistente de IA (o cliente MCP) conecta-se a um servidor MCP fornecido por uma companhia aérea.

2. **Descoberta de Ferramentas**: O cliente pergunta ao servidor MCP da companhia aérea: "Quais ferramentas vocês têm disponíveis?" O servidor responde com ferramentas como "buscar voos" e "reservar voos".

3. **Invocação da Ferramenta**: Você então pede ao assistente de IA: "Por favor, busque um voo de Portland para Honolulu." O assistente de IA, usando seu LLM, identifica que precisa chamar a ferramenta "buscar voos" e passa os parâmetros relevantes (origem, destino) ao servidor MCP.

4. **Execução e Resposta**: O servidor MCP, atuando como um wrapper, faz a chamada real à API interna de reservas da companhia aérea. Recebe as informações dos voos (por exemplo, dados JSON) e as envia de volta ao assistente de IA.

5. **Interação Posterior**: O assistente de IA apresenta as opções de voo. Uma vez que você seleciona um voo, o assistente pode invocar a ferramenta "reservar voo" no mesmo servidor MCP, completando a reserva.

## Protocolo Agente-para-Agente (A2A)

Enquanto o MCP foca em conectar LLMs a ferramentas, o **protocolo Agent-to-Agent (A2A)** dá um passo adiante ao possibilitar comunicação e colaboração entre diferentes agentes de IA. O A2A conecta agentes de IA entre diferentes organizações, ambientes e pilhas tecnológicas para completar uma tarefa compartilhada.

Examinaremos os componentes e benefícios do A2A, juntamente com um exemplo de como ele poderia ser aplicado em nossa aplicação de viagens.

### Componentes Centrais do A2A

O A2A foca em habilitar a comunicação entre agentes e fazer com que trabalhem juntos para completar uma subtarefa do usuário. Cada componente do protocolo contribui para isso:

#### Ficha do Agente

Semelhante a como um servidor MCP compartilha uma lista de ferramentas, uma Ficha do Agente tem:
- O Nome do Agente .
- Uma **descrição das tarefas gerais** que ele realiza.
- Uma **lista de habilidades específicas** com descrições para ajudar outros agentes (ou mesmo usuários humanos) a entender quando e por que chamariam esse agente.
- A **URL de Endpoint atual** do agente
- A **versão** e as **capacidades** do agente como respostas em streaming e notificações push.

#### Executor do Agente

O Executor do Agente é responsável por **passar o contexto do chat do usuário para o agente remoto**, o agente remoto precisa disso para entender a tarefa que precisa ser concluída. Em um servidor A2A, um agente usa seu próprio Large Language Model (LLM) para analisar solicitações recebidas e executar tarefas usando suas próprias ferramentas internas.

#### Artefato

Uma vez que um agente remoto tenha concluído a tarefa solicitada, seu produto de trabalho é criado como um artefato. Um artefato **contém o resultado do trabalho do agente**, uma **descrição do que foi concluído**, e o **contexto em texto** que é enviado através do protocolo. Após o envio do artefato, a conexão com o agente remoto é encerrada até que seja necessária novamente.

#### Fila de Eventos

Este componente é usado para **lidar com atualizações e passar mensagens**. É particularmente importante em produção para sistemas agentivos para evitar que a conexão entre agentes seja fechada antes que uma tarefa seja concluída, especialmente quando os tempos de conclusão de tarefas podem ser mais longos.

### Benefícios do A2A

• **Colaboração Aprimorada**: Permite que agentes de diferentes fornecedores e plataformas interajam, compartilhem contexto e trabalhem juntos, facilitando automação contínua entre sistemas tradicionalmente desconectados.

• **Flexibilidade na Seleção de Modelos**: Cada agente A2A pode decidir qual LLM usa para atender suas solicitações, permitindo modelos otimizados ou afinados por agente, ao contrário de uma única conexão LLM em alguns cenários MCP.

• **Autenticação Integrada**: A autenticação é integrada diretamente no protocolo A2A, fornecendo uma estrutura de segurança robusta para interações entre agentes.

### Exemplo do A2A

![Diagrama A2A](../../../translated_images/pt-BR/A2A-Diagram.8666928d648acc26.webp)

Vamos expandir nosso cenário de reserva de viagens, mas desta vez usando A2A.

1. **Solicitação do Usuário ao Multi-Agente**: Um usuário interage com um agente/cliente A2A "Agente de Viagens", talvez dizendo: "Por favor, reserve uma viagem completa para Honolulu na próxima semana, incluindo voos, hotel e aluguel de carro".

2. **Orquestração pelo Agente de Viagens**: O Agente de Viagens recebe essa solicitação complexa. Ele usa seu LLM para raciocinar sobre a tarefa e determinar que precisa interagir com outros agentes especializados.

3. **Comunicação entre Agentes**: O Agente de Viagens então usa o protocolo A2A para conectar-se a agentes posteriores, como um "Agente da Companhia Aérea", um "Agente de Hotel" e um "Agente de Locadora de Carros" criados por empresas diferentes.

4. **Execução Delegada de Tarefas**: O Agente de Viagens envia tarefas específicas para esses agentes especializados (por exemplo, "Encontre voos para Honolulu", "Reserve um hotel", "Alugue um carro"). Cada um desses agentes especializados, executando seus próprios LLMs e utilizando suas próprias ferramentas (que poderiam ser servidores MCP), realiza sua parte específica da reserva.

5. **Resposta Consolidada**: Uma vez que todos os agentes posteriores concluam suas tarefas, o Agente de Viagens compila os resultados (detalhes do voo, confirmação do hotel, reserva do carro) e envia uma resposta abrangente em estilo de chat de volta ao usuário.

## Natural Language Web (NLWeb)

Sites há muito são a principal forma dos usuários acessarem informações e dados pela internet.

Vamos ver os diferentes componentes do NLWeb, os benefícios do NLWeb e um exemplo de como nosso NLWeb funciona observando nossa aplicação de viagens.

### Componentes do NLWeb

- **Aplicação NLWeb (Código de Serviço Central)**: O sistema que processa perguntas em linguagem natural. Conecta as diferentes partes da plataforma para criar respostas. Você pode pensar nele como o **motor que alimenta os recursos em linguagem natural** de um site.

- **Protocolo NLWeb**: Este é um **conjunto básico de regras para interação em linguagem natural** com um site. Retorna respostas em formato JSON (frequentemente usando Schema.org). Seu propósito é criar uma base simples para a "Web de IA", da mesma forma que o HTML tornou possível compartilhar documentos online.

- **Servidor MCP (Endpoint do Model Context Protocol)**: Cada configuração do NLWeb também funciona como um **servidor MCP**. Isso significa que pode **compartilhar ferramentas (como um método “ask”) e dados** com outros sistemas de IA. Na prática, isso torna o conteúdo e as habilidades do site utilizáveis por agentes de IA, permitindo que o site faça parte do ecossistema mais amplo de agentes.

- **Modelos de Embedding**: Esses modelos são usados para **converter o conteúdo do site em representações numéricas chamadas vetores** (embeddings). Esses vetores capturam o significado de uma forma que computadores podem comparar e buscar. Eles são armazenados em um banco de dados especial, e os usuários podem escolher qual modelo de embedding desejam usar.

- **Banco de Dados Vetorial (Mecanismo de Recuperação)**: Este banco de dados **armazenas os embeddings do conteúdo do site**. Quando alguém faz uma pergunta, o NLWeb verifica o banco de dados vetorial para encontrar rapidamente as informações mais relevantes. Ele fornece uma lista rápida de possíveis respostas, ranqueadas por similaridade. NLWeb funciona com diferentes sistemas de armazenamento vetorial como Qdrant, Snowflake, Milvus, Azure AI Search e Elasticsearch.

### NLWeb por Exemplo

![NLWeb](../../../translated_images/pt-BR/nlweb-diagram.c1e2390b310e5fe4.webp)

Considere novamente nosso site de reservas de viagem, mas desta vez, ele é alimentado pelo NLWeb.

1. **Ingestão de Dados**: Os catálogos de produtos existentes do site de viagens (por exemplo, listagens de voos, descrições de hotéis, pacotes de turismo) são formatados usando Schema.org ou carregados via feeds RSS. As ferramentas do NLWeb ingerem esses dados estruturados, criam embeddings e os armazenam em um banco de dados vetorial local ou remoto.

2. **Consulta em Linguagem Natural (Humano)**: Um usuário visita o site e, em vez de navegar por menus, digita em uma interface de chat: "Encontre um hotel em Honolulu apropriado para família com piscina para a próxima semana".

3. **Processamento pelo NLWeb**: A aplicação NLWeb recebe essa consulta. Ela envia a consulta para um LLM para compreensão e simultaneamente pesquisa seu banco de dados vetorial por listagens de hotéis relevantes.

4. **Resultados Precisos**: O LLM ajuda a interpretar os resultados da busca no banco de dados, identifica as melhores correspondências com base nos critérios "apto para família", "piscina" e "Honolulu", e então formata uma resposta em linguagem natural. Crucialmente, a resposta se refere a hotéis reais do catálogo do site, evitando informações inventadas.

5. **Interação com Agente de IA**: Como o NLWeb serve como um servidor MCP, um agente de viagens externo também poderia se conectar à instância NLWeb deste site. O agente de IA poderia então usar o método `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. A instância NLWeb processaria isso, aproveitando seu banco de dados de informações sobre restaurantes (se carregado), e retornaria uma resposta JSON estruturada.

### Tem Mais Perguntas sobre MCP/A2A/NLWeb?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar de horários de atendimento e tirar suas dúvidas sobre Agentes de IA.

## Recursos

- [MCP para Iniciantes](https://aka.ms/mcp-for-beginners)  
- [Documentação do MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repositório NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Guias do Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Isenção de responsabilidade**:
Este documento foi traduzido usando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos pela precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original, em seu idioma nativo, deve ser considerado a versão autorizada. Para informações críticas, recomenda-se tradução profissional realizada por um tradutor humano. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->