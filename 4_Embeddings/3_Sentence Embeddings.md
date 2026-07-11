# Embeddings – Sentence Embeddings

## What are Sentence Embeddings?

**Sentence Embeddings** are **dense numerical vectors** that represent the **meaning of an entire sentence**, rather than individual words.

Instead of creating one vector per token, the model creates **one vector for the whole sentence**.

---

## Simple Definition

> **Sentence Embeddings convert an entire sentence into a single vector that captures its overall meaning.**

---

# Why Do We Need Sentence Embeddings?

Sometimes we want to compare the meaning of complete sentences instead of individual words.

For example:

Sentence 1:

```text
I love artificial intelligence.
```

Sentence 2:

```text
AI is my favorite subject.
```

Although the words are different, both sentences have a similar meaning.

Sentence embeddings place these sentences **close together in vector space**.

---

# How Sentence Embeddings Work

### Step 1: Input Sentence

```text
The cat is sleeping.
```

↓

### Step 2: Tokenization

```text
["The", "cat", "is", "sleeping"]
```

↓

### Step 3: Token Embeddings

```text
The       → [ ... ]
cat       → [ ... ]
is        → [ ... ]
sleeping  → [ ... ]
```

↓

### Step 4: Transformer

The Transformer processes the tokens and understands the context.

↓

### Step 5: Combine Token Representations

The model combines the token embeddings into **one vector**.

Example:

```text
Sentence Embedding

[0.42, 0.71, -0.13, ...]
```

This single vector represents the meaning of the entire sentence.

---

# Flow Diagram

```text
Sentence
    │
    ▼
Tokenization
    │
    ▼
Token Embeddings
    │
    ▼
Transformer
    │
    ▼
Combine Token Representations
    │
    ▼
Sentence Embedding
```

---

# Example

Sentence A:

```text
The weather is nice today.
```

Sentence B:

```text
Today has pleasant weather.
```

Their sentence embeddings will be **very similar** because the meanings are similar.

Sentence C:

```text
I bought a new laptop.
```

Its embedding will be **farther away** because it has a different meaning.

---

# Applications of Sentence Embeddings

Sentence embeddings are widely used in:

* ✅ Semantic Search
* ✅ RAG (Retrieval-Augmented Generation)
* ✅ Question Answering
* ✅ Chatbots
* ✅ Text Similarity
* ✅ Document Search
* ✅ Recommendation Systems
* ✅ Clustering and Classification

---

# Advantages

* ✅ Represents the meaning of the whole sentence.
* ✅ Easy to compare sentence similarity.
* ✅ Useful for search and retrieval.
* ✅ Reduces an entire sentence to one compact vector.

---

# Token Embeddings vs Sentence Embeddings

| Token Embeddings            | Sentence Embeddings                    |
| --------------------------- | -------------------------------------- |
| Represent individual tokens | Represent the entire sentence          |
| One vector per token        | One vector for the whole sentence      |
| Used inside the Transformer | Used for similarity, search, RAG, etc. |

---

# Models Commonly Used for Sentence Embeddings

Examples include:

* Sentence-BERT
* all-MiniLM-L6-v2
* e5

---

> **Sentence Embeddings are dense vector representations of an entire sentence. They capture the overall semantic meaning of the sentence and are commonly used in applications like semantic search, RAG, document retrieval, and text similarity. Unlike token embeddings, which represent individual words or subwords, sentence embeddings represent the complete sentence as a single vector.**

---

# Easy Memory Trick

Imagine a movie.

* **Each actor** = Token Embedding
* **The whole movie story** = Sentence Embedding

Token embeddings describe **individual words**, while a sentence embedding summarizes the **overall meaning** of the entire sentence.

---

> **Sentence Embeddings represent the entire sentence as a single dense vector that captures its overall meaning and is useful for tasks like semantic search and RAG.**
