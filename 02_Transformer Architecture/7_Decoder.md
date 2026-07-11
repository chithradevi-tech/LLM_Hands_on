# Transformer Architecture – Decoder

## What is the Decoder?

The **Decoder** is the second part of the Transformer architecture.

Its job is to **generate the output sequence one token (word) at a time** using:

* The previously generated tokens.
* Information from the encoder (in encoder–decoder models).

---

## Simple Definition

> **The Decoder generates the output text one token at a time by using previous tokens and, in encoder–decoder models, information from the encoder.**

---

# Example

Suppose we want to translate:

```text id="ulj09a"
English:
I love AI
```

The decoder generates:

```text id="th7ixw"
French:
J' → J'aime → J'aime l' → J'aime l'IA
```

It predicts **one word at a time**, not the whole sentence at once.

---

# Components of a Decoder Layer

Each decoder layer contains:

```text id="gw8w5b"
Input
   │
   ▼
Masked Multi-Head Self-Attention
   │
   ▼
Add & Layer Normalization
   │
   ▼
Cross-Attention
   │
   ▼
Add & Layer Normalization
   │
   ▼
Feed Forward Network (FFN)
   │
   ▼
Add & Layer Normalization
   │
   ▼
Output
```

---

# Step-by-Step Working

### Step 1: Previous Output Tokens

Suppose the model has generated:

```text id="iq7zj5"
I
```

Now it predicts the next word.

---

### Step 2: Embedding + Positional Encoding

The previous output tokens are converted into embeddings and positional information is added.

---

### Step 3: Masked Multi-Head Self-Attention

The decoder can only look at:

* ✅ Previous words
* ✅ Current word

It **cannot** look at future words.

Example:

```text id="vhjlwm"
I love AI
```

While predicting **"love"**, it can only see:

```text id="bnn6tq"
I love
```

Not:

```text id="w76ael"
AI
```

---

### Step 4: Cross-Attention

The decoder attends to the encoder output.

* **Query (Q)** → Decoder
* **Key (K)** → Encoder
* **Value (V)** → Encoder

This helps the decoder focus on the relevant parts of the input sentence.

---

### Step 5: Feed Forward Network (FFN)

Each token passes through the FFN to learn richer representations.

---

### Step 6: Predict Next Token

The decoder predicts the next word.

Example:

```text id="0oaqf8"
I
↓
love
↓
AI
↓
<END>
```

The process repeats until an end token is generated.

---

# Decoder Flow Diagram

```text id="7ih54u"
Previous Tokens
        │
        ▼
Embedding Layer
        │
        ▼
Positional Encoding
        │
        ▼
Masked Multi-Head Attention
        │
        ▼
Cross-Attention
        │
        ▼
Feed Forward Network
        │
        ▼
Linear + Softmax
        │
        ▼
Next Token
```

---

# Why is the Decoder Important?

The decoder:

* ✅ Generates text one token at a time.
* ✅ Prevents looking at future tokens using masking.
* ✅ Uses encoder information (for encoder–decoder models).
* ✅ Produces coherent output.

---

# Models That Use the Decoder

### Decoder-Only Models

* GPT
* Llama
* Gemma

These models generate text but **do not use Cross-Attention**, because there is no separate encoder.

---

### Encoder–Decoder Models

* T5
* BART

These models use:

* Masked Self-Attention
* Cross-Attention
* FFN

---

# Encoder vs Decoder

| Encoder                                  | Decoder                                        |
| ---------------------------------------- | ---------------------------------------------- |
| Reads the input                          | Generates the output                           |
| Uses Self-Attention                      | Uses Masked Self-Attention                     |
| Can see all input tokens                 | Can see only previous output tokens            |
| Produces contextual embeddings           | Predicts the next token                        |
| Uses FFN                                 | Uses FFN                                       |
| No Cross-Attention (encoder-only models) | Uses Cross-Attention in encoder–decoder models |

---

# Interview Answer (30 Seconds)

> **The Decoder is the component of a Transformer responsible for generating the output sequence one token at a time. Each decoder layer contains Masked Multi-Head Self-Attention, Cross-Attention (in encoder–decoder models), Feed Forward Networks, Residual Connections, and Layer Normalization. Masked attention prevents the model from seeing future tokens, while Cross-Attention allows it to use information from the encoder to generate accurate outputs.**

---

# Easy Memory Trick

Imagine a student writing an essay.

* ✍️ The student can read **only what has already been written**.
* 📖 The student can also refer to the **source material** (encoder output) if available.
* ✨ Then the student writes the **next word**.

That's exactly how the **Decoder** works.

---

> **The Decoder generates the output sequence one token at a time using Masked Self-Attention, Cross-Attention (if an encoder exists), and Feed Forward Networks.**
