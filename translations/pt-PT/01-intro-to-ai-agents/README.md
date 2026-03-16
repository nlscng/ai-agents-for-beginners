[![Introdução aos Agentes de IA](../../../translated_images/pt-PT/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Clique na imagem acima para ver o vídeo desta lição)_


# Introdução aos Agentes de IA e Casos de Uso de Agentes

Bem-vindo ao curso "Agentes de IA para Iniciantes"! Este curso oferece conhecimentos fundamentais e exemplos aplicados para a construção de Agentes de IA.

Junte-se à <a href="https://discord.gg/kzRShWzttr" target="_blank">Comunidade Azure AI no Discord</a> para conhecer outros aprendizes e construtores de Agentes de IA e tirar quaisquer dúvidas que tenha sobre este curso.

Para começar este curso, iniciamos por obter uma melhor compreensão do que são Agentes de IA e como podemos usá-los nas aplicações e fluxos de trabalho que criamos.

## Introdução

Esta lição cobre:

- O que são Agentes de IA e quais são os diferentes tipos de agentes?
- Quais casos de uso são mais adequados para Agentes de IA e como podem ajudar-nos?
- Quais são alguns dos blocos básicos na conceção de Soluções Agentivas?

## Objetivos de Aprendizagem
Após completar esta lição, deverá ser capaz de:

- Compreender os conceitos de Agente de IA e como diferem de outras soluções de IA.
- Aplicar Agentes de IA da forma mais eficiente.
- Conceber soluções agentivas produtivamente para utilizadores e clientes.

## Definindo Agentes de IA e Tipos de Agentes de IA

### O que são Agentes de IA?

Agentes de IA são **sistemas** que permitem que **Modelos de Linguagem Ampla (LLMs)** **executem ações** ao ampliar as suas capacidades, dando aos LLMs **acesso a ferramentas** e **conhecimento**.

Vamos decompor esta definição em partes menores:

- **Sistema** - É importante pensar nos agentes não apenas como um único componente, mas como um sistema de múltiplos componentes. A nível básico, os componentes de um Agente de IA são:
  - **Ambiente** - O espaço definido onde o Agente de IA está a operar. Por exemplo, se tivermos um agente de IA para reservas de viagem, o ambiente poderia ser o sistema de reservas de viagem que o agente utiliza para completar tarefas.
  - **Sensores** - Os ambientes têm informação e fornecem feedback. Os Agentes de IA usam sensores para recolher e interpretar essa informação sobre o estado atual do ambiente. No exemplo do Agente de Reservas de Viagem, o sistema de reservas pode fornecer informações como disponibilidade de hotéis ou preços de voos.
  - **Atuadores** - Assim que o Agente de IA recebe o estado atual do ambiente, para a tarefa em curso o agente determina qual ação executar para alterar o ambiente. Para o agente de reservas, pode ser reservar um quarto disponível para o utilizador.

![O que são Agentes de IA?](../../../translated_images/pt-PT/what-are-ai-agents.1ec8c4d548af601a.webp)

**Modelos de Linguagem Ampla** - O conceito de agentes existia antes da criação dos LLMs. A vantagem de construir Agentes de IA com LLMs é a sua capacidade de interpretar a linguagem humana e dados. Esta capacidade permite aos LLMs interpretar a informação do ambiente e definir um plano para alterar o ambiente.

**Executar Ações** - Fora dos sistemas de Agentes de IA, os LLMs estão limitados a situações em que a ação é gerar conteúdo ou informação com base no comando do utilizador. Dentro dos sistemas de Agentes de IA, os LLMs podem realizar tarefas ao interpretar o pedido do utilizador e usando ferramentas disponíveis no seu ambiente.

**Acesso a Ferramentas** - Quais ferramentas o LLM tem acesso é definido por 1) o ambiente onde opera e 2) o desenvolvedor do Agente de IA. No exemplo do agente de viagem, as ferramentas do agente são limitadas pelas operações disponíveis no sistema de reservas e/ou o desenvolvedor pode limitar o acesso do agente apenas a voos.

**Memória+Conhecimento** - A memória pode ser de curto prazo no contexto da conversa entre o utilizador e o agente. A longo prazo, fora da informação fornecida pelo ambiente, os Agentes de IA podem também recuperar conhecimento de outros sistemas, serviços, ferramentas e até outros agentes. No exemplo do agente de viagem, esse conhecimento pode ser a informação sobre as preferências de viagem do utilizador localizada numa base de dados de clientes.

### Os diferentes tipos de agentes

Agora que temos uma definição geral de Agentes de IA, vejamos alguns tipos específicos de agentes e como estes seriam aplicados a um agente de reserva de viagens.

| **Tipo de Agente**           | **Descrição**                                                                                                                       | **Exemplo**                                                                                                                                                                                                                    |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Agentes Reflexos Simples** | Executam ações imediatas baseadas em regras predefinidas.                                                                          | Agente de viagem interpreta o contexto do email e encaminha reclamações de viagens para o serviço de apoio ao cliente.                                                                                                         |
| **Agentes Reflexos Baseados em Modelo** | Executam ações baseadas num modelo do mundo e alterações a esse modelo.                                                             | Agente de viagem prioriza rotas com alterações significativas de preço com base em dados históricos de preços.                                                                                                                 |
| **Agentes Baseados em Objetivos** | Criam planos para atingir objetivos específicos, interpretando o objetivo e determinando ações para o alcançar.                   | Agente de viagem reserva uma viagem determinando os arranjos de viagem necessários (carro, transporte público, voos) desde a localização atual até ao destino.                                                                  |
| **Agentes Baseados em Utilidade** | Consideram preferências e ponderam compensações numericamente para determinar como alcançar objetivos.                             | Agente de viagem maximiza utilidade ponderando conveniência versus custo ao reservar viagem.                                                                                                                                   |
| **Agentes de Aprendizagem**  | Melhoram ao longo do tempo respondendo a feedback e ajustando ações em conformidade.                                               | Agente de viagem melhora utilizando feedback dos clientes em questionários pós-viagem para ajustar futuras reservas.                                                                                                           |
| **Agentes Hierárquicos**     | Incluem múltiplos agentes num sistema em camadas, com agentes de nível superior a dividir tarefas em subtarefas para os agentes de nível inferior completarem. | Agente de viagem cancela uma viagem dividindo a tarefa em subtarefas (por exemplo, cancelar reservas específicas) e pedindo aos agentes de nível inferior para as concretizarem, reportando depois ao agente de nível superior.        |
| **Sistemas Multi-Agente (MAS)** | Agentes completam tarefas de forma independente, seja cooperativa ou competitiva.                                                 | Cooperativo: Múltiplos agentes reservam serviços de viagem específicos como hotéis, voos e entretenimento. Competitivo: Múltiplos agentes gerem e competem por um calendário partilhado de reservas de hotel para alojar clientes. |

## Quando Usar Agentes de IA

Na secção anterior, usamos o caso de uso do agente de viagem para explicar como os diferentes tipos de agentes podem ser usados em diferentes cenários de reserva de viagens. Continuaremos a usar esta aplicação ao longo do curso.

Vamos analisar os tipos de casos de uso para os quais os Agentes de IA são mais indicados:

![Quando usar Agentes de IA?](../../../translated_images/pt-PT/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Problemas Abertos** - permitindo ao LLM determinar os passos necessários para completar uma tarefa porque nem sempre podem ser codificados diretamente num fluxo de trabalho.
- **Processos em Múltiplos Passos** - tarefas que requerem um nível de complexidade em que o Agente de IA precisa usar ferramentas ou informação ao longo de várias interações em vez de numa única recuperação.  
- **Melhoria ao Longo do Tempo** - tarefas em que o agente pode melhorar ao longo do tempo recebendo feedback do ambiente ou dos utilizadores para oferecer melhor utilidade.

Abordamos mais considerações sobre o uso de Agentes de IA na lição Construindo Agentes de IA Confiáveis.

## Fundamentos das Soluções Agentivas

### Desenvolvimento de Agentes

O primeiro passo na conceção de um sistema de Agente de IA é definir as ferramentas, ações e comportamentos. Neste curso, focamo-nos no uso do **Azure AI Agent Service** para definir os nossos Agentes. Este serviço oferece funcionalidades como:

- Seleção de Modelos Abertos como OpenAI, Mistral e Llama
- Uso de Dados Licenciados através de fornecedores como Tripadvisor
- Utilização de ferramentas padronizadas OpenAPI 3.0

### Padrões Agentivos

A comunicação com LLMs é feita através de prompts. Dada a natureza semi-autónoma dos Agentes de IA, nem sempre é possível ou necessário re-promptar manualmente o LLM após uma mudança no ambiente. Usamos **Padrões Agentivos** que nos permitem solicitar ao LLM interações em múltiplos passos de uma forma mais escalável.

Este curso está dividido em alguns dos atuais padrões agentivos populares.

### Frameworks Agentivos

Frameworks agentivos permitem aos desenvolvedores implementar padrões agentivos através de código. Esses frameworks oferecem templates, plugins e ferramentas para melhor colaboração entre Agentes de IA. Estes benefícios providenciam capacidades para melhor observabilidade e resolução de problemas em sistemas de Agentes de IA.

Neste curso, iremos explorar o framework AutoGen, orientado para investigação, e o framework Agent, pronto para produção, da Semantic Kernel.

## Exemplos de Código

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Tem Mais Perguntas sobre Agentes de IA?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar em horas de atendimento e esclarecer as suas dúvidas sobre Agentes de IA.

## Lição Anterior

[Configuração do Curso](../00-course-setup/README.md)

## Próxima Lição

[Explorando Frameworks Agentivos](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, por favor, tenha em conta que traduções automáticas podem conter erros ou imprecisões. O documento original no seu idioma nativo deve ser considerado a fonte oficial. Para informações críticas, recomenda-se a tradução profissional por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas resultantes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->