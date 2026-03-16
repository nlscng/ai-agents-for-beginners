# Agentes de IA em Produção: Observabilidade & Avaliação

[![Agentes de IA em Produção](../../../translated_images/pt-BR/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

À medida que agentes de IA passam de protótipos experimentais para aplicações no mundo real, a capacidade de entender seu comportamento, monitorar seu desempenho e avaliar sistematicamente suas saídas se torna importante.

## Objetivos de Aprendizagem

Após concluir esta lição, você saberá como/entenderá:
- Conceitos centrais de observabilidade e avaliação de agentes
- Técnicas para melhorar o desempenho, os custos e a efetividade dos agentes
- O que e como avaliar seus agentes de IA de forma sistemática
- Como controlar custos ao implantar agentes de IA em produção
- Como instrumentar agentes construídos com AutoGen

O objetivo é capacitá-lo com o conhecimento para transformar seus agentes "caixa-preta" em sistemas transparentes, gerenciáveis e confiáveis.

_**Nota:** É importante implantar Agentes de IA que sejam seguros e confiáveis. Confira também a lição [Building Trustworthy AI Agents](./06-building-trustworthy-agents/README.md)._

## Traces e Spans

Ferramentas de observabilidade como [Langfuse](https://langfuse.com/) ou [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) geralmente representam execuções de agentes como traces e spans.

- **Trace** representa uma tarefa completa do agente do início ao fim (como lidar com uma consulta do usuário).
- **Spans** são etapas individuais dentro do trace (como chamar um modelo de linguagem ou recuperar dados).

![Árvore de rastreamento no Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Sem observabilidade, um agente de IA pode parecer uma "caixa-preta" — seu estado interno e raciocínio são opacos, tornando difícil diagnosticar problemas ou otimizar o desempenho. Com observabilidade, agentes se tornam "caixas de vidro", oferecendo transparência vital para construir confiança e garantir que operem conforme o esperado.

## Por que a Observabilidade Importa em Ambientes de Produção

A transição de agentes de IA para ambientes de produção introduz um novo conjunto de desafios e requisitos. Observabilidade deixa de ser um "desejável" e passa a ser uma capacidade crítica:

*   **Depuração e Análise da Causa Raiz**: Quando um agente falha ou produz uma saída inesperada, ferramentas de observabilidade fornecem os traces necessários para identificar a origem do erro. Isso é especialmente importante em agentes complexos que podem envolver múltiplas chamadas LLM, interações com ferramentas e lógica condicional.
*   **Gerenciamento de Latência e Custos**: Agentes de IA frequentemente dependem de LLMs e outras APIs externas que são cobradas por token ou por chamada. A observabilidade permite rastrear com precisão essas chamadas, ajudando a identificar operações excessivamente lentas ou caras. Isso possibilita que equipes otimizem prompts, escolham modelos mais eficientes ou redesenhem fluxos de trabalho para controlar custos operacionais e garantir uma boa experiência do usuário.
*   **Confiança, Segurança e Conformidade**: Em muitas aplicações, é importante garantir que agentes se comportem de forma segura e ética. Observabilidade fornece um rastro de auditoria das ações e decisões do agente. Isso pode ser usado para detectar e mitigar problemas como injeção de prompt, geração de conteúdo prejudicial ou manuseio indevido de informações pessoalmente identificáveis (PII). Por exemplo, você pode revisar traces para entender por que um agente forneceu certa resposta ou usou uma ferramenta específica.
*   **Ciclos de Melhoria Contínua**: Dados de observabilidade são a base de um processo de desenvolvimento iterativo. Ao monitorar como agentes se comportam no mundo real, equipes podem identificar áreas para melhoria, coletar dados para ajuste fino de modelos e validar o impacto de mudanças. Isso cria um loop de feedback onde insights de produção provenientes da avaliação online alimentam experimentação e refinamento offline, levando a um desempenho progressivamente melhor do agente.

## Métricas Principais para Acompanhar

Para monitorar e entender o comportamento do agente, uma variedade de métricas e sinais deve ser acompanhada. Embora as métricas específicas possam variar conforme o propósito do agente, algumas são universalmente importantes.

Aqui estão algumas das métricas mais comuns que ferramentas de observabilidade monitoram:

**Latência:** Quão rápido o agente responde? Tempos de espera longos impactam negativamente a experiência do usuário. Você deve medir a latência de tarefas e etapas individuais traçando execuções do agente. Por exemplo, um agente que demora 20 segundos para todas as chamadas de modelo poderia ser acelerado usando um modelo mais rápido ou executando chamadas de modelo em paralelo.

**Custos:** Qual é a despesa por execução do agente? Agentes de IA dependem de chamadas LLM cobradas por token ou de APIs externas. Uso frequente de ferramentas ou múltiplos prompts pode aumentar rapidamente os custos. Por exemplo, se um agente chama um LLM cinco vezes por uma melhoria marginal de qualidade, você precisa avaliar se o custo é justificado ou se poderia reduzir o número de chamadas ou usar um modelo mais barato. Monitoramento em tempo real também pode ajudar a identificar picos inesperados (por exemplo, bugs causando loops excessivos de API).

**Erros de Requisição:** Quantas requisições o agente falhou? Isso pode incluir erros de API ou chamadas de ferramenta que falharam. Para tornar seu agente mais robusto contra esses problemas em produção, você pode configurar alternativas ou tentativas de nova chamada (retries). Ex.: se o provedor de LLM A estiver fora do ar, você alterna para o provedor de LLM B como backup.

**Feedback do Usuário:** Implementar avaliações diretas dos usuários fornece insights valiosos. Isso pode incluir avaliações explícitas (👍thumbs-up/👎down, ⭐1-5 estrelas) ou comentários textuais. Feedback negativo consistente deve alertá-lo, pois é um sinal de que o agente não está funcionando como esperado.

**Feedback Implícito do Usuário:** Comportamentos dos usuários fornecem feedback indireto mesmo sem avaliações explícitas. Isso pode incluir reformulação imediata de perguntas, consultas repetidas ou clicar em um botão de tentar novamente. Ex.: se você perceber que usuários repetidamente fazem a mesma pergunta, isso é um sinal de que o agente não está funcionando como esperado.

**Precisão:** Com que frequência o agente produz saídas corretas ou desejáveis? As definições de precisão variam (por exemplo, corretude na resolução de problemas, precisão em recuperação de informação, satisfação do usuário). O primeiro passo é definir como o sucesso se parece para seu agente. Você pode acompanhar a precisão por meio de verificações automatizadas, scores de avaliação ou rótulos de conclusão de tarefas. Por exemplo, marcar traces como "succeeded" ou "failed".

**Métricas de Avaliação Automatizadas:** Você também pode configurar avaliações automatizadas. Por exemplo, pode usar um LLM para pontuar a saída do agente, por exemplo, se foi útil, precisa ou não. Existem também várias bibliotecas de código aberto que ajudam a pontuar diferentes aspectos do agente. Ex.: [RAGAS](https://docs.ragas.io/) para agentes RAG ou [LLM Guard](https://llm-guard.com/) para detectar linguagem prejudicial ou injeção de prompt.

Na prática, uma combinação dessas métricas fornece a melhor cobertura da saúde de um agente de IA. No [notebook de exemplo](./code_samples/10_autogen_evaluation.ipynb) deste capítulo, mostraremos como essas métricas aparecem em exemplos reais, mas primeiro, aprenderemos como é um fluxo de trabalho típico de avaliação.

## Instrumente seu Agente

Para coletar dados de tracing, você precisará instrumentar seu código. O objetivo é instrumentar o código do agente para emitir traces e métricas que possam ser capturados, processados e visualizados por uma plataforma de observabilidade.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) emergiu como um padrão da indústria para observabilidade de LLMs. Ele fornece um conjunto de APIs, SDKs e ferramentas para gerar, coletar e exportar dados de telemetria.

Existem muitas bibliotecas de instrumentação que envolvem frameworks de agente existentes e facilitam exportar spans do OpenTelemetry para uma ferramenta de observabilidade. Abaixo está um exemplo de instrumentação de um agente AutoGen com a [biblioteca de instrumentação OpenLit](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

O [notebook de exemplo](./code_samples/10_autogen_evaluation.ipynb) neste capítulo demonstrará como instrumentar seu agente AutoGen.

**Criação Manual de Spans:** Embora bibliotecas de instrumentação forneçam uma boa linha de base, muitas vezes há casos em que informações mais detalhadas ou personalizadas são necessárias. Você pode criar spans manualmente para adicionar lógica de aplicação personalizada. Mais importante, eles podem enriquecer spans criados automaticamente ou manualmente com atributos personalizados (também conhecidos como tags ou metadados). Esses atributos podem incluir dados específicos do negócio, cálculos intermediários ou qualquer contexto que possa ser útil para depuração ou análise, como `user_id`, `session_id` ou `model_version`.

Exemplo de criação de traces e spans manualmente com o [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3): 

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Avaliação do Agente

Observabilidade nos dá métricas, mas avaliação é o processo de analisar esses dados (e realizar testes) para determinar quão bem um agente de IA está desempenhando e como ele pode ser melhorado. Em outras palavras, uma vez que você tem esses traces e métricas, como usá-los para julgar o agente e tomar decisões?

Avaliações regulares são importantes porque agentes de IA costumam ser não-determinísticos e podem evoluir (por meio de atualizações ou alteração do comportamento do modelo) – sem avaliação, você não saberia se seu "agente inteligente" está realmente fazendo bem seu trabalho ou se regrediu.

Existem duas categorias de avaliações para agentes de IA: **avaliação online** e **avaliação offline**. Ambas são valiosas e se complementam. Normalmente começamos com avaliação offline, pois este é o passo mínimo necessário antes de implantar qualquer agente.

### Avaliação Offline

![Itens do conjunto de dados no Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Isso envolve avaliar o agente em um ambiente controlado, tipicamente usando conjuntos de teste, não consultas de usuários ao vivo. Você usa conjuntos de dados curados onde se sabe qual é a saída esperada ou o comportamento correto, e então executa seu agente sobre eles.

Por exemplo, se você construiu um agente para resolver problemas matemáticos em texto, pode ter um [conjunto de teste](https://huggingface.co/datasets/gsm8k) de 100 problemas com respostas conhecidas. A avaliação offline costuma ser feita durante o desenvolvimento (e pode fazer parte de pipelines de CI/CD) para verificar melhorias ou proteger contra regressões. O benefício é que é **reprodutível e você pode obter métricas claras de precisão, já que tem a verdade de base**. Você também pode simular consultas de usuários e medir as respostas do agente contra respostas ideais ou usar métricas automatizadas, como descrito acima.

O principal desafio da avaliação offline é garantir que seu conjunto de teste seja abrangente e permaneça relevante – o agente pode ter bom desempenho em um conjunto de teste fixo, mas encontrar consultas muito diferentes em produção. Portanto, você deve manter os conjuntos de teste atualizados com novos casos de borda e exemplos que reflitam cenários do mundo real. Uma mistura de pequenos casos de "smoke test" e conjuntos maiores de avaliação é útil: conjuntos pequenos para verificações rápidas e conjuntos maiores para métricas de desempenho mais amplas.

### Avaliação Online 

![Visão geral das métricas de observabilidade](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Refere-se a avaliar o agente em um ambiente ao vivo e do mundo real, ou seja, durante o uso real em produção. Avaliação online envolve monitorar o desempenho do agente em interações reais de usuários e analisar os resultados de forma contínua.

Por exemplo, você pode acompanhar taxas de sucesso, pontuações de satisfação do usuário ou outras métricas no tráfego ao vivo. A vantagem da avaliação online é que ela **captura coisas que você pode não antecipar em um ambiente de laboratório** – você pode observar deriva do modelo ao longo do tempo (se a efetividade do agente se degradar conforme padrões de entrada mudam) e capturar consultas ou situações inesperadas que não estavam em seus dados de teste. Isso fornece uma imagem verdadeira de como o agente se comporta em produção.

A avaliação online frequentemente envolve coletar feedback implícito e explícito dos usuários, como discutido, e possivelmente executar testes shadow ou testes A/B (onde uma nova versão do agente roda em paralelo para comparação com a antiga). O desafio é que pode ser complicado obter rótulos ou pontuações confiáveis para interações ao vivo – você pode depender do feedback do usuário ou de métricas downstream (como se o usuário clicou no resultado).

### Combinando os dois

Avaliações online e offline não são mutuamente exclusivas; elas se complementam muito bem. Insights do monitoramento online (por exemplo, novos tipos de consultas de usuários onde o agente tem baixo desempenho) podem ser usados para aumentar e melhorar conjuntos de teste offline. Por outro lado, agentes que se saem bem em testes offline podem ser implantados com mais confiança e monitorados online.

De fato, muitas equipes adotam um loop:

_avaliar offline -> implantar -> monitorar online -> coletar novos casos de falha -> adicionar ao conjunto de teste offline -> refinar o agente -> repetir_.

## Problemas Comuns

Ao implantar agentes de IA em produção, você pode encontrar vários desafios. Aqui estão alguns problemas comuns e suas possíveis soluções:

| **Problema**    | **Solução Potencial**   |
| ------------- | ------------------ |
| Agente de IA não executa tarefas de forma consistente | - Aprimore o prompt fornecido ao Agente de IA; seja claro quanto aos objetivos.<br>- Identifique onde dividir as tarefas em subtarefas e tratá-las por múltiplos agentes pode ajudar. |
| Agente de IA entrando em loops contínuos  | - Garanta que você tenha termos e condições de término claros para que o Agente saiba quando parar o processo.<br>- Para tarefas complexas que exigem raciocínio e planejamento, use um modelo maior especializado para tarefas de raciocínio. |
| Chamadas a ferramentas pelo Agente de IA não estão tendo bom desempenho   | - Teste e valide a saída da ferramenta fora do sistema do agente.<br>- Aprimore os parâmetros definidos, prompts e a nomenclatura das ferramentas.  |
| Sistema Multi-Agente não está funcionando de forma consistente | - Aprimore os prompts dados a cada agente para garantir que sejam específicos e distintos entre si.<br>- Construa um sistema hierárquico usando um agente de "routing" ou controlador para determinar qual agente é o correto. |

Muitos desses problemas podem ser identificados de forma mais eficaz com observabilidade em vigor. Os traces e métricas discutidos anteriormente ajudam a localizar exatamente onde no fluxo de trabalho do agente os problemas ocorrem, tornando a depuração e otimização muito mais eficientes.

## Gerenciando Custos
Aqui estão algumas estratégias para gerenciar os custos de implantar agentes de IA em produção:

**Using Smaller Models:** Small Language Models (SLMs) can perform well on certain agentic use-cases and will reduce costs significantly. As mentioned earlier, building an evaluation system to determine and compare performance vs larger models is the best way to understand how well an SLM will perform on your use case. Consider using SLMs for simpler tasks like intent classification or parameter extraction, while reserving larger models for complex reasoning.

**Using a Router Model:** A similar strategy is to use a diversity of models and sizes. You can use an LLM/SLM or serverless function to route requests based on complexity to the best fit models. This will also help reduce costs while also ensuring performance on the right tasks. For example, route simple queries to smaller, faster models, and only use expensive large models for complex reasoning tasks.

**Caching Responses:** Identifying common requests and tasks and providing the responses before they go through your agentic system is a good way to reduce the volume of similar requests. You can even implement a flow to identify how similar a request is to your cached requests using more basic AI models. This strategy can significantly reduce costs for frequently asked questions or common workflows.

## Vamos ver como isso funciona na prática

In the [example notebook of this section](./code_samples/10_autogen_evaluation.ipynb), we’ll see examples of how we can use observability tools to monitor and evaluate our agent.


### Tem mais perguntas sobre Agentes de IA em Produção?

Participe do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar de horários de atendimento e obter respostas às suas perguntas sobre Agentes de IA.

## Lição Anterior

[Padrão de Design de Metacognição](../09-metacognition/README.md)

## Próxima Lição

[Protocolos Agentivos](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Isenção de responsabilidade:
Este documento foi traduzido usando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automatizadas podem conter erros ou imprecisões. O documento original, em seu idioma nativo, deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se uma tradução profissional realizada por um tradutor humano. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->