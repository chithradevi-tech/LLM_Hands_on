# Context Window – Token Limits

## What is a Context Window?

A **Context Window** is the **maximum number of tokens** that an LLM can process at one time.

It includes:

* Your input (prompt)
* Conversation history
* Documents provided
* The model's generated output

---

## Simple Definition

> **The context window is the maximum number of tokens an LLM can remember and process in a single request.**

---

# What are Token Limits?

A **Token Limit** is the maximum number of tokens allowed within the model's context window.

For example:

```text
Context Window = 8,000 tokens
```

This means the **total** of:

* Input tokens
* Previous conversation
* Retrieved documents (RAG)
* Output tokens

must be **8,000 tokens or less**.

---

# Example

Suppose a model has:

```text
Context Window = 8,000 tokens
```

You send:

| Content       | Tokens |
| ------------- | -----: |
| Prompt        |  2,000 |
| Chat History  |  3,000 |
| RAG Documents |  2,000 |
| Output        |  1,000 |

Total:

```text
2000 + 3000 + 2000 + 1000
=
8000 tokens
```

This fits within the context window.

---

# What Happens If You Exceed the Limit?

Example:

```text
Context Window = 8,000
```

Request:

```text
Input = 9,000 tokens
```

The model **cannot process all tokens**.

Depending on the system, it may:

* ❌ Reject the request.
* ❌ Truncate (remove) older tokens.
* ❌ Summarize earlier conversation.
* ❌ Drop part of the retrieved documents.

---

# Flow Diagram

```text
User Prompt
      │
      ▼
Chat History
      │
      ▼
RAG Documents
      │
      ▼
Total Tokens
      │
      ▼
Must Be ≤ Context Window
      │
      ▼
LLM Processes Request
```

---

# Why is the Context Window Important?

A larger context window allows the model to:

* ✅ Remember longer conversations.
* ✅ Read larger documents.
* ✅ Handle long code files.
* ✅ Improve RAG by using more retrieved information.
* ✅ Answer questions with more context.

---

# Real-Life Example

Imagine your brain can remember only **10 pages** while reading a book.

If someone gives you:

* 📖 8 pages → You remember everything.
* 📖 20 pages → You may forget the earlier pages.

An LLM works similarly with its context window.

---

# Applications

A larger context window is useful for:

* 📄 Long document summarization
* 💻 Code generation and debugging
* 🤖 Chatbots with long conversations
* 📚 RAG applications
* 📑 Legal and medical document analysis

---


> **A context window is the maximum number of tokens an LLM can process in a single request. It includes the input prompt, conversation history, retrieved documents, and generated output. The token limit is determined by the model's context window, and if the total number of tokens exceeds this limit, some information may be truncated or the request may be rejected.**

---

# Easy Memory Trick

Imagine a **school bag**.

* 🎒 The bag = **Context Window**
* 📚 Books = **Tokens**

If the bag can hold **20 books**, you cannot put in **25 books**.

Similarly:

```text
Context Window
        =
Maximum Tokens
```

---


> **The context window is the maximum number of tokens an LLM can process at once, including the input, conversation history, retrieved context, and generated output.**
