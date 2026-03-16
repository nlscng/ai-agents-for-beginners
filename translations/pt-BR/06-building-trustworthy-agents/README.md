[![Agentes de IA Confiáveis](../../../translated_images/pt-BR/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Clique na imagem acima para assistir ao vídeo desta lição)_

# Construindo Agentes de IA Confiáveis

## Introdução

Esta lição abordará:

- Como construir e implantar Agentes de IA seguros e eficazes
- Considerações importantes de segurança ao desenvolver Agentes de IA.
- Como manter a privacidade dos dados e dos usuários ao desenvolver Agentes de IA.

## Objetivos de Aprendizagem

Após concluir esta lição, você saberá como:

- Identificar e mitigar riscos ao criar Agentes de IA.
- Implementar medidas de segurança para garantir que dados e acessos sejam gerenciados adequadamente.
- Criar Agentes de IA que mantenham a privacidade dos dados e ofereçam uma experiência de usuário de qualidade.

## Segurança

Vamos primeiro olhar para a construção de aplicações agenticas seguras. Segurança significa que o agente de IA funciona conforme o projetado. Como construtores de aplicações agenticas, temos métodos e ferramentas para maximizar a segurança:

### Construindo uma Estrutura de Mensagem de Sistema

Se você já construiu uma aplicação de IA usando Modelos de Linguagem Grandes (LLMs), sabe a importância de projetar um prompt ou mensagem de sistema robusta. Esses prompts estabelecem as regras meta, instruções e diretrizes para como o LLM interagirá com o usuário e os dados.

Para Agentes de IA, o prompt do sistema é ainda mais importante, pois os Agentes de IA precisarão de instruções altamente específicas para completar as tarefas que projetamos para eles.

Para criar prompts de sistema escaláveis, podemos usar uma estrutura de mensagem de sistema para construir um ou mais agentes em nossa aplicação:

![Construindo uma Estrutura de Mensagem de Sistema](../../../translated_images/pt-BR/system-message-framework.3a97368c92d11d68.webp)

#### Passo 1: Criar uma Mensagem Meta do Sistema

O prompt meta será usado por um LLM para gerar os prompts de sistema para os agentes que criamos. O projetamos como um template para que possamos criar múltiplos agentes de forma eficiente, se necessário.

Aqui está um exemplo de uma mensagem meta do sistema que daríamos ao LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Passo 2: Criar um prompt básico

O próximo passo é criar um prompt básico para descrever o Agente de IA. Você deve incluir o papel do agente, as tarefas que o agente irá completar e quaisquer outras responsabilidades do agente.

Aqui está um exemplo:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Passo 3: Fornecer Mensagem Básica do Sistema ao LLM

Agora podemos otimizar essa mensagem de sistema fornecendo a mensagem meta do sistema como a mensagem de sistema e nossa mensagem básica do sistema.

Isso produzirá uma mensagem de sistema melhor projetada para guiar nossos agentes de IA:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Passo 4: Iterar e Melhorar

O valor dessa estrutura de mensagens de sistema está em conseguir escalar a criação de mensagens de sistema de múltiplos agentes de forma mais fácil, assim como melhorar suas mensagens de sistema ao longo do tempo. É raro que você tenha uma mensagem de sistema que funcione perfeitamente na primeira tentativa para todo o seu caso de uso. Ser capaz de fazer pequenos ajustes e melhorias mudando a mensagem básica do sistema e rodando-a pelo sistema permitirá que você compare e avalie os resultados.

## Compreendendo Ameaças

Para construir agentes de IA confiáveis, é importante entender e mitigar os riscos e ameaças ao seu agente de IA. Vamos olhar apenas algumas das diferentes ameaças aos agentes de IA e como você pode se planejar e preparar melhor para elas.

![Compreendendo Ameaças](../../../translated_images/pt-BR/understanding-threats.89edeada8a97fc0f.webp)

### Tarefa e Instrução

**Descrição:** Atacantes tentam mudar as instruções ou metas do agente de IA através de prompts ou manipulando entradas.

**Mitigação**: Execute validações e filtros de entrada para detectar prompts potencialmente perigosos antes que sejam processados pelo Agente de IA. Como esses ataques normalmente requerem interações frequentes com o Agente, limitar o número de turnos numa conversa é outra forma de prevenir esses tipos de ataques.

### Acesso a Sistemas Críticos

**Descrição**: Se um agente de IA tem acesso a sistemas e serviços que armazenam dados sensíveis, atacantes podem comprometer a comunicação entre o agente e esses serviços. Isso pode ser ataques diretos ou tentativas indiretas de obter informações sobre esses sistemas através do agente.

**Mitigação**: Agentes de IA devem ter acesso aos sistemas somente conforme a necessidade, para evitar esses tipos de ataques. A comunicação entre o agente e o sistema também deve ser segura. Implementar autenticação e controle de acesso é outra forma de proteger essas informações.

### Sobrecarga de Recursos e Serviços

**Descrição:** Agentes de IA podem acessar diferentes ferramentas e serviços para completar tarefas. Atacantes podem usar essa habilidade para atacar esses serviços enviando um alto volume de requisições pelo Agente de IA, o que pode resultar em falhas do sistema ou custos elevados.

**Mitigação:** Implemente políticas para limitar o número de requisições que um agente de IA pode fazer a um serviço. Limitar o número de turnos de conversa e requisições ao seu agente de IA é outra forma de prevenir esses tipos de ataques.

### Envenenamento da Base de Conhecimento

**Descrição:** Este tipo de ataque não mira diretamente o agente de IA, mas a base de conhecimento e outros serviços que o agente de IA irá usar. Isso pode envolver corromper os dados ou informações que o agente de IA usará para completar uma tarefa, levando a respostas tendenciosas ou não intencionais ao usuário.

**Mitigação:** Realize verificações regulares dos dados que o agente de IA usará em seus fluxos de trabalho. Garanta que o acesso a esses dados seja seguro e que somente pessoas confiáveis possam alterá-los para evitar esse tipo de ataque.

### Erros em Cascata

**Descrição:** Agentes de IA acessam várias ferramentas e serviços para completar tarefas. Erros causados por atacantes podem levar a falhas em outros sistemas aos quais o agente está conectado, fazendo com que o ataque se torne mais amplo e difícil de solucionar.

**Mitigação**: Um método para evitar isso é fazer o Agente de IA operar em um ambiente limitado, como executar tarefas em um contêiner Docker, para prevenir ataques diretos ao sistema. Criar mecanismos de fallback e lógica de tentativas quando certos sistemas respondem com erro é outra forma de prevenir falhas maiores no sistema.

## Humano no Loop

Outra forma eficaz de construir sistemas de agentes de IA confiáveis é usando um Humano no loop. Isso cria um fluxo em que os usuários podem fornecer feedback aos Agentes durante a execução. Os usuários atuam essencialmente como agentes em um sistema multi-agentes, aprovando ou terminando o processo em execução.

![Humano no Loop](../../../translated_images/pt-BR/human-in-the-loop.5f0068a678f62f4f.webp)

Aqui está um trecho de código usando AutoGen para mostrar como esse conceito é implementado:

```python

# Crie os agentes.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Use input() para obter entrada do usuário no console.

# Crie a condição de término que encerrará a conversa quando o usuário disser "APPROVE".
termination = TextMentionTermination("APPROVE")

# Crie a equipe.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Execute a conversa e exiba no console.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Use asyncio.run(...) ao executar em um script.
await Console(stream)

```

## Conclusão

Construir agentes de IA confiáveis requer um design cuidadoso, medidas de segurança robustas e iteração contínua. Ao implementar sistemas estruturados de meta prompts, compreender ameaças potenciais e aplicar estratégias de mitigação, os desenvolvedores podem criar agentes de IA que sejam seguros e eficazes. Além disso, incorporar uma abordagem de humano no loop garante que os agentes de IA permaneçam alinhados com as necessidades do usuário enquanto minimizam riscos. À medida que a IA continua a evoluir, manter uma postura proativa sobre segurança, privacidade e considerações éticas será fundamental para fomentar confiança e confiabilidade em sistemas movidos por IA.

### Tem Mais Perguntas sobre Construir Agentes de IA Confiáveis?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar de office hours e obter respostas para suas perguntas sobre Agentes de IA.

## Recursos Adicionais

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Visão geral de IA Responsável</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Avaliação de modelos de IA generativa e aplicações de IA</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Mensagens de sistema para segurança</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Template de Avaliação de Riscos</a>

## Lição Anterior

[Agentic RAG](../05-agentic-rag/README.md)

## Próxima Lição

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se tradução profissional feita por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->