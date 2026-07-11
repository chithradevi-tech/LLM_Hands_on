# LLM Architecture – Decoder-Only

## What is a Decoder-Only Architecture?

A **Decoder-Only** architecture uses **only the Decoder** part of the Transformer.

Its main job is to **generate text one token at a time**.

This is the architecture used by most modern **LLMs**.

---

## Simple Definition

> **A Decoder-Only model generates text by predicting one token at a time using the previous tokens as context.**

---

# How It Works

Example prompt:

```text
I love
```

The model predicts:

```text
I love AI
```

Then it predicts:

```text
I love AI because
```

Then:

```text
I love AI because it
```

The process continues until the response is complete.

---

# Architecture Diagram

```text
Input Prompt
      │
      ▼
Embedding Layer
      │
      ▼
Positional Encoding
      │
      ▼
Decoder Layers
(Masked Self-Attention + FFN)
      │
      ▼
Linear Layer
      │
      ▼
Softmax
      │
      ▼
Next Token
      │
      ▼
Repeat
```

---

# Key Features

* ✅ Uses only the **Decoder**.
* ✅ Uses **Masked (Causal) Self-Attention**.
* ✅ Generates one token at a time.
* ✅ Cannot see future tokens.
* ✅ Excellent for text generation.

---

# Why Masked (Causal) Attention?

Suppose the sentence is:

```text
I love AI
```

When predicting **"AI"**, the model can see only:

```text
I
love
```

It **cannot** see:

```text
AI
```

before predicting it.

This prevents the model from "cheating."

---

# Generation Process

Suppose the prompt is:

```text
The cat
```

### Step 1

Input:

```text
The cat
```

↓

Predict:

```text
sat
```

---

### Step 2

Now input becomes:

```text
The cat sat
```

↓

Predict:

```text
on
```

---

### Step 3

Now input becomes:

```text
The cat sat on
```

↓

Predict:

```text
the
```

This continues until the model predicts an end-of-sequence token or reaches the maximum output length.

---

# Applications

Decoder-only models are used for:

* ✅ Chatbots
* ✅ Text Generation
* ✅ Code Generation
* ✅ Story Writing
* ✅ Content Creation
* ✅ Question Answering
* ✅ AI Assistants

---

# Popular Decoder-Only Models

Examples include:

* GPT-2
* GPT-3
* Llama
* Gemma

---

# Advantages

* ✅ Excellent at generating fluent text.
* ✅ Supports long conversations.
* ✅ Great for code generation.
* ✅ Simple architecture compared to Encoder–Decoder models.
* ✅ Most modern LLMs use this design.

---

# Disadvantages

* ❌ Mainly optimized for generation rather than deep bidirectional understanding.
* ❌ Generates tokens sequentially, so output generation is slower than processing the entire sequence in parallel.

---

# Encoder-Only vs Decoder-Only

| Encoder-Only                     | Decoder-Only                   |
| -------------------------------- | ------------------------------ |
| Understands text                 | Generates text                 |
| Bidirectional Self-Attention     | Masked (Causal) Self-Attention |
| Reads the whole sentence at once | Generates one token at a time  |
| Example: BERT                    | Example: GPT, Llama            |

---

> **A Decoder-Only Transformer uses only the decoder part of the Transformer architecture. It generates text one token at a time using masked (causal) self-attention, where each token can attend only to previous tokens. This architecture is ideal for autoregressive text generation and is used in modern LLMs such as GPT, Llama, and Gemma.**

---

# Easy Memory Trick

Imagine writing a sentence on paper.

You write:

```text
I
```

↓

Then:

```text
I love
```

↓

Then:

```text
I love AI
```

You can only use the words you've already written—you cannot look at future words.

That's exactly how a **Decoder-Only Transformer** works.

```text
Previous Tokens
        │
        ▼
Masked Self-Attention
        │
        ▼
Predict Next Token
        │
        ▼
Repeat
```

---

> **A Decoder-Only Transformer generates text autoregressively by predicting one token at a time using masked (causal) self-attention.**
