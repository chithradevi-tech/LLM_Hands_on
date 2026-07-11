# LLM Architecture – Encoder–Decoder

## What is an Encoder–Decoder Architecture?

An **Encoder–Decoder** architecture uses **both the Encoder and the Decoder** of the Transformer.

* **Encoder** → Understands the input.
* **Decoder** → Generates the output.

It is mainly used for **sequence-to-sequence (Seq2Seq)** tasks such as translation and summarization.

---

## Simple Definition

> **An Encoder–Decoder model first understands the input using the Encoder and then generates the output step by step using the Decoder.**

---

# How It Works

Example:

Input:

```text
English:
I love AI
```

↓

Encoder understands the sentence.

↓

Decoder generates:

```text
French:
J'aime l'IA
```

The Decoder uses:

* The previous generated tokens
* The Encoder's output (through **Cross-Attention**)

---

# Architecture Diagram

```text
              Input Sentence
              "I love AI"
                    │
                    ▼
           Embedding + Position
                    │
                    ▼
              ┌────────────┐
              │  Encoder   │
              └────────────┘
                    │
      Contextual Embeddings
                    │
                    ▼
              ┌────────────┐
              │  Decoder   │
              └────────────┘
                    │
            Linear + Softmax
                    │
                    ▼
            Output Sentence
          "J'aime l'IA"
```

---

# Encoder Components

Each encoder layer contains:

```text
Embedding
      │
      ▼
Positional Encoding
      │
      ▼
Multi-Head Self-Attention
      │
      ▼
Add & LayerNorm
      │
      ▼
Feed Forward Network
      │
      ▼
Add & LayerNorm
```

The encoder reads **the entire input sentence**.

---

# Decoder Components

Each decoder layer contains:

```text
Embedding
      │
      ▼
Positional Encoding
      │
      ▼
Masked Multi-Head Attention
      │
      ▼
Add & LayerNorm
      │
      ▼
Cross-Attention
      │
      ▼
Add & LayerNorm
      │
      ▼
Feed Forward Network
      │
      ▼
Add & LayerNorm
```

The decoder generates **one token at a time**.

---

# Step-by-Step Flow

### Step 1

Input:

```text
Summarize this article...
```

↓

### Step 2

Encoder processes the complete input and creates **contextual embeddings**.

↓

### Step 3

Decoder starts with a special **<START>** token.

↓

### Step 4

Masked Self-Attention allows the decoder to see only previously generated tokens.

↓

### Step 5

Cross-Attention lets the decoder attend to the encoder's output.

↓

### Step 6

The model predicts the next token.

↓

### Step 7

Repeat until the **<END>** token is generated.

---

# Flow Diagram

```text
Input Text
     │
     ▼
Encoder
(Understand)
     │
     ▼
Contextual Embeddings
     │
     ▼
Decoder
(Generate)
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

# Applications

Encoder–Decoder models are widely used for:

* ✅ Machine Translation
* ✅ Text Summarization
* ✅ Question Answering
* ✅ Speech-to-Text
* ✅ Text-to-Text Tasks

---

# Popular Encoder–Decoder Models

Examples include:

* T5
* BART
* mT5

---

# Advantages

* ✅ Excellent for input-to-output tasks.
* ✅ Encoder understands the complete input.
* ✅ Decoder generates fluent output.
* ✅ Very effective for translation and summarization.

---

# Disadvantages

* ❌ More computationally expensive than Encoder-Only or Decoder-Only models.
* ❌ More complex architecture because it contains both an Encoder and a Decoder.

---

# Encoder-Only vs Decoder-Only vs Encoder–Decoder

| Encoder-Only                 | Decoder-Only                   | Encoder–Decoder                     |
| ---------------------------- | ------------------------------ | ----------------------------------- |
| Understands text             | Generates text                 | Understands and generates           |
| Bidirectional Self-Attention | Masked (Causal) Self-Attention | Encoder + Decoder + Cross-Attention |
| Reads the whole input        | Generates one token at a time  | Input → Output transformation       |
| Example: BERT                | Example: GPT, Llama            | Example: T5, BART                   |

---

> **An Encoder–Decoder Transformer uses both the Encoder and the Decoder. The Encoder processes and understands the entire input sequence, while the Decoder generates the output one token at a time using masked self-attention and cross-attention over the encoder's output. This architecture is ideal for sequence-to-sequence tasks such as machine translation, text summarization, and question answering.**

---

# Easy Memory Trick

Imagine a translator:

👨‍🏫 **Interpreter (Encoder)** listens to the complete English sentence and understands it.

↓

👩‍🏫 **Speaker (Decoder)** uses that understanding to speak the sentence in French, one word at a time.

```text
English Sentence
        │
        ▼
   Encoder
 (Understand)
        │
        ▼
 Meaning
        │
        ▼
   Decoder
 (Generate)
        │
        ▼
French Sentence
```

---

> **An Encoder–Decoder Transformer first understands the input using the Encoder and then generates the output token by token using the Decoder with cross-attention.**
