# Agentes de IA em Produção: Observabilidade & Avaliação

[![AI Agents in Production](../../../translated_images/pt-PT/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

À medida que os agentes de IA passam de protótipos experimentais para aplicações no mundo real, a capacidade de compreender o seu comportamento, monitorizar o seu desempenho e avaliar sistematicamente os seus resultados torna-se importante.

## Objetivos de Aprendizagem

Após completar esta lição, irá saber fazer/compreender:
- Conceitos essenciais de observabilidade e avaliação de agentes
- Técnicas para melhorar o desempenho, custos e eficácia dos agentes
- O que e como avaliar sistematicamente os seus agentes de IA
- Como controlar custos ao implementar agentes de IA em produção
- Como instrumentar agentes construídos com AutoGen

O objetivo é equipá-lo com o conhecimento para transformar os seus agentes "caixa preta" em sistemas transparentes, geríveis e fiáveis.

_**Nota:** É importante implementar Agentes de IA que sejam seguros e confiáveis. Consulte também a lição [Construção de Agentes de IA Confiáveis](./06-building-trustworthy-agents/README.md)._

## Rastreamentos e Spans

Ferramentas de observabilidade, como [Langfuse](https://langfuse.com/) ou [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry), normalmente representam execuções de agentes como rastreamentos e spans.

- **Rastreamento (Trace)** representa uma tarefa completa do agente do início ao fim (como tratar uma consulta de utilizador).
- **Spans** são passos individuais dentro do rastreamento (como chamar um modelo de linguagem ou recuperar dados).

![Trace tree in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Sem observabilidade, um agente de IA pode parecer uma "caixa preta" — o seu estado interno e raciocínio são opacos, dificultando a deteção de problemas ou otimização do desempenho. Com observabilidade, os agentes tornam-se "caixas de vidro", oferecendo transparência que é vital para construir confiança e garantir que operam conforme previsto.

## Porque a Observabilidade é Importante em Ambientes de Produção

A transição dos agentes de IA para ambientes de produção introduz um novo conjunto de desafios e requisitos. A observabilidade deixa de ser algo "agradável de ter" para se tornar uma capacidade crítica:

*   **Depuração e Análise da Causa Raiz**: Quando um agente falha ou produz um resultado inesperado, as ferramentas de observabilidade fornecem os rastreamentos necessários para identificar a origem do erro. Isto é especialmente importante em agentes complexos que podem envolver múltiplas chamadas a LLM, interações com ferramentas e lógica condicional.
*   **Gestão de Latência e Custos**: Os agentes de IA frequentemente dependem de LLMs e outras APIs externas faturadas por token ou por chamada. A observabilidade permite o acompanhamento preciso dessas chamadas, ajudando a identificar operações excessivamente lentas ou caras. Isto permite às equipas otimizar prompts, selecionar modelos mais eficientes ou redesenhar fluxos de trabalho para controlar custos operacionais e garantir uma boa experiência ao utilizador.
*   **Confiança, Segurança e Conformidade**: Em muitas aplicações, é importante garantir que os agentes se comportam de forma segura e ética. A observabilidade fornece um registo de auditoria das ações e decisões do agente. Este pode ser usado para detetar e mitigar problemas como injeção de prompt, geração de conteúdo prejudicial ou o manuseio incorreto de informações pessoalmente identificáveis (PII). Por exemplo, pode rever rastreamentos para entender por que um agente forneceu certa resposta ou usou uma ferramenta específica.
*   **Ciclos de Melhoria Contínua**: Os dados de observabilidade são a base de um processo de desenvolvimento iterativo. Ao monitorizar o desempenho dos agentes no mundo real, as equipas podem identificar áreas para melhoria, recolher dados para ajuste fino dos modelos e validar o impacto das alterações. Isto cria um ciclo de feedback onde insights da produção a partir da avaliação online informam experimentação e refinamento offline, levando a um desempenho progressivamente melhor dos agentes.

## Métricas-Chave a Monitorizar

Para monitorizar e entender o comportamento do agente, deve-se acompanhar uma série de métricas e sinais. Embora as métricas específicas possam variar conforme o propósito do agente, algumas são universalmente importantes.

Aqui estão algumas das métricas mais comuns que as ferramentas de observabilidade monitorizam:

**Latência:** Com que rapidez responde o agente? Tempos de espera longos impactam negativamente a experiência do utilizador. Deve medir a latência para tarefas e etapas individuais, rastreando as execuções do agente. Por exemplo, um agente que leva 20 segundos para todas as chamadas do modelo pode ser acelerado utilizando um modelo mais rápido ou executando chamadas em paralelo.

**Custos:** Qual o custo por execução do agente? Os agentes de IA dependem de chamadas a LLM faturadas por token ou APIs externas. O uso frequente de ferramentas ou múltiplos prompts pode aumentar rapidamente os custos. Por exemplo, se um agente chama um LLM cinco vezes para uma melhoria marginal da qualidade, deve avaliar se o custo é justificado ou se pode reduzir o número de chamadas ou usar um modelo mais barato. Monitorização em tempo real pode também ajudar a identificar picos inesperados (ex.: bugs que causam loops excessivos de API).

**Erros de Pedido:** Quantas requisições falharam? Isto pode incluir erros de API ou chamadas a ferramentas que falharam. Para tornar o seu agente mais robusto contra estes erros em produção, pode configurar mecanismos de fallback ou tentativas de repetição. Ex.: se o fornecedor LLM A estiver indisponível, pode mudar para o fornecedor LLM B como reserva.

**Feedback do Utilizador:** Implementar avaliações diretas dos utilizadores fornece insights valiosos. Isto pode incluir classificações explícitas (👍gosto/👎não gosto, ⭐ 1-5 estrelas) ou comentários textuais. Feedback negativo consistente deve alertá-lo pois é um sinal de que o agente não está a funcionar como esperado.

**Feedback Implícito do Utilizador:** Os comportamentos dos utilizadores fornecem feedback indireto mesmo sem classificações explícitas. Isto pode incluir reformulação imediata da pergunta, consultas repetidas ou clicar num botão de retry. Ex.: se notar que os utilizadores fazem repetidamente a mesma pergunta, é um sinal de que o agente não está a funcionar como esperado.

**Precisão:** Com que frequência o agente produz resultados corretos ou desejáveis? As definições de precisão variam (ex.: correção na resolução de problemas, precisão na recuperação de informação, satisfação do utilizador). O primeiro passo é definir o que constitui sucesso para o seu agente. Pode acompanhar precisão através de verificações automáticas, pontuações de avaliação ou etiquetas de conclusão da tarefa. Por exemplo, marcar rastreamentos como "bem-sucedidos" ou "falhados".

**Métricas de Avaliação Automática:** Pode também configurar avaliações automáticas. Por exemplo, pode usar um LLM para pontuar a saída do agente, p.ex., se é útil, precisa ou não. Existem também várias bibliotecas open source que ajudam a pontuar diferentes aspetos do agente. Ex.: [RAGAS](https://docs.ragas.io/) para agentes RAG ou [LLM Guard](https://llm-guard.com/) para detetar linguagem prejudicial ou injeção de prompt.

Na prática, uma combinação destas métricas oferece a melhor cobertura da saúde de um agente de IA. No [caderno de exemplo](./code_samples/10_autogen_evaluation.ipynb) deste capítulo, iremos mostrar como estas métricas se apresentam em exemplos reais, mas primeiro, vamos aprender como é um fluxo típico de avaliação.

## Instrumente o Seu Agente

Para recolher dados de rastreamento, precisará instrumentar o seu código. O objetivo é instrumentar o código do agente para emitir rastreamentos e métricas que possam ser capturados, processados e visualizados por uma plataforma de observabilidade.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) tornou-se um standard da indústria para observabilidade de LLMs. Fornece um conjunto de APIs, SDKs e ferramentas para gerar, recolher e exportar dados de telemetria.

Existem muitas bibliotecas de instrumentação que envolvem frameworks existentes de agentes e facilitam a exportação de spans OpenTelemetry para uma ferramenta de observabilidade. Abaixo está um exemplo de como instrumentar um agente AutoGen com a [biblioteca de instrumentação OpenLit](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

O [caderno de exemplo](./code_samples/10_autogen_evaluation.ipynb) deste capítulo demonstra como instrumentar o seu agente AutoGen.

**Criação Manual de Spans:** Apesar das bibliotecas de instrumentação fornecerem uma boa base, há frequentemente casos onde se precisa de informação mais detalhada ou personalizada. Pode criar spans manualmente para adicionar lógica customizada da aplicação. Mais importante, pode enriquecer spans criados automática ou manualmente com atributos personalizados (também conhecidos como tags ou metadados). Estes atributos podem incluir dados específicos do negócio, cálculos intermédios ou qualquer contexto que seja útil para depuração ou análise, como `user_id`, `session_id` ou `model_version`.

Exemplo de criação manual de rastreamentos e spans com o [SDK Langfuse Python](https://langfuse.com/docs/sdk/python/sdk-v3):

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Avaliação do Agente

A observabilidade fornece métricas, mas a avaliação é o processo de analisar esses dados (e realizar testes) para determinar como está o desempenho do agente de IA e como pode ser melhorado. Por outras palavras, uma vez que tem esses rastreamentos e métricas, como os usa para julgar o agente e tomar decisões?

A avaliação regular é importante porque os agentes de IA são frequentemente não determinísticos e podem evoluir (por atualizações ou mudança no comportamento do modelo) – sem avaliação, não saberia se o seu "agente inteligente" está realmente a fazer bem o seu trabalho ou se decaiu.

Existem duas categorias de avaliação para agentes de IA: **avaliação online** e **avaliação offline**. Ambas são valiosas e complementares. Normalmente começamos pela avaliação offline, pois este é o passo mínimo necessário antes de implementar qualquer agente.

### Avaliação Offline

![Dataset items in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Envolve avaliar o agente num ambiente controlado, tipicamente usando conjuntos de dados de teste, não consultas reais de utilizadores. Usa conjuntos de dados curados onde sabe qual é o resultado esperado ou comportamento correto, e depois executa o seu agente nesses dados.

Por exemplo, se construiu um agente para resolver problemas matemáticos em palavra, pode ter um [conjunto de dados de teste](https://huggingface.co/datasets/gsm8k) com 100 problemas e respostas conhecidas. A avaliação offline é geralmente feita durante o desenvolvimento (e pode fazer parte das pipelines de CI/CD) para verificar melhorias ou proteger contra regressões. A vantagem é que é **repetível e pode obter métricas claras de precisão, uma vez que tem a verdade fundamentada**. Pode também simular consultas de utilizador e medir as respostas do agente contra respostas ideais ou usar métricas automáticas como descrito acima.

O grande desafio com a avaliação offline é garantir que o conjunto de dados de teste é abrangente e se mantém relevante – o agente pode usar bem um conjunto fixo, mas encontrar consultas muito diferentes em produção. Assim, deve manter os conjuntos de teste atualizados com novos casos de borda e exemplos que reflitam os cenários do mundo real. Uma mistura de pequenos casos “smoke test” e conjuntos maiores de avaliação é útil: pequenos conjuntos para verificações rápidas e conjuntos maiores para métricas de desempenho mais amplas.

### Avaliação Online

![Observability metrics overview](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Refere-se à avaliação do agente num ambiente real e ao vivo, ou seja, durante o uso efetivo em produção. A avaliação online envolve monitorizar o desempenho do agente nas interações reais dos utilizadores e analisar os resultados continuamente.

Por exemplo, pode acompanhar taxas de sucesso, pontuações de satisfação do utilizador ou outras métricas no tráfego ao vivo. A vantagem da avaliação online é que **captura coisas que pode não antecipar num laboratório** – pode observar desvios do modelo ao longo do tempo (se a eficácia do agente decrescer à medida que os padrões de entrada mudam) e detectar consultas ou situações inesperadas que não estavam nos dados de teste. Fornece uma imagem real de como o agente se comporta no "mundo real".

A avaliação online envolve frequentemente a recolha de feedback implícito e explícito dos utilizadores, como foi discutido, e possivelmente a realização de testes sombra ou testes A/B (onde uma nova versão do agente corre em paralelo para comparação com a antiga). O desafio é que pode ser difícil obter etiquetas ou pontuações fiáveis para interações ao vivo – pode depender do feedback do utilizador ou de métricas subsequentes (ex.: se o utilizador clicou no resultado).

### Combinar os dois

As avaliações online e offline não são mutuamente exclusivas; são altamente complementares. Os insights da monitorização online (ex.: novos tipos de consultas onde o agente tem desempenho fraco) podem ser usados para melhorar os conjuntos de dados de teste offline. Por outro lado, agentes que performam bem nos testes offline podem depois ser implementados com mais confiança e monitorizados online.

De facto, muitas equipas adotam um ciclo:

_avaliar offline -> implementar -> monitorizar online -> recolher novos casos de falha -> adicionar ao conjunto offline -> refinar agente -> repetir_.

## Problemas Comuns

Ao implementar agentes de IA em produção, poderá encontrar vários desafios. Aqui estão alguns problemas comuns e as suas possíveis soluções:

| **Problema**    | **Solução Potencial**   |
| ------------- | ------------------ |
| Agente de IA não executa tarefas de forma consistente | - Refinar o prompt dado ao agente de IA; ser claro nos objetivos.<br>- Identificar onde dividir as tarefas em subtarefas e lidar com elas por múltiplos agentes pode ajudar. |
| Agente de IA entra em loops contínuos  | - Garantir que tem termos e condições claros de término para que o agente saiba quando parar o processo.<br>- Para tarefas complexas que requerem raciocínio e planeamento, usar um modelo maior especializado nessas tarefas. |
| Chamadas às ferramentas do agente não estão a funcionar bem   | - Testar e validar a saída da ferramenta fora do sistema do agente.<br>- Refinar os parâmetros definidos, prompts e nomes das ferramentas.  |
| Sistema Multi-Agente não funciona de forma consistente | - Refinar os prompts dados a cada agente para garantir que são específicos e distintos entre si.<br>- Construir um sistema hierárquico usando um agente de "roteamento" ou controlador para determinar qual agente é o correto. |

Muitos destes problemas podem ser identificados de forma mais eficaz com observabilidade implementada. Os rastreamentos e métricas discutidos anteriormente ajudam a localizar exatamente onde no fluxo de trabalho do agente ocorrem os problemas, tornando a depuração e otimização muito mais eficientes.

## Gestão de Custos
Aqui estão algumas estratégias para gerir os custos de implementação de agentes de IA em produção:

**Utilizar Modelos Mais Pequenos:** Modelos de Linguagem Pequenos (SLMs) podem ter um bom desempenho em certos casos de uso agentic e reduzirão significativamente os custos. Como mencionado anteriormente, construir um sistema de avaliação para determinar e comparar o desempenho em relação a modelos maiores é a melhor forma de entender quão bem um SLM se comportará no seu caso de uso. Considere usar SLMs para tarefas mais simples, como classificação de intenção ou extração de parâmetros, enquanto reserva modelos maiores para raciocínios complexos.

**Usar um Modelo de Roteamento:** Uma estratégia semelhante é usar uma diversidade de modelos e tamanhos. Pode usar um LLM/SLM ou uma função serverless para encaminhar pedidos com base na complexidade para os modelos mais adequados. Isto também ajudará a reduzir custos, garantindo o desempenho nas tarefas certas. Por exemplo, encaminhar consultas simples para modelos menores e mais rápidos, e usar apenas modelos grandes e dispendiosos para tarefas de raciocínio complexo.

**Cache de Respostas:** Identificar pedidos e tarefas comuns e fornecer as respostas antes de passarem pelo seu sistema agentic é uma boa forma de reduzir o volume de pedidos semelhantes. Pode até implementar um fluxo para identificar o quão semelhante um pedido é aos seus pedidos em cache usando modelos de IA mais básicos. Esta estratégia pode reduzir significativamente os custos para perguntas frequentes ou fluxos de trabalho comuns.

## Vamos ver como isto funciona na prática

No [exemplo de notebook desta seção](./code_samples/10_autogen_evaluation.ipynb), veremos exemplos de como podemos usar ferramentas de observabilidade para monitorizar e avaliar o nosso agente.


### Tem mais perguntas sobre Agentes de IA em Produção?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar em sessões de esclarecimento e obter respostas às suas perguntas sobre Agentes de IA.

## Aula Anterior

[Metacognition Design Pattern](../09-metacognition/README.md)

## Próxima Aula

[Agentic Protocols](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos pela precisão, pedimos que tenha em conta que traduções automáticas podem conter erros ou imprecisões. O documento original na sua língua nativa deverá ser considerado a fonte autoritativa. Para informações críticas, recomenda-se a tradução profissional por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações erradas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->