[![Planning Design Pattern](../../../translated_images/bn/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(এই পাঠটির ভিডিও দেখতে উপরের ছবিতে ক্লিক করুন)_

# পরিকল্পনা ডিজাইন

## পরিচিতি

এই পাঠে আলোচনা করা হবে

* একটি স্পষ্ট সামগ্রিক লক্ষ্য চিহ্নিতকরণ এবং একটি জটিল কাজকে পরিচালনাযোগ্য কাজগুলিতে ভাগ করা।
* আরও বিশ্বাসযোগ্য এবং মেশিন-পাঠযোগ্য প্রতিক্রিয়ার জন্য সজ্জিত আউটপুট ব্যবহার।
* গতিশীল কাজ এবং অপ্রত্যাশিত ইনপুট হ্যান্ডেল করার জন্য একটি ইভেন্ট-ড্রিভেন পদ্ধতি প্রয়োগ করা।

## শেখার লক্ষ্য

এই পাঠ শেষ করার পরে, আপনি নিম্নলিখিত বিষয়গুলি সম্পর্কে ধারণা লাভ করবেন:

* একটি কৃত্রিম বুদ্ধিমত্তা এজেন্টের জন্য একটি সামগ্রিক লক্ষ্য নির্ধারণ করা এবং সেট করা, নিশ্চিত করা যে এটি স্পষ্টভাবে জানে কি অর্জন করতে হবে।
* একটি জটিল কাজকে পরিচালনাযোগ্য উপকাজে বিভক্ত করা এবং সেগুলোকে একটি যুক্তিযুক্ত ক্রমে সংগঠিত করা।
* এজেন্টদের সঠিক সরঞ্জাম (যেমন, অনুসন্ধান সরঞ্জাম বা ডেটা বিশ্লেষণ সরঞ্জাম) দিয়ে সজ্জিত করা, তারা কখন এবং কীভাবে ব্যবহার হবে তা নির্ধারণ করা, এবং উদ্ভূত অপ্রত্যাশিত পরিস্থিতি মোকাবেলা করা।
* উপকাজের ফলাফল মূল্যায়ন করা, কর্মক্ষমতা মাপা, এবং চূড়ান্ত আউটপুট উন্নত করার জন্য পদক্ষেপ পুনরাবৃত্তি করা।

## সামগ্রিক লক্ষ্য নির্ধারণ ও কাজ বিভাজন

![Defining Goals and Tasks](../../../translated_images/bn/defining-goals-tasks.d70439e19e37c47a.webp)

অধিকাংশ বাস্তব বিশ্বের কাজ একক ধাপে মোকাবেলা করার তুলনায় অত্যন্ত জটিল। একটি AI এজেন্টের কাছে তার পরিকল্পনা এবং কার্যাবলী পরিচালনার জন্য একটি সংক্ষিপ্ত উদ্দেশ্য থাকা প্রয়োজন। উদাহরণস্বরূপ, লক্ষ্য বিবেচনা করুন:

    "৩ দিনের একটি ভ্রমণ সূচি তৈরি করুন।"

যদিও এটি সহজে বলা যায়, তবুও এটি সূক্ষ্মতার প্রয়োজন। যত পরিষ্কার লক্ষ্য হবে, তত ভাল এজেন্ট (এবং যেকোনো মানব সহযোগী) সঠিক ফলাফল অর্জনে মনোযোগী হতে পারবে, যেমন একটি পূর্ণাঙ্গ সূচিতে বিমান বিকল্প, হোটেল সুপারিশ এবং কার্যক্রমের পরামর্শ তৈরি করা।

### কাজ বিভাজন

বড় বা জটিল কাজ ছোট, লক্ষ্যনির্দিষ্ট উপকাজে বিভক্ত হলে তা আরো সহজে পরিচালনাযোগ্য হয়।
ভ্রমণ সূচি উদাহরণে, লক্ষ্যটি বিভাজন করা যেতে পারে:

* বিমান বুকিং
* হোটেল বুকিং
* গাড়ি ভাড়া
* ব্যক্তিগতকরণ

প্রতিটি উপকাজ তারপর নির্দিষ্ট এজেন্ট বা প্রক্রিয়ার মাধ্যমে মোকাবেলা করা যেতে পারে। একজন এজেন্ট সবচেয়ে ভালো বিমান দরের সন্ধান দিতে পারেন, অন্য একজন হোটেল বুকিংয়ে মনোনিবেশ করেন, এবং সুতরাং। এক সচল বা “ডাউনস্ট্রীম” এজেন্ট এই ফলাফলগুলি একত্রিত করে চূড়ান্ত ইউজারের জন্য একটি সঙ্গতিপূর্ণ সূচি তৈরি করতে পারে।

এই মডুলার পদ্ধতি এছাড়াও ক্রমবর্ধমান উন্নতির সুযোগ দেয়। উদাহরণস্বরূপ, আপনি খাবারের সুপারিশ বা স্থানীয় কার্যক্রমের পরামর্শের জন্য বিশেষায়িত এজেন্ট যুক্ত করতে পারেন এবং সময়ের সাথে সূচি উন্নত করতে পারেন।

### সজ্জিত আউটপুট

বড় ভাষার মডেলগুলি (LLMs) সজ্জিত আউটপুট (যেমন JSON) তৈরি করতে পারে যা ডাউনস্ট্রীম এজেন্ট বা সেবাগুলোর জন্য বিশ্লেষণ এবং প্রক্রিয়াকরণ সহজ করে তোলে। এটি বিশেষ করে বহু-এজেন্ট প্রেক্ষাপটে কার্যকর, যেখানে আমরা পরিকল্পনার ফলাফল প্রাপ্তির পরে কাজগুলো সম্পাদন করতে পারি। দ্রুত ধারণার জন্য এই <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">ব্লগপোস্ট</a> দেখুন।

নিচের পাইথন কোড স্নিপেট একটি সরল পরিকল্পনাকারী এজেন্টকে একটি লক্ষ্যকে উপকাজে বিভক্ত করে এবং একটি সজ্জিত পরিকল্পনা তৈরি করতে দেখায়:

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

# ট্রাভেল সাবটাস্ক মডেল
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # আমরা এজেন্টকে কাজটি দিতে চাই

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # মডেলের সাথে প্রমাণীকরণের জন্য আপনাকে আপনার GitHub সেটিংস-এ একটি পার্সোনাল অ্যাকসেস টোকেন (PAT) তৈরি করতে হবে।
    # এখানে নির্দেশনাগুলি অনুসরণ করে আপনার PAT টোকেন তৈরি করুন: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# ব্যবহারকারীর বার্তা সংজ্ঞায়িত করুন
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

# # লোড করার আগে নিশ্চিত করুন যে রেসপন্সের বিষয়বস্তু একটি বৈধ JSON স্ট্রিং
# response_content: Optional[str] = response.content যদি isinstance(
#     response.content, str) হয় তাহলে else None
# যদি response_content None হয়:
#     ValueError তোলুন("রেসপন্সের বিষয়বস্তু একটি বৈধ JSON স্ট্রিং নয়")

# # JSON হিসাবে লোড করার পর রেসপন্স বিষয়বস্তু প্রিন্ট করুন
# pprint(json.loads(response_content))

# MathReasoning মডেল দিয়ে রেসপন্স বিষয়বস্তু যাচাই করুন
# TravelPlan.model_validate(json.loads(response_content))
```

### বহু-এজেন্ট সমন্বয়ে পরিকল্পনাকারী এজেন্ট

এই উদাহরণে, একটি সেমান্টিক রাউটার এজেন্ট একটি ব্যবহারকারীর অনুরোধ পায় (যেমন, "আমার যাত্রার জন্য একটি হোটেল পরিকল্পনা দরকার।")।

পরিকল্পনাকারী তারপর:

* হোটেল পরিকল্পনা গ্রহণ করে: পরিকল্পনাকারী ব্যবহারকারীর বার্তা গ্রহণ করে এবং একটি সিস্টেম প্রম্পট (যার মধ্যে উপলব্ধ এজেন্ট বিবরণ অন্তর্ভুক্ত) অনুযায়ী একটি সজ্জিত ট্র্যাভেল পরিকল্পনা তৈরি করে।
* এজেন্ট এবং তাদের সরঞ্জামের তালিকা তৈরি করে: এজেন্ট রেজিস্ট্রি এজেন্টদের একটি তালিকা রাখে (যেমন, বিমান, হোটেল, গাড়ি ভাড়া, এবং কার্যক্রম) সহ তাদের সরবরাহ করা ফাংশন বা সরঞ্জামসহ।
* পরিকল্পনা প্রাসঙ্গিক এজেন্টদের কাছে রুট করে: উপকাজের সংখ্যার উপর নির্ভর করে, পরিকল্পনাকারী বার্তাটি সরাসরি একটি নির্ধারিত এজেন্টকে পাঠায় (একক কাজের জন্য) অথবা বহু-এজেন্ট সহযোগিতার জন্য একটি গ্রুপ চ্যাট ম্যানেজারের মাধ্যমে সমন্বয় করে।
* ফলাফল সারাংশ করে: শেষমেশ, পরিষ্কারতার জন্য পরিকল্পনাটি সারাংশ করা হয়।
নিচের পাইথন কোড নমুনা এই ধাপগুলো দেখায়:

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

# ট্রাভেল সাবটাস্ক মডেল

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # আমরা এজেন্টকে কাজটি নির্ধারণ করতে চাই

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# টাইপ-চেকড পরিবেশ ভেরিয়েবল সহ ক্লায়েন্ট তৈরি করুন

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# ব্যবহারকারীর বার্তা নির্ধারণ করুন

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

# লোড করার আগে নিশ্চিত করুন যে প্রতিক্রিয়ার বিষয়বস্তু একটি বৈধ JSON স্ট্রিং

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# JSON হিসাবে লোড করার পরে প্রতিক্রিয়ার বিষয়বস্তু প্রিন্ট করুন

pprint(json.loads(response_content))
```

পরবর্তী কোডটির ফলাফল হলো এই আউটপুট এবং আপনি এটি ব্যবহার করে `assigned_agent` এ রুট করতে এবং ব্যবহারকারীর কাছে ভ্রমণ পরিকল্পনা সারাংশ করতে পারবেন।

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

আগের কোড নমুনার একটি উদাহরণ নোটবুক পাওয়া যাবে [এখানে](07-autogen.ipynb)।

### পুনরাবৃত্তিমূলক পরিকল্পনা

কিছু কাজ ধাপে ধাপে বা পুনরায় পরিকল্পনা প্রয়োজন, যেখানে একটি উপকাজের ফলাফল পরবর্তীটি প্রভাবিত করে। উদাহরণস্বরূপ, যদি এজেন্ট বিমান বুকিংয়ের সময় অপ্রত্যাশিত ডেটা ফর্ম্যাট আবিষ্কার করে, তবে হোটেল বুকিংয়ের আগে তার কৌশল পরিবর্তন করতে হতে পারে।

অতিরিক্তভাবে, ব্যবহারকারীর প্রতিক্রিয়া (যেমন, একজন মানুষ আগে বিমানের পছন্দ নির্ধারণ করলে) আংশিক পুনঃপরিকল্পনার সূচনা করতে পারে। এই গতিশীল, পুনরাবৃত্তিমূলক পদ্ধতি নিশ্চিত করে যে চূড়ান্ত সমাধান বাস্তব সীমাবদ্ধতা এবং পরিবর্তিত ব্যবহারকারীর পছন্দের সাথে সামঞ্জস্যপূর্ণ থাকে।

উদাহরণস্বরূপ কোড:

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. আগের কোডের মতোই এবং ব্যবহারকারীর ইতিহাস, বর্তমান পরিকল্পনা পাঠান
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
# .. পুনঃপরিকল্পনা করুন এবং সংশ্লিষ্ট এজেন্টদের কাছে কাজগুলি পাঠান
```

আরও বিস্তৃত পরিকল্পনার জন্য <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Magnetic One ব্লগপোস্ট</a> দেখুন, যা জটিল কাজ সমাধানের জন্য একটি সাধারণ বহু-এজেন্ট সিস্টেম।

## সারাংশ

এই প্রবন্ধে আমরা একটি উদাহরণ দেখেছি কিভাবে আমরা একটি পরিকল্পনাকারী তৈরি করতে পারি যা ডাইনামিক্যালি উপলব্ধ সংজ্ঞায়িত এজেন্টগুলো নির্বাচন করে। পরিকল্পনাকারীর আউটপুট কাজগুলো বিভাজন করে এবং এজেন্টদের অ্যাসাইন করে যাতে সেগুলো কার্যকর করা যায়। অনুমান করা হয় যে এজেন্টরা কাজটি পরিচালনার জন্য প্রয়োজনীয় ফাংশন/সরঞ্জাম অ্যাক্সেস করতে পারে। এজেন্ট ছাড়াও আপনি প্রতিফলন, সারাংশকারী এবং রাউন্ড রবিন চ্যাটের মতো অন্যান্য প্যাটার্ন অন্তর্ভুক্ত করতে পারেন কাস্টমাইজেশন বাড়ানোর জন্য।

## অতিরিক্ত রিসোর্স

AutoGen Magnetic One - জটিল কাজ সমাধানের জন্য একটি সাধারণ বহু-এজেন্ট সিস্টেম যা বহু চ্যালেঞ্জিং এজেন্টিক বেঞ্চমার্কে চমৎকার ফলাফল অর্জন করেছে। রেফারেন্স: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>। এই বাস্তবায়নে, অর্কেস্ট্রেটর টাস্ক-নির্দিষ্ট পরিকল্পনা তৈরি করে এবং উপলব্ধ এজেন্টদের কাছে কাজগুলো হস্তান্তর করে। পরিকল্পনার পাশাপাশি অর্কেস্ট্রেটর একটি ট্র্যাকিং পদ্ধতি ব্যবহার করে কাজের অগ্রগতি মনিটার করে এবং প্রয়োজন অনুযায়ী পুনরায় পরিকল্পনা করে।

### পরিকল্পনা ডিজাইন প্যাটার্ন সম্পর্কে আরও প্রশ্ন আছে?

অন্য শিক্ষার্থীদের সাথে আলাপ করতে, অফিস আওয়ারে যেতে এবং আপনার AI এজেন্টদের প্রশ্নের উত্তর পেতে [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)-এ যোগ দিন।

## আগের পাঠ

[বিশ্বাসযোগ্য AI এজেন্ট তৈরি](../06-building-trustworthy-agents/README.md)

## পরবর্তী পাঠ

[বহু-এজেন্ট ডিজাইন প্যাটার্ন](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**অস্বীকারোক্তি**:
এই ডকুমেন্টটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা সঠিকতার জন্য চেষ্টা করি, তবে দয়া করে জানুন যে স্বয়ংক্রিয় অনুবাদে ভুল বা অসংগতি থাকতে পারে। সংশ্লিষ্ট মূল ভাষার ডকুমেন্টটিকেই কর্তৃত্বপূর্ণ উৎস হিসেবে গণ্য করা উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদ গ্রহণ করা সুপারিশ করা হয়। এই অনুবাদের ব্যবহারে সৃষ্ট কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়বদ্ধ নই।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->