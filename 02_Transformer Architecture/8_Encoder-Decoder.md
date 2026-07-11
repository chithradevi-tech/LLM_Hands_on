# Transformer Architecture – Encoder-Decoder

## What is an Encoder–Decoder Architecture?

The **Encoder–Decoder architecture** is the original Transformer architecture introduced in the **"Attention Is All You Need"** paper.

It consists of two parts:

1. **Encoder** → Understands the input.
2. **Decoder** → Generates the output.

---

## Simple Definition

> **The Encoder reads and understands the input sentence, while the Decoder generates the output sentence one token at a time.**

---

# Example

Suppose we want to translate:

```text
English:
I love AI
```

↓

```text
French:
J'aime l'IA
```

### Encoder

Reads:

```text
I
Love
AI
```

and understands the meaning.

↓

Produces **Contextual Embeddings**

↓

### Decoder

Uses:

* Previous generated words
* Encoder output

↓

Generates:

```text
J'
↓
J'aime
↓
J'aime l'
↓
J'aime l'IA
```

---

# Architecture Diagram

```text
                INPUT SENTENCE
              "I love AI"
                     │
                     ▼
              ┌───────────────┐
              │    Encoder    │
              └───────────────┘
                     │
         Contextual Embeddings
                     │
                     ▼
              ┌───────────────┐
              │    Decoder    │
              └───────────────┘
                     │
                     ▼
              OUTPUT SENTENCE
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

The encoder understands the entire input sentence.

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

The decoder generates one token at a time.

---

# Step-by-Step Flow

### Step 1

Input Sentence

```text
I love AI
```

↓

### Step 2

Embedding + Positional Encoding

↓

### Step 3

Encoder understands the sentence.

↓

### Step 4

Encoder outputs contextual embeddings.

↓

### Step 5

Decoder starts with a special **<START>** token.

↓

### Step 6

Masked Self-Attention looks only at previous output tokens.

↓

### Step 7

Cross-Attention looks at the encoder output.

↓

### Step 8

FFN processes the information.

↓

### Step 9

Softmax predicts the next word.

↓

Repeat until the **<END>** token is generated.

---

# Complete Flow

```text
Input Sentence
       │
       ▼
Embedding
       │
       ▼
Positional Encoding
       │
       ▼
Encoder
       │
       ▼
Contextual Embeddings
       │
       ▼
Decoder
       │
       ▼
Linear Layer
       │
       ▼
Softmax
       │
       ▼
Next Word
       │
       ▼
Repeat
       │
       ▼
Final Output
```

---

# Applications

Encoder–Decoder Transformers are commonly used for:

* 🌍 Machine Translation
* 📝 Text Summarization
* ❓ Question Answering
* 🎤 Speech Recognition
* 📄 Text Generation from Input

---

# Models Using Encoder–Decoder

Examples include:

* T5
* BART
* mT5

---

# Encoder vs Decoder vs Encoder–Decoder

| Encoder             | Decoder                    | Encoder–Decoder               |
| ------------------- | -------------------------- | ----------------------------- |
| Understands input   | Generates output           | Does both                     |
| Uses Self-Attention | Uses Masked Self-Attention | Uses both                     |
| No text generation  | Text generation            | Input → Output transformation |
| Example: BERT       | Example: GPT               | Example: T5, BART             |

---

# Interview Answer (30 Seconds)

> **The Encoder–Decoder architecture is the original Transformer design. The Encoder reads and understands the input sentence using Multi-Head Self-Attention and Feed Forward Networks, producing contextual embeddings. The Decoder then generates the output sequence one token at a time using Masked Self-Attention, Cross-Attention, and Feed Forward Networks. This architecture is widely used for sequence-to-sequence tasks such as machine translation and text summarization.**

---

# Easy Memory Trick

Imagine a translator:

👨‍🏫 **Person A (Encoder)** listens carefully to an English sentence and understands its meaning.

👩‍🏫 **Person B (Decoder)** uses that understanding to speak the sentence in French, one word at a time.

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

> **The Encoder–Decoder architecture first understands the input using the Encoder and then generates the output step by step using the Decoder.**
