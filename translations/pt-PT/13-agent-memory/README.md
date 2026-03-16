# Memória para Agentes de IA 
[![Agent Memory](../../../translated_images/pt-PT/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Ao discutir os benefícios únicos de criar Agentes de IA, dois aspetos são principalmente debatidos: a capacidade de chamar ferramentas para completar tarefas e a capacidade de melhorar ao longo do tempo. A memória está na base da criação de um agente autoaperfeiçoável que pode criar melhores experiências para os nossos utilizadores.

Nesta lição, iremos ver o que é a memória para Agentes de IA e como podemos geri-la e utilizá-la para benefício das nossas aplicações.

## Introdução

Esta lição irá cobrir:

• **Compreender a Memória dos Agentes de IA**: O que é a memória e porque é essencial para os agentes.

• **Implementação e Armazenamento da Memória**: Métodos práticos para adicionar capacidades de memória aos seus agentes de IA, focando-se na memória de curto prazo e de longo prazo.

• **Tornar os Agentes de IA Autoaperfeiçoáveis**: Como a memória permite aos agentes aprender com interações passadas e melhorar ao longo do tempo.

## Implementações Disponíveis

Esta lição inclui dois tutoriais completos em notebooks:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementa memória usando Mem0 e Azure AI Search com o framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementa memória estruturada usando Cognee, construindo automaticamente um grafo de conhecimento suportado por embeddings, visualizando o grafo e recuperação inteligente

## Objetivos de Aprendizagem

Depois de completar esta lição, saberá como:

• **Diferenciar entre vários tipos de memória dos agentes de IA**, incluindo memória operacional, de curto prazo e de longo prazo, assim como formas especializadas como memória de persona e memórias episódicas.

• **Implementar e gerir memória de curto e longo prazo para agentes de IA** usando o framework Semantic Kernel, aproveitando ferramentas como Mem0, Cognee, memória em Whiteboard, e integrando com Azure AI Search.

• **Compreender os princípios por detrás dos agentes de IA autoaperfeiçoáveis** e como sistemas robustos de gestão de memória contribuem para a aprendizagem contínua e adaptação.

## Compreender a Memória dos Agentes de IA

Na sua essência, **a memória para agentes de IA refere-se aos mecanismos que lhes permitem reter e recordar informação**. Esta informação pode ser detalhes específicos sobre uma conversa, preferências do utilizador, ações passadas ou até padrões aprendidos.

Sem memória, as aplicações de IA são frequentemente sem estado, o que significa que cada interação começa do zero. Isto conduz a uma experiência de utilizador repetitiva e frustrante onde o agente "esquece" o contexto ou preferências anteriores.

### Porque é a Memória Importante?

A inteligência de um agente está profundamente ligada à sua capacidade de recordar e utilizar informação passada. A memória permite que os agentes sejam:

• **Reflexivos**: Aprendendo com ações e resultados anteriores.

• **Interativos**: Mantendo o contexto ao longo de uma conversa em curso.

• **Proativos e Reativos**: Antecipando necessidades ou respondendo adequadamente com base em dados históricos.

• **Autónomos**: Operando de forma mais independente ao recorrer ao conhecimento armazenado.

O objetivo de implementar memória é tornar os agentes mais **fiáveis e capazes**.

### Tipos de Memória

#### Memória Operacional

Considere isto como uma folha de rascunho que um agente usa durante uma tarefa ou processo de pensamento único e contínuo. Esta memória contém a informação imediata necessária para calcular o próximo passo.

Para agentes de IA, a memória operacional captura muitas vezes a informação mais relevante de uma conversa, mesmo que o histórico completo do chat seja extenso ou truncado. Foca-se em extrair elementos-chave como requisitos, propostas, decisões e ações.

**Exemplo de Memória Operacional**

Numa agente de reserva de viagens, a memória operacional pode captar o pedido atual do utilizador, como "Quero reservar uma viagem para Paris". Este requisito específico está presente no contexto imediato do agente para orientar a interação atual.

#### Memória de Curto Prazo

Este tipo de memória retém informação durante a duração de uma única conversa ou sessão. É o contexto do chat atual, permitindo que o agente se refira a turnos anteriores do diálogo.

**Exemplo de Memória de Curto Prazo**

Se um utilizador pergunta, "Quanto custaria um voo para Paris?" e depois segue com "E quanto custa a acomodação lá?", a memória de curto prazo assegura que o agente sabe que "lá" se refere a "Paris" dentro da mesma conversa.

#### Memória de Longo Prazo

Esta é a informação que persiste ao longo de múltiplas conversas ou sessões. Permite aos agentes lembrar preferências do utilizador, interações históricas ou conhecimentos gerais ao longo de períodos prolongados. Isto é importante para personalização.

**Exemplo de Memória de Longo Prazo**

Uma memória de longo prazo pode armazenar que "O Ben gosta de esqui e atividades ao ar livre, aprecia café com vista para a montanha e quer evitar pistas de esqui avançadas devido a uma lesão anterior". Esta informação, aprendida em interações anteriores, influencia recomendações em futuras sessões de planeamento de viagens, tornando-as altamente personalizadas.

#### Memória de Persona

Este tipo de memória especializada ajuda um agente a desenvolver uma "personalidade" ou "persona" consistente. Permite ao agente lembrar detalhes sobre si próprio ou o seu papel pretendido, tornando as interações mais fluidas e focadas.

**Exemplo de Memória de Persona**

Se o agente de viagens for desenhado para ser um "planeador de esqui especialista", a memória de persona pode reforçar este papel, influenciando as suas respostas para alinhar-se com o tom e conhecimento de um especialista.

#### Memória de Fluxo de Trabalho/Episódica

Esta memória armazena a sequência de passos que um agente toma durante uma tarefa complexa, incluindo sucessos e falhas. É como lembrar "episódios" específicos ou experiências passadas para aprender com eles.

**Exemplo de Memória Episódica**

Se o agente tentou reservar um voo específico mas falhou devido à indisponibilidade, a memória episódica poderia registar essa falha, permitindo que o agente tente voos alternativos ou informe o utilizador sobre o problema de forma mais informada numa tentativa subsequente.

#### Memória de Entidade

Isto envolve extrair e lembrar entidades específicas (como pessoas, locais ou coisas) e eventos de conversas. Permite ao agente construir um entendimento estruturado dos elementos-chave discutidos.

**Exemplo de Memória de Entidade**

Numa conversa sobre uma viagem passada, o agente pode extrair "Paris", "Torre Eiffel" e "jantar no restaurante Le Chat Noir" como entidades. Numa interação futura, o agente poderia recordar "Le Chat Noir" e oferecer fazer uma nova reserva lá.

#### RAG Estruturado (Retrieval Augmented Generation)

Embora RAG seja uma técnica mais ampla, o "RAG Estruturado" é destacado como uma tecnologia de memória poderosa. Extrai informação densa e estruturada de várias fontes (conversas, e-mails, imagens) e usa-a para melhorar a precisão, a recordação e a velocidade das respostas. Ao contrário do RAG clássico que se baseia apenas na similaridade semântica, o RAG Estruturado trabalha com a estrutura inerente da informação.

**Exemplo de RAG Estruturado**

Em vez de apenas corresponder palavras-chave, o RAG Estruturado poderia analisar detalhes de voo (destino, data, hora, companhia aérea) de um e-mail e armazená-los de forma estruturada. Isto permite consultas precisas como "Qual o voo que reservei para Paris na terça-feira?"

## Implementar e Armazenar Memória

Implementar memória para agentes de IA envolve um processo sistemático de **gestão de memória**, que inclui gerar, armazenar, recuperar, integrar, atualizar e até "esquecer" (ou eliminar) informação. A recuperação é um aspeto particularmente crucial.

### Ferramentas Especializadas de Memória

#### Mem0

Uma forma de armazenar e gerir a memória dos agentes é usar ferramentas especializadas como o Mem0. O Mem0 funciona como uma camada persistente de memória, permitindo que os agentes recordem interações relevantes, armazenem preferências do utilizador e contexto factual, e aprendam com sucessos e falhas ao longo do tempo. A ideia aqui é que agentes sem estado se tornam agentes com estado.

Funciona através de uma **pipeline de memória em duas fases: extração e atualização**. Primeiro, as mensagens adicionadas a um tópico do agente são enviadas ao serviço Mem0, que utiliza um Modelo de Linguagem Grande (LLM) para resumir o histórico da conversa e extrair novas memórias. Subsequentemente, uma fase de atualização conduzida por um LLM determina se deve adicionar, modificar ou eliminar essas memórias, armazenando-as numa base de dados híbrida que pode incluir bases de dados vetoriais, de grafos e de chave-valor. Este sistema suporta também vários tipos de memória e pode incorporar memória em grafos para gerir relações entre entidades.

#### Cognee

Outra abordagem poderosa é usar o **Cognee**, uma memória semântica open-source para agentes de IA que transforma dados estruturados e não estruturados em grafos de conhecimento consultáveis suportados por embeddings. O Cognee fornece uma **arquitetura de armazenamento dual** que combina pesquisa por similaridade vetorial com relações em grafos, permitindo aos agentes entender não só que informação é similar, mas como os conceitos se relacionam entre si.

Destaca-se pela **recuperação híbrida** que combina similaridade vetorial, estrutura de grafos e raciocínio LLM – desde pesquisa de fragmentos crus até resposta a perguntas consciente de grafos. O sistema mantém uma **memória viva** que evolui e cresce enquanto permanece consultável como um grafo conectado, suportando tanto o contexto de sessão de curto prazo como a memória persistente de longo prazo.

O tutorial em notebook do Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstra a construção desta camada unificada de memória, com exemplos práticos de ingestão de várias fontes de dados, visualização do grafo de conhecimento e consulta com diferentes estratégias de busca adaptadas às necessidades específicas dos agentes.

### Armazenar Memória com RAG

Para além de ferramentas especializadas de memória como o Mem0, pode aproveitar serviços de busca robustos como o **Azure AI Search como backend para armazenar e recuperar memórias**, especialmente para RAG estruturado.

Isto permite fundamentar as respostas do seu agente nos seus próprios dados, garantindo respostas mais relevantes e precisas. O Azure AI Search pode ser usado para armazenar memórias de viagens específicas do utilizador, catálogos de produtos, ou qualquer outro conhecimento específico de domínio.

O Azure AI Search suporta capacidades como o **RAG Estruturado**, que se destaca na extração e recuperação de informação densa e estruturada de grandes conjuntos de dados como históricos de conversas, e-mails, ou mesmo imagens. Isto oferece "precisão e recordação super-humanas" comparado com abordagens tradicionais de fragmentação de texto e embeddings.

## Tornar os Agentes de IA Autoaperfeiçoáveis

Um padrão comum para agentes autoaperfeiçoáveis envolve introduzir um **"agente de conhecimento"**. Este agente separado observa a conversa principal entre o utilizador e o agente primário. O seu papel é:

1. **Identificar informação valiosa**: Determinar se alguma parte da conversa vale a pena ser guardada como conhecimento geral ou preferência específica do utilizador.

2. **Extrair e resumir**: Destilar o aprendizado essencial ou preferência da conversa.

3. **Armazenar numa base de conhecimento**: Persistir esta informação extraída, muitas vezes numa base de dados vetorial, para que possa ser recuperada mais tarde.

4. **Aumentar consultas futuras**: Quando o utilizador inicia uma nova consulta, o agente de conhecimento recupera a informação armazenada relevante e anexa-a ao prompt do utilizador, fornecendo contexto crucial ao agente primário (semelhante ao RAG).

### Otimizações para Memória

• **Gestão da Latência**: Para evitar atrasos nas interações dos utilizadores, um modelo mais barato e rápido pode ser usado inicialmente para verificar rapidamente se a informação vale a pena guardar ou recuperar, somente invocando o processo mais complexo de extração/recuperação quando necessário.

• **Manutenção da Base de Conhecimento**: Para uma base de conhecimento em crescimento, a informação menos utilizada pode ser movida para "armazenamento frio" para gerir custos.

## Tem Mais Perguntas Sobre Memória de Agentes?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar em horas de atendimento e obter respostas às suas questões sobre Agentes de IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original no seu idioma nativo deve ser considerado a fonte oficial. Para informações críticas, recomenda-se a tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->