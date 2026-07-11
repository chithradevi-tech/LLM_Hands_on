# Function / Tool Calling

## What is Function Calling (Tool Calling)?

**Function Calling** (also called **Tool Calling**) is a feature that allows an **LLM to interact with external tools, APIs, databases, or applications** to perform tasks beyond just generating text.

Instead of only answering from its internal knowledge, the LLM can **call a function**, get real data, and then generate the final response.

---

## Simple Definition

> **Function (Tool) Calling allows an LLM to use external tools or APIs to perform real-world tasks and return accurate results.**

---

# Why Do We Need Function Calling?

LLMs **cannot**:

* Check live weather by themselves.
* Book a flight.
* Query a database.
* Send an email.
* Call an API.

They need **external tools** to perform these actions.

---

# Example

User asks:

```text
What's the weather in Chennai today?
```

Instead of guessing, the LLM:

1. Detects that weather information is needed.
2. Calls a Weather API.
3. Receives the latest weather.
4. Responds to the user.

---

# How Function Calling Works

### Step 1: User Prompt

```text
Book a hotel in Bangalore.
```

↓

### Step 2: LLM Understands the Intent

The model recognizes that a **hotel booking tool** is required.

↓

### Step 3: Call the Function

```python
book_hotel(
    city="Bangalore",
    check_in="2026-07-20",
    check_out="2026-07-22"
)
```

↓

### Step 4: Tool Executes

The booking system returns:

```text
Booking Successful
```

↓

### Step 5: LLM Responds

```text
Your hotel has been booked successfully.
```

---

# Flow Diagram

```text
User
 │
 ▼
LLM
 │
 ▼
Need Tool?
 │
 ├── No ──► Answer Directly
 │
 └── Yes
      │
      ▼
Function / API Call
      │
      ▼
Receive Result
      │
      ▼
Generate Final Response
```

---

# Real-Life Example

User:

```text
What is my bank balance?
```

LLM:

❌ Doesn't know your balance.

↓

Calls:

```text
Bank API
```

↓

API returns:

```text
₹25,000
```

↓

LLM replies:

```text
Your current account balance is ₹25,000.
```

---

# Common Tools Used with LLMs

| Tool            | Purpose                   |
| --------------- | ------------------------- |
| Weather API     | Current weather           |
| Google Maps API | Location and directions   |
| Calendar API    | Schedule meetings         |
| Email API       | Send emails               |
| Database        | Retrieve user information |
| Calculator      | Perform calculations      |
| Search Engine   | Get latest information    |
| SQL Database    | Execute SQL queries       |

---

# Applications

Function Calling is used in:

* ✅ AI Chatbots
* ✅ AI Agents
* ✅ Customer Support
* ✅ RAG Applications
* ✅ Travel Booking
* ✅ Banking Assistants
* ✅ Healthcare Systems
* ✅ Smart Home Automation

---

# Advantages

* ✅ Accesses real-time information.
* ✅ Connects with external systems.
* ✅ Automates tasks.
* ✅ Makes AI assistants more powerful.

---

# Limitations

* ❌ Depends on external APIs/tools.
* ❌ API failures can affect responses.
* ❌ Requires proper authentication and permissions.
* ❌ Tool responses must be validated.

---

# Function Calling vs RAG

| Function Calling                             | RAG                                        |
| -------------------------------------------- | ------------------------------------------ |
| Executes actions using external tools        | Retrieves relevant documents               |
| Calls APIs or databases                      | Searches a knowledge base/vector database  |
| Can book tickets, send emails, check weather | Answers questions from retrieved documents |
| Performs tasks                               | Retrieves information                      |

---

> **Function Calling, also known as Tool Calling, enables an LLM to interact with external tools, APIs, databases, or services. When the model detects that a user's request requires external information or an action, it calls the appropriate function, receives the result, and uses that result to generate the final response. This allows LLMs to perform real-world tasks such as checking weather, querying databases, booking appointments, or sending emails.**

---

# Easy Memory Trick

Imagine a **restaurant waiter**.

* 🍽️ Customer places an order.
* 🧑‍🍳 The waiter **doesn't cook** the food.
* The waiter goes to the **kitchen (tool)**.
* The kitchen prepares the food.
* The waiter brings it back to the customer.

Similarly:

```text
User Request
      │
      ▼
LLM
      │
      ▼
Tool / API
      │
      ▼
Result
      │
      ▼
LLM Response
```

The **LLM is like the waiter**, and the **tool/API is like the kitchen**.

---

> **Function (Tool) Calling allows an LLM to invoke external APIs or tools to retrieve real-time information or perform actions, then use the results to generate an accurate response.**
