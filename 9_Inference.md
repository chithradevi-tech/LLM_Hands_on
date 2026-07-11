# Inference

## What is Inference?

**Inference** is the process of **using a trained LLM to generate predictions or responses** for new input.

Unlike training, **the model does not learn or update its weights** during inference. It only uses the knowledge it has already learned.

---

## Simple Definition

> **Inference is the process of using a trained LLM to generate an answer for a user's input.**

---

# Example

User Prompt:

```text
What is Artificial Intelligence?
```

↓

The trained LLM processes the prompt.

↓

Response:

```text
Artificial Intelligence (AI) is the simulation of human intelligence by machines.
```

This entire process is called **Inference**.

---

# How Inference Works

### Step 1: User Input

```text
Explain Machine Learning.
```

↓

### Step 2: Tokenization

```text
["Explain", "Machine", "Learning"]
```

↓

### Step 3: Embeddings

Each token is converted into vectors.

↓

### Step 4: Transformer Processing

The model uses:

* Self-Attention
* Feed Forward Networks
* Layer Normalization

to understand the input.

↓

### Step 5: Predict Next Token

Example:

```text
Machine Learning is
```

↓

Predict:

```text
a
```

↓

Then:

```text
Machine Learning is a
```

↓

Predict:

```text
field
```

The model continues predicting **one token at a time** until the response is complete.

---

# Inference Flow

```text
User Prompt
      │
      ▼
Tokenization
      │
      ▼
Embeddings
      │
      ▼
Transformer
      │
      ▼
Predict Next Token
      │
      ▼
Generate Response
```

---

# Training vs Inference

| Training                                   | Inference                                |
| ------------------------------------------ | ---------------------------------------- |
| Teaches the model                          | Uses the trained model                   |
| Updates model weights                      | Does **not** update weights              |
| Uses loss and backpropagation              | No loss or backpropagation               |
| Very time-consuming                        | Much faster                              |
| Done once (or occasionally for retraining) | Happens every time a user sends a prompt |

---

# What Happens During Inference?

During inference, the model:

* ✅ Reads the input prompt.
* ✅ Converts it into tokens.
* ✅ Processes the tokens through the Transformer.
* ✅ Predicts the next token.
* ✅ Repeats until the response is complete.
* ❌ Does not learn new information or change its parameters.

---

# Optimization Techniques Used During Inference

To make inference faster and more efficient:

* ✅ **KV Cache** – Reuses previously computed Key and Value vectors.
* ✅ **Quantization** – Reduces model size and memory usage.
* ✅ **Batching** – Processes multiple requests together.
* ✅ **Speculative Decoding** – Speeds up token generation by using a smaller draft model (in supported systems).

---

# Applications

Inference is used in:

* 🤖 Chatbots
* 💻 Code Generation
* 🌐 Language Translation
* 📄 Document Summarization
* 🔍 Semantic Search
* 🎙️ AI Assistants
* 📧 Email Generation

---

> **Inference is the process of using a trained LLM to generate predictions or responses for new input. During inference, the model tokenizes the input, converts it into embeddings, processes it through the Transformer, and predicts the next token one at a time. Unlike training, inference does not update the model's weights or use backpropagation.**

---

# Easy Memory Trick

Imagine a student:

* **Training** → The student studies and learns.
* **Inference** → The student writes the exam using what they already know.

During the exam:

* ❌ They don't learn new chapters.
* ✅ They simply answer the questions.

Similarly:

```text
Training → Learn 📚

Inference → Answer ✍️
```

---

> **Inference is the process of using a trained LLM to generate responses for new inputs without updating the model's weights.**
