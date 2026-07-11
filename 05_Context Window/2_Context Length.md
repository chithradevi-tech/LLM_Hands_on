# Context Length

## What is Context Length?

**Context Length** is the **number of tokens the model can use or remember in a single request**.

It is essentially the **size of the model's context window**.

---

## Simple Definition

> **Context Length is the maximum number of tokens an LLM can process at one time.**

---

# Why is Context Length Important?

The model needs to remember:

* User prompt
* Previous conversation
* Retrieved documents (RAG)
* Code or files
* Instructions

All of these must fit within the **context length**.

---

# Example

Suppose an LLM has:

```text id="vgsbrk"
Context Length = 8,000 tokens
```

Your request contains:

| Content        | Tokens |
| -------------- | -----: |
| User Prompt    |  1,500 |
| Chat History   |  2,500 |
| RAG Documents  |  2,000 |
| Model Response |  2,000 |

Total:

```text id="zjlwm5"
1500 + 2500 + 2000 + 2000
=
8000 tokens
```

This fits within the context length.

---

# What Happens If You Exceed the Context Length?

Suppose:

```text id="xmtjlwm"
Context Length = 8,000 tokens
```

But your request contains:

```text id="odjlwm"
10,000 tokens
```

The model cannot process everything.

Possible outcomes:

* ❌ Older conversation is removed.
* ❌ Documents are truncated.
* ❌ Request is rejected.
* ❌ Response quality decreases because some context is lost.

---

# Flow Diagram

```text id="8rmjlwm"
Prompt
   │
   ▼
Conversation History
   │
   ▼
RAG Documents
   │
   ▼
Output Tokens
   │
   ▼
Total Tokens
   │
   ▼
Must Be ≤ Context Length
```

---

# Why is a Longer Context Length Better?

A larger context length allows the model to:

* ✅ Remember longer conversations.
* ✅ Read long PDFs and documents.
* ✅ Analyze large codebases.
* ✅ Improve RAG by using more retrieved context.
* ✅ Generate more coherent long responses.

---

# Real-Life Example

Imagine you have a notebook.

* 📒 Small notebook → Can store only a few pages.
* 📘 Large notebook → Can store many pages.

Similarly:

* Small context length → Less information remembered.
* Large context length → More information remembered.

---

# Applications

Long context lengths are useful for:

* 📄 Document summarization
* 📚 Book analysis
* 💻 Code generation
* 🤖 Long conversations
* 🔍 RAG applications
* 📑 Legal and research documents

---

# Context Length vs Context Window

| Context Length                                 | Context Window                       |
| ---------------------------------------------- | ------------------------------------ |
| Maximum number of tokens the model can process | Memory area that holds those tokens  |
| Measured in tokens                             | Also measured in tokens              |
| Defines the limit                              | Refers to the same limit in practice |

> **In modern LLMs, "Context Length" and "Context Window" are generally used interchangeably.**

---

> **Context Length is the maximum number of tokens an LLM can process in a single request. It includes the input prompt, conversation history, retrieved documents, and generated output. If the total tokens exceed the context length, the model may truncate older information or reject the request.**

---

# Easy Memory Trick

Imagine a whiteboard.

* 🖍️ The **whiteboard size** = **Context Length**
* 📝 The **notes you write** = **Tokens**

If the whiteboard is full, you must erase some notes before writing more.

Similarly:

```text id="jjlwm7"
Context Length
      =
Maximum Tokens
```

---

> **Context Length is the maximum number of tokens an LLM can process and remember in a single request.**
