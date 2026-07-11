# Transformer Architecture – Encoder

## What is the Encoder?

The **Encoder** is the first part of the Transformer architecture.

Its job is to **read the input sentence, understand its meaning and context, and produce contextual representations (embeddings)** that are passed to the decoder or used directly by encoder-only models.

---

## Simple Definition

> **The Encoder reads the input text and converts it into context-aware embeddings by understanding the relationships between all words in the sentence.**

---

# Example

Input Sentence:

```text
I love AI
```

The encoder reads the entire sentence at once and understands:

* "I" → Subject
* "love" → Action
* "AI" → Object

It then creates contextual embeddings for each word.

---

# Components of an Encoder Layer

Each encoder layer contains:

```text
Input
   │
   ▼
Multi-Head Self-Attention
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

A Transformer encoder is built by **stacking multiple encoder layers** (e.g., 6, 12, 24, or more).

---

# Step-by-Step Working

### Step 1: Tokenization

```text
I love AI
```

↓

```text
["I", "love", "AI"]
```

---

### Step 2: Embedding Layer

Convert tokens into vectors.

```text
I    → Vector
Love → Vector
AI   → Vector
```

---

### Step 3: Add Positional Encoding

Since the Transformer doesn't know word order, positional information is added.

```text
Word Embedding
       +
Positional Encoding
```

↓

Final Input

---

### Step 4: Multi-Head Self-Attention

Each word attends to **every other word** in the sentence.

Example:

```text
I love AI
```

The word **"love"** attends to both **"I"** and **"AI"** to understand the full context.

---

### Step 5: Add & Layer Normalization

* Add the original input (**Residual Connection**)
* Apply **Layer Normalization**

This stabilizes training.

---

### Step 6: Feed Forward Network (FFN)

Each token passes through a small neural network independently to learn richer representations.

---

### Step 7: Add & Layer Normalization

Again:

* Residual Connection
* Layer Normalization

---

### Step 8: Output

The encoder produces **contextual embeddings**.

These embeddings contain both:

* The meaning of each word.
* The context from surrounding words.

---

# Encoder Flow Diagram

```text
Input Sentence
      │
      ▼
Tokenization
      │
      ▼
Embedding Layer
      │
      ▼
Positional Encoding
      │
      ▼
Encoder Layer
 ┌───────────────────────────┐
 │ Multi-Head Self-Attention │
 │ Add & LayerNorm           │
 │ Feed Forward Network      │
 │ Add & LayerNorm           │
 └───────────────────────────┘
      │
      ▼
Contextual Embeddings
```

---

# Why is the Encoder Important?

The encoder:

* ✅ Understands the complete input sentence.
* ✅ Learns relationships between words.
* ✅ Captures context and meaning.
* ✅ Produces embeddings for downstream tasks.

---

# Models That Use Only the Encoder

Examples:

* BERT
* RoBERTa
* DistilBERT

These models are mainly used for:

* Text Classification
* Sentiment Analysis
* Named Entity Recognition (NER)
* Question Answering (extractive)

---

# Interview Answer (30 Seconds)

> **The Encoder is the first part of the Transformer architecture. It reads the input sentence, converts tokens into embeddings, adds positional information, and processes them through multiple encoder layers consisting of Multi-Head Self-Attention, Feed Forward Networks, Residual Connections, and Layer Normalization. The output is a set of context-aware embeddings that capture the meaning and relationships between words.**

---

# Easy Memory Trick

Imagine a teacher reading a paragraph.

* 📖 Reads the entire paragraph.
* 🧠 Understands the meaning.
* 📝 Makes detailed notes.

The **teacher** is like the **Encoder**.

* **Input sentence** = Paragraph
* **Notes** = Contextual embeddings

---


> **The Encoder reads the entire input sentence and produces context-aware embeddings using Self-Attention and Feed Forward Networks.**
