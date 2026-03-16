[![Planning Design Pattern](../../../translated_images/pcm/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Click di image wey dey above to watch video for dis lesson)_

# Planning Design

## Introduction

Dis lesson go cover

* How to define clear overall goal and break big work into small, manageable work.
* How to use structured output for better and machine-readable answers.
* How to use event-driven way to handle dynamic work and surprise inputs.

## Learning Goals

After you finish dis lesson, you go sabi about:

* How to find and set overall goal for AI agent, make e clear wetin e want achieve.
* How to break big work into small tasks and arrange dem well.
* How to give agents correct tools (e.g., search tools or data analysis tools), decide when and how to use dem, and handle surprise wahala.
* How to check subtask results, measure how e perform, and improve actions to make final result better.

## Defining the Overall Goal and Breaking Down a Task

![Defining Goals and Tasks](../../../translated_images/pcm/defining-goals-tasks.d70439e19e37c47a.webp)

Most real-life work too complex to do one time. AI agent need clear objective to guide plan and actions. For example, check dis goal:

    "Generate a 3-day travel itinerary."

E simple to talk but still need more detail. If goal clear well, agent (and any human wey dey work with am) fit focus well to get correct result, like make full itinerary wey get flight choices, hotel recommendations, and activity ideas.

### Task Decomposition

Big or complex work go easier if you divide am into smaller, clear tasks.
For travel itinerary example, you fit break goal into:

* Flight Booking
* Hotel Booking
* Car Rental
* Personalization

Each task fit be handled by special agents or processes. One agent fit focus on searching best flight deals, another fit arrange hotel booking, and so on. One agent wey dey coordinate or “downstream” fit gather all results combine am into one full itinerary for customer.

Dis method also allow small improvements little by little. For example, you fit add special agents for Food Recommendations or Local Activity Ideas and improve itinerary later.

### Structured output

Large Language Models (LLMs) fit create structured output (like JSON) wey easy for downstream agents or services to understand and handle. This important especially for multi-agent work, where we fit do these tasks after we get plan. Check dis <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogpost</a> for quick overview.

Below Python snippet show how simple planning agent break goal into tasks and create structured plan:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Travel SubTask Model
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # we wan assign di task to di agent

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # To authenticate wit di model you go need generate your own personal access token (PAT) for your GitHub settings.
    # Make your PAT token by following di instructions here: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Define di user message
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Make sure say di response content na correct JSON string before you load am
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content no dey:
#     raise ValueError("Response content no be correct JSON string")

# # Print di response content after you don load am as JSON
# pprint(json.loads(response_content))

# Check di response content with di MathReasoning model
# TravelPlan.model_validate(json.loads(response_content))
```

### Planning Agent with Multi-Agent Orchestration

For dis example, Semantic Router Agent dey receive user message (e.g., "I need a hotel plan for my trip.").

Planner then:

* Receive Hotel Plan: Planner take user message and based on system prompt (with info on available agents), e make structured travel plan.
* List Agents and Their Tools: Agent list get agents (for flight, hotel, car rental, activity) and tools or functions dem get.
* Send Plan to Right Agents: Based on how many subtasks, planner either send message straight to one agent (if one task) or manage group chat for many agents.
* Summarize Outcome: Lastly, planner summarize plan to make am clear.
Below Python code show these steps:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Travel SubTask Model

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # we wan assign di task to di agent

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Make di client wit type-checked environment variables

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Define di user message

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Make sure di response content na correct JSON string before you load am

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Print di response content after you don load am as JSON

pprint(json.loads(response_content))
```

Wetin follow na output from previous code and you fit use this structured output to send to `assigned_agent` and summarize travel plan for end user.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Example notebook with previous code dey available [here](07-autogen.ipynb).

### Iterative Planning

Some tasks need go back and forth or redo plan, because result from one subtask fit affect next one. For example, if agent find surprise data format while booking flights, e go need change plan before e start hotel booking.

Also, user feedback (e.g. human say dem want earlier flight) fit cause partial re-plan. Dis dynamic, repeating method make sure final plan match real-life condition and changing user taste.

Example code

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. di same as di code before and carry go di user history, current plan
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. re-plan and send di tasks go di correct agents
```

For better planning, check Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> wey dey talk about solving complex work.

## Summary

For dis article we don see example of how to make planner wey fit dynamically choose available agents. Planner output dey break tasks and assign agents so dem fit do am. We assume say agents fit use functions/tools wey dem need for work. Besides agents, you fit add other patterns like reflection, summarizer, and round robin chat to customize more.

## Additional Resources

AutoGen Magnetic One - Generalist multi-agent system wey fit solve complex tasks and don get better results for many hard agent tests. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. For this system, orchestrator dey create task plan and assign task to available agents. Other than planning, orchestrator still dey track how work dey go and fit redo plan if e need.

### You Get More Questions About Planning Design Pattern?

Come join [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet other learners, attend office hours and get answer for your AI Agents questions.

## Previous Lesson

[Building Trustworthy AI Agents](../06-building-trustworthy-agents/README.md)

## Next Lesson

[Multi-Agent Design Pattern](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dis document don translate wit AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). Even though we try make e accurate, abeg sabi say automated translation fit get errors or mistakes. Di original document for dia own language na di correct one wey you suppose use. If na important info, better make human professional translate am. We no go hold ourselves responsible for any wahala or wrong understand wey fit happen because you use dis translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->