# Embeddings – Semantic Embeddings

## What are Semantic Embeddings?

**Semantic Embeddings** are vector representations that capture the **meaning (semantics)** of text.

Texts with **similar meanings** will have **similar embedding vectors**, even if they use different words.

---

## Simple Definition

> **Semantic Embeddings are numerical vectors that represent the meaning of words, sentences, or documents.**

---

# Why Do We Need Semantic Embeddings?

Traditional keyword search only looks for **exact words**.

Example:

```text
Query:
I bought a car.
```

Document:

```text
I purchased a vehicle.
```

Keyword search may not match because:

* car ≠ vehicle
* bought ≠ purchased

But Semantic Embeddings understand that:

* car ≈ vehicle
* bought ≈ purchased

So they recognize that both sentences have the **same meaning**.

---

# How Semantic Embeddings Work

### Step 1: Input Text

```text
I love AI.
```

↓

### Step 2: Convert to Embedding

```text
[0.42, -0.15, 0.87, ...]
```

↓

### Step 3: Compare with Another Text

```text
Artificial Intelligence is my favorite.
```

↓

Embedding:

```text
[0.40, -0.18, 0.85, ...]
```

Since the vectors are very similar, the model knows the meanings are similar.

---

# Flow Diagram

```text
Text
 │
 ▼
Embedding Model
 │
 ▼
Semantic Embedding (Vector)
 │
 ▼
Compare with Other Vectors
 │
 ▼
Similarity Score
```

---

# Example

### Sentence 1

```text
The boy is playing football.
```

### Sentence 2

```text
A child is playing soccer.
```

Different words, but nearly the same meaning.

Semantic embeddings place these vectors **close together**.

---

### Sentence 3

```text
I bought a laptop.
```

This has a different meaning, so its vector will be **farther away**.

---

# Applications

Semantic Embeddings are widely used in:

* ✅ Semantic Search
* ✅ RAG (Retrieval-Augmented Generation)
* ✅ Chatbots
* ✅ Question Answering
* ✅ Recommendation Systems
* ✅ Text Similarity
* ✅ Document Clustering
* ✅ Duplicate Detection

---

# Semantic Embeddings vs Token Embeddings vs Sentence Embeddings

| Feature    | Token Embeddings     | Sentence Embeddings     | Semantic Embeddings                            |
| ---------- | -------------------- | ----------------------- | ---------------------------------------------- |
| Represents | Individual token     | Entire sentence         | Meaning of text (word, sentence, or document)  |
| Output     | One vector per token | One vector per sentence | One or more vectors capturing semantic meaning |
| Main Use   | Transformer input    | Similarity/Search       | Semantic search, RAG, retrieval                |

> **Note:** In practice, **sentence embeddings are a type of semantic embedding**. The term **semantic embedding** is broader—it can refer to embeddings for words, sentences, paragraphs, or documents as long as they capture meaning.

---

# Popular Models

Examples include:

* Sentence-BERT
* all-MiniLM-L6-v2
* e5
* text-embedding-3-small

---

> **Semantic Embeddings are dense vector representations that capture the meaning of text rather than just the words themselves. Texts with similar meanings produce similar vectors, making semantic embeddings ideal for applications such as semantic search, RAG, document retrieval, recommendation systems, and text similarity.**

---

# Easy Memory Trick

Imagine two people saying:

```text
I bought a car.
```

and

```text
I purchased a vehicle.
```

The words are different, but the **meaning is the same**.

Semantic embeddings don't focus on the exact words—they focus on the **meaning**.

---

> **Semantic Embeddings are vector representations that capture the meaning of text, allowing models to identify semantically similar content even when different words are used.**
