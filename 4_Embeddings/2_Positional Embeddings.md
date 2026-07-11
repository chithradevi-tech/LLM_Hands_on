# Embeddings – Positional Embeddings

## What are Positional Embeddings?

**Positional Embeddings** provide information about the **position (order)** of each token in a sentence.

Since Transformers process all tokens **in parallel**, they do not naturally know the order of words. Positional embeddings solve this problem.

---

## Simple Definition

> **Positional Embeddings tell the Transformer where each token appears in the sentence.**

---

# Why Do We Need Positional Embeddings?

Consider these two sentences:

```text
I love AI
```

```text
AI love I
```

Both sentences contain the same words, but the order is different, so the meaning changes.

Without positional information, the Transformer would treat them almost the same.

---

# How Positional Embeddings Work

### Step 1: Token Embeddings

Sentence:

```text
I love AI
```

↓

```text
I     → [0.2, 0.8, ...]
love  → [0.5, 0.3, ...]
AI    → [0.7, 0.4, ...]
```

---

### Step 2: Position Embeddings

Each position has its own embedding.

| Position | Position Embedding |
| -------- | ------------------ |
| 0        | [0.1, 0.2, ...]    |
| 1        | [0.3, 0.4, ...]    |
| 2        | [0.5, 0.6, ...]    |

---

### Step 3: Add Them Together

The model combines the token embedding with the positional embedding.

```text
Final Input = Token Embedding + Positional Embedding
```

Example:

```text
Token Embedding ("love")
        +
Position Embedding (1)
        ↓
Final Vector
```

This final vector is passed to the Transformer.

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
Positional Embeddings
     │
     ▼
Add Both Together
     │
     ▼
Transformer
```

---

# Types of Positional Embeddings

### 1. **Sinusoidal Positional Encoding**

* Uses **sine and cosine functions**.
* Fixed values (not trainable).
* Introduced in the original Transformer paper.

### 2. **Learned Positional Embeddings**

* Position vectors are **learned during training**.
* Trainable parameters.

### 3. **RoPE (Rotary Positional Embedding)**

* Rotates the **Query (Q)** and **Key (K)** vectors.
* Excellent for long-context understanding.
* Used in many modern LLMs.

### 4. **ALiBi (Attention with Linear Biases)**

* Adds a **distance-based linear bias** to attention scores.
* No positional vectors are added.
* Works well for long sequences.

---

# Example

Sentence:

```text
The cat sat
```

| Token | Position |
| ----- | -------: |
| The   |        0 |
| cat   |        1 |
| sat   |        2 |

The model now knows:

* **The** is the first word.
* **cat** is the second word.
* **sat** is the third word.

---

# Advantages

* ✅ Preserves word order.
* ✅ Helps the Transformer understand sentence structure.
* ✅ Essential for language understanding.
* ✅ Improves context and meaning.

---

# Token Embeddings vs Positional Embeddings

| Token Embeddings                    | Positional Embeddings                |
| ----------------------------------- | ------------------------------------ |
| Represent the meaning of a token    | Represent the position of a token    |
| Example: "cat"                      | Example: Position 2                  |
| Tell the model **what** the word is | Tell the model **where** the word is |

---

> **Positional Embeddings provide information about the order of tokens in a sentence. Since Transformers process all tokens in parallel, they need positional information to understand sequence order. Positional embeddings are combined with token embeddings before being passed to the Transformer. Common approaches include Sinusoidal Encoding, Learned Positional Embeddings, RoPE, and ALiBi.**

---

# Easy Memory Trick

Imagine students in a classroom.

* **Student Name** = Token Embedding (who the student is)
* **Seat Number** = Positional Embedding (where the student sits)

To identify a student completely, you need both:

```text
Student Profile
        +
Seat Number
        ↓
Complete Information
```

Similarly:

* **Token Embedding** = Meaning
* **Positional Embedding** = Position

Together, they help the Transformer understand the sentence.

---


> **Positional Embeddings provide the position of each token in a sequence, enabling the Transformer to understand word order.**
