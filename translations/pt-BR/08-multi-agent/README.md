[![Multi-Agente Design](../../../translated_images/pt-BR/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Clique na imagem acima para assistir ao vídeo desta lição)_

# Padrões de design multi-agente

Assim que você começar a trabalhar em um projeto que envolve múltiplos agentes, será necessário considerar o padrão de design multi-agente. No entanto, pode não estar imediatamente claro quando mudar para multi-agentes e quais são as vantagens.

## Introdução

Nesta lição, buscamos responder às seguintes perguntas:

- Quais são os cenários onde multi-agentes são aplicáveis?
- Quais são as vantagens de usar multi-agentes em vez de um único agente realizando múltiplas tarefas?
- Quais são os blocos de construção para implementar o padrão de design multi-agente?
- Como ter visibilidade de como os múltiplos agentes estão interagindo entre si?

## Objetivos de Aprendizagem

Após esta lição, você deve ser capaz de:

- Identificar cenários onde multi-agentes são aplicáveis
- Reconhecer as vantagens de usar multi-agentes em vez de um agente singular.
- Compreender os blocos de construção para implementar o padrão de design multi-agente.

Qual é o panorama geral?

*Multi-agentes são um padrão de design que permite que múltiplos agentes trabalhem juntos para alcançar um objetivo comum*.

Este padrão é amplamente usado em diversos campos, incluindo robótica, sistemas autônomos e computação distribuída.

## Cenários Onde Multi-Agentes São Aplicáveis

Então, quais cenários são um bom caso de uso para utilizar multi-agentes? A resposta é que existem muitos cenários onde empregar múltiplos agentes é benéfico, especialmente nos seguintes casos:

- **Grandes cargas de trabalho**: Grandes cargas de trabalho podem ser divididas em tarefas menores e atribuídas a diferentes agentes, permitindo processamento paralelo e conclusão mais rápida. Um exemplo disso é no caso de uma grande tarefa de processamento de dados.
- **Tarefas complexas**: Tarefas complexas, como grandes cargas de trabalho, podem ser divididas em subtarefas menores e atribuídas a diferentes agentes, cada um especializado em um aspecto específico da tarefa. Um bom exemplo disso é no caso de veículos autônomos onde diferentes agentes gerenciam navegação, detecção de obstáculos e comunicação com outros veículos.
- **Expertise diversa**: Diferentes agentes podem ter expertise diversa, permitindo que tratem diferentes aspectos de uma tarefa de forma mais eficaz do que um único agente. Para este caso, um bom exemplo é na área da saúde, onde agentes podem gerenciar diagnósticos, planos de tratamento e monitoramento de pacientes.

## Vantagens de Usar Multi-Agentes em Relação a um Agente Singular

Um sistema com um único agente pode funcionar bem para tarefas simples, mas para tarefas mais complexas, usar múltiplos agentes pode oferecer várias vantagens:

- **Especialização**: Cada agente pode ser especializado em uma tarefa específica. A falta de especialização em um único agente significa que você tem um agente que pode fazer tudo, mas pode ficar confuso quanto ao que fazer quando enfrenta uma tarefa complexa. Por exemplo, ele pode acabar realizando uma tarefa para a qual não é o mais adequado.
- **Escalabilidade**: É mais fácil escalar sistemas adicionando mais agentes do que sobrecarregando um único agente.
- **Tolerância a falhas**: Se um agente falhar, os outros podem continuar funcionando, garantindo a confiabilidade do sistema.

Vamos pegar um exemplo, vamos reservar uma viagem para um usuário. Um sistema com agente único teria que lidar com todos os aspectos do processo de reserva da viagem, desde encontrar voos até reservar hotéis e carros de aluguel. Para conseguir isso com um único agente, o agente precisaria ter ferramentas para lidar com todas essas tarefas. Isso poderia levar a um sistema complexo e monolítico que é difícil de manter e escalar. Um sistema multi-agente, por outro lado, poderia ter diferentes agentes especializados em encontrar voos, reservar hotéis e carros de aluguel. Isso tornaria o sistema mais modular, mais fácil de manter e escalável.

Compare isso com uma agência de viagens tradicional gerida por um pequeno negócio familiar versus uma agência de viagens gerida como uma franquia. O negócio familiar teria um único agente lidando com todos os aspectos do processo de reserva da viagem, enquanto a franquia teria diferentes agentes lidando com diferentes aspectos do processo de reserva da viagem.

## Blocos de Construção para Implementar o Padrão de Design Multi-Agente

Antes de você poder implementar o padrão de design multi-agente, é necessário entender os blocos de construção que compõem o padrão.

Vamos tornar isso mais concreto novamente olhando o exemplo de reservar uma viagem para um usuário. Nesse caso, os blocos de construção incluiriam:

- **Comunicação entre Agentes**: Agentes para encontrar voos, reservar hotéis e carros de aluguel precisam se comunicar e compartilhar informações sobre as preferências e restrições do usuário. Você precisa decidir os protocolos e métodos para essa comunicação. O que isso significa concretamente é que o agente para encontrar voos precisa se comunicar com o agente para reservar hotéis para garantir que o hotel seja reservado para as mesmas datas do voo. Isso significa que os agentes precisam compartilhar informações sobre as datas de viagem do usuário, ou seja, você precisa decidir *quais agentes estão compartilhando informações e como eles estão compartilhando*.
- **Mecanismos de Coordenação**: Os agentes precisam coordenar suas ações para garantir que as preferências e restrições do usuário sejam atendidas. Uma preferência do usuário pode ser que ele queira um hotel perto do aeroporto, enquanto uma restrição poderia ser que os carros de aluguel só estão disponíveis no aeroporto. Isso significa que o agente para reservar hotéis precisa coordenar com o agente para reservar carros de aluguel para garantir que as preferências e restrições do usuário sejam cumpridas. Isso significa que você precisa decidir *como os agentes coordenam suas ações*.
- **Arquitetura do Agente**: Os agentes precisam ter uma estrutura interna para tomar decisões e aprender com suas interações com o usuário. Isso quer dizer que o agente para encontrar voos precisa ter a estrutura interna para decidir quais voos recomendar ao usuário. Isso significa que você precisa decidir *como os agentes tomam decisões e aprendem com suas interações com o usuário*. Exemplos de como um agente aprende e melhora poderiam ser que o agente para encontrar voos poderia usar um modelo de aprendizado de máquina para recomendar voos ao usuário baseado em suas preferências passadas.
- **Visibilidade nas Interações Multi-Agentes**: Você precisa ter visibilidade de como os múltiplos agentes estão interagindo entre si. Isso significa que você precisa de ferramentas e técnicas para rastrear as atividades e interações dos agentes. Isso pode ser na forma de ferramentas de registro e monitoramento, ferramentas de visualização e métricas de desempenho.
- **Padrões Multi-Agente**: Existem diferentes padrões para implementar sistemas multi-agente, tais como arquiteturas centralizadas, descentralizadas e híbridas. Você precisa decidir o padrão que melhor se adequa ao seu caso de uso.
- **Humano no loop**: Na maioria dos casos, você terá um humano no loop e precisará instruir os agentes quando solicitar intervenção humana. Isso pode ocorrer na forma de um usuário pedindo um hotel ou voo específico que os agentes não recomendaram ou pedindo confirmação antes de reservar um voo ou hotel.

## Visibilidade nas Interações Multi-Agentes

É importante que você tenha visibilidade de como os múltiplos agentes estão interagindo entre si. Essa visibilidade é essencial para depuração, otimização e para garantir a eficácia geral do sistema. Para isso, você precisa de ferramentas e técnicas para rastrear as atividades e interações dos agentes. Isso pode ser na forma de ferramentas de registro e monitoramento, ferramentas de visualização e métricas de desempenho.

Por exemplo, no caso de reservar uma viagem para um usuário, você poderia ter um painel que mostre o status de cada agente, as preferências e restrições do usuário e as interações entre agentes. Esse painel poderia mostrar as datas de viagem do usuário, os voos recomendados pelo agente de voos, os hotéis recomendados pelo agente de hotéis e os carros de aluguel recomendados pelo agente de carros. Isso lhe daria uma visão clara de como os agentes estão interagindo e se as preferências e restrições do usuário estão sendo atendidas.

Vamos analisar cada um desses aspectos com mais detalhes.

- **Ferramentas de Registro e Monitoramento**: Você deseja que cada ação realizada por um agente seja registrada. Uma entrada de log poderia armazenar informações sobre o agente que realizou a ação, a ação realizada, o horário da ação e o resultado da ação. Essas informações podem então ser usadas para depuração, otimização e mais.

- **Ferramentas de Visualização**: As ferramentas de visualização podem ajudá-lo a ver as interações entre agentes de maneira mais intuitiva. Por exemplo, você poderia ter um gráfico que mostra o fluxo de informações entre os agentes. Isso poderia ajudá-lo a identificar gargalos, ineficiências e outros problemas no sistema.

- **Métricas de Desempenho**: Métricas de desempenho podem ajudá-lo a acompanhar a eficácia do sistema multi-agente. Por exemplo, você poderia monitorar o tempo para completar uma tarefa, o número de tarefas concluídas por unidade de tempo e a precisão das recomendações feitas pelos agentes. Essas informações podem ajudar a identificar áreas para melhoria e otimizar o sistema.

## Padrões Multi-Agente

Vamos explorar alguns padrões concretos que podemos usar para criar apps multi-agente. Aqui estão alguns padrões interessantes que valem a pena considerar:

### Bate-papo em grupo

Esse padrão é útil quando você quer criar um aplicativo de bate-papo em grupo onde múltiplos agentes podem se comunicar entre si. Casos de uso típicos para esse padrão incluem colaboração em equipe, suporte ao cliente e redes sociais.

Nesse padrão, cada agente representa um usuário no bate-papo em grupo, e as mensagens são trocadas entre agentes usando um protocolo de mensagens. Os agentes podem enviar mensagens para o grupo, receber mensagens do grupo e responder a mensagens de outros agentes.

Esse padrão pode ser implementado usando uma arquitetura centralizada onde todas as mensagens são roteadas por um servidor central, ou uma arquitetura descentralizada onde as mensagens são trocadas diretamente.

![Bate-papo em grupo](../../../translated_images/pt-BR/multi-agent-group-chat.ec10f4cde556babd.webp)

### Transferência de tarefa

Esse padrão é útil quando você quer criar um aplicativo onde múltiplos agentes podem transferir tarefas entre si.

Casos de uso típicos para esse padrão incluem suporte ao cliente, gerenciamento de tarefas e automação de fluxos de trabalho.

Nesse padrão, cada agente representa uma tarefa ou uma etapa em um fluxo de trabalho, e os agentes podem transferir tarefas para outros agentes baseados em regras predefinidas.

![Transferência de tarefa](../../../translated_images/pt-BR/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Filtragem colaborativa

Esse padrão é útil quando você quer criar um aplicativo onde múltiplos agentes podem colaborar para fazer recomendações aos usuários.

Por que você gostaria que múltiplos agentes colaborassem? Porque cada agente pode ter expertise diferente e pode contribuir para o processo de recomendação de maneiras diversas.

Vamos pegar um exemplo onde um usuário quer uma recomendação sobre a melhor ação para comprar no mercado de ações.

- **Especialista na indústria**: Um agente pode ser especialista em uma indústria específica.
- **Análise técnica**: Outro agente pode ser especialista em análise técnica.
- **Análise fundamentalista**: E outro agente pode ser especialista em análise fundamentalista. Colaborando, esses agentes podem fornecer uma recomendação mais abrangente para o usuário.

![Recomendação](../../../translated_images/pt-BR/multi-agent-filtering.d959cb129dc9f608.webp)

## Cenário: Processo de reembolso

Considere um cenário onde um cliente está tentando obter um reembolso por um produto, pode haver vários agentes envolvidos nesse processo, mas vamos dividir entre agentes específicos para esse processo e agentes gerais que podem ser usados em outros processos.

**Agentes específicos para o processo de reembolso**:

A seguir estão alguns agentes que poderiam estar envolvidos no processo de reembolso:

- **Agente do cliente**: Este agente representa o cliente e é responsável por iniciar o processo de reembolso.
- **Agente do vendedor**: Este agente representa o vendedor e é responsável por processar o reembolso.
- **Agente de pagamento**: Este agente representa o processo de pagamento e é responsável por reembolsar o pagamento do cliente.
- **Agente de resolução**: Este agente representa o processo de resolução e é responsável por resolver quaisquer problemas que surgirem durante o processo de reembolso.
- **Agente de conformidade**: Este agente representa o processo de conformidade e é responsável por garantir que o processo de reembolso esteja em conformidade com regulamentos e políticas.

**Agentes gerais**:

Estes agentes podem ser usados por outras partes do seu negócio.

- **Agente de envio**: Este agente representa o processo de envio e é responsável por enviar o produto de volta ao vendedor. Este agente pode ser usado tanto para o processo de reembolso quanto para o envio geral de um produto via compra, por exemplo.
- **Agente de feedback**: Este agente representa o processo de feedback e é responsável por coletar feedback do cliente. O feedback pode ser obtido a qualquer momento e não apenas durante o processo de reembolso.
- **Agente de escalonamento**: Este agente representa o processo de escalonamento e é responsável por escalar problemas para um nível superior de suporte. Você pode usar esse tipo de agente para qualquer processo onde seja necessário escalar um problema.
- **Agente de notificações**: Este agente representa o processo de notificações e é responsável por enviar notificações ao cliente em várias etapas do processo de reembolso.
- **Agente de análise**: Este agente representa o processo de análise e é responsável por analisar dados relacionados ao processo de reembolso.
- **Agente de auditoria**: Este agente representa o processo de auditoria e é responsável por auditar o processo de reembolso para garantir que está sendo realizado corretamente.
- **Agente de relatórios**: Este agente representa o processo de relatórios e é responsável por gerar relatórios sobre o processo de reembolso.
- **Agente de conhecimento**: Este agente representa o processo de conhecimento e é responsável por manter uma base de conhecimento de informações relacionadas ao processo de reembolso. Este agente poderia ser especialista tanto em reembolsos quanto em outras partes do seu negócio.
- **Agente de segurança**: Este agente representa o processo de segurança e é responsável por garantir a segurança do processo de reembolso.
- **Agente de qualidade**: Este agente representa o processo de qualidade e é responsável por assegurar a qualidade do processo de reembolso.

Há bastante agentes listados anteriormente, tanto para o processo específico de reembolso quanto para os agentes gerais que podem ser usados em outras partes do seu negócio. Esperamos que isso lhe dê uma ideia de como decidir quais agentes usar no seu sistema multi-agente.

## Tarefa

Projete um sistema multi-agente para um processo de suporte ao cliente. Identifique os agentes envolvidos no processo, seus papéis e responsabilidades, e como interagem entre si. Considere tanto agentes específicos para o processo de suporte ao cliente quanto agentes gerais que podem ser usados em outras partes do seu negócio.
> Pense um pouco antes de ler a solução a seguir, você pode precisar de mais agentes do que imagina.

> DICA: Pense sobre as diferentes etapas do processo de suporte ao cliente e também considere os agentes necessários para qualquer sistema.

## Solução

[Solução](./solution/solution.md)

## Verificações de conhecimento

Pergunta: Quando você deve considerar usar multiagentes?

- [ ] A1: Quando você tem uma carga de trabalho pequena e uma tarefa simples.
- [ ] A2: Quando você tem uma carga de trabalho grande
- [ ] A3: Quando você tem uma tarefa simples.

[Quiz da solução](./solution/solution-quiz.md)

## Resumo

Nesta lição, vimos o padrão de design multiagente, incluindo os cenários onde multiagentes são aplicáveis, as vantagens de usar multiagentes em vez de um agente singular, os blocos de construção para implementar o padrão de design multiagente e como ter visibilidade sobre como os múltiplos agentes estão interagindo entre si.

### Tem mais perguntas sobre o padrão de design Multiagente?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar de horários de atendimento e obter respostas para suas perguntas sobre Agentes de IA.

## Recursos adicionais

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Padrões de design AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Padrões de design agentic</a>


## Lição anterior

[Planejamento de Design](../07-planning-design/README.md)

## Próxima lição

[Metacognição em Agentes de IA](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos empenhemos para garantir a precisão, esteja ciente de que traduções automatizadas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->