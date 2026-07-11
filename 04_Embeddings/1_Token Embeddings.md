# Embeddings – Token Embeddings

## What are Token Embeddings?

**Token Embeddings** are **dense numerical vectors** that represent the meaning of each token (word or subword).

They are the **first representation** of text inside a Transformer model.

---

## Simple Definition

> **Token Embeddings convert each token into a dense vector of numbers that captures its meaning.**

---

# Why Do We Need Token Embeddings?

Computers cannot understand text directly.

Example:

```text
I love AI
```

The Transformer cannot process words.

So first:

```text
"I"
"love"
"AI"
```

↓

Convert into vectors:

```text
I     → [0.12, 0.45, 0.87, ...]
love  → [0.78, 0.21, 0.35, ...]
AI    → [0.91, 0.63, 0.48, ...]
```

These vectors are called **Token Embeddings**.

---

# How Token Embeddings Work

### Step 1: Tokenization

Sentence:

```text
I love AI
```

↓

Tokens:

```text
["I", "love", "AI"]
```

---

### Step 2: Convert to Token IDs

Example:

| Token | Token ID |
| ----- | -------: |
| I     |      101 |
| love  |      502 |
| AI    |      845 |

---

### Step 3: Embedding Lookup

The model has an **Embedding Matrix**.

Example:

| Token ID | Embedding Vector        |
| -------- | ----------------------- |
| 101      | [0.12, 0.45, 0.87, ...] |
| 502      | [0.78, 0.21, 0.35, ...] |
| 845      | [0.91, 0.63, 0.48, ...] |

The model looks up the vector corresponding to each token ID.

---

### Step 4: Pass to the Transformer

The token embeddings are combined with **Positional Embeddings/Positional Encoding** and then passed to the Transformer layers.

```text
Token Embeddings
        +
Positional Encoding
        ↓
Transformer
```

---

# Flow Diagram

```text
Sentence
    │
    ▼
Tokenization
    │
    ▼
Token IDs
    │
    ▼
Embedding Matrix
    │
    ▼
Token Embeddings
    │
    ▼
+ Positional Encoding
    │
    ▼
Transformer
```

---

# Example

Sentence:

```text
The cat sat.
```

Token embeddings (example values):

| Token | Embedding          |
| ----- | ------------------ |
| The   | [0.21, 0.65, 0.12] |
| cat   | [0.84, 0.19, 0.77] |
| sat   | [0.43, 0.91, 0.36] |

> **Note:** These are example values. Real LLMs use vectors with hundreds or thousands of dimensions (e.g., 768, 1024, or 4096).

---

# Why are Token Embeddings Important?

Token embeddings help the model understand **semantic meaning**.

For example:

```text
King
Queen
```

have similar embeddings because they are semantically related.

Likewise:

```text
Car
Vehicle
```

will have similar embeddings.

---

# Advantages

* ✅ Converts text into numerical vectors.
* ✅ Captures semantic meaning.
* ✅ Similar words have similar embeddings.
* ✅ Forms the input to the Transformer.

---

# Token Embeddings vs Positional Embeddings

| Token Embeddings                 | Positional Embeddings                                                                 |
| -------------------------------- | ------------------------------------------------------------------------------------- |
| Represent the meaning of a token | Represent the position of a token                                                     |
| Learned during training          | Can be fixed (Sinusoidal) or learned (Learned Positional Encoding, RoPE, ALiBi, etc.) |
| Example: "cat"                   | Example: Position 1, Position 2                                                       |

---


> **Token Embeddings are dense vector representations of tokens. Each token ID is mapped to a trainable embedding vector using an embedding matrix. These embeddings capture the semantic meaning of tokens and are combined with positional information before being passed to the Transformer for further processing.**

---

# Easy Memory Trick

Imagine a school:

* **Student Name** → Token
* **Roll Number** → Token ID
* **Student Profile** → Token Embedding

The Transformer doesn't just use the student's name—it uses the **profile** to understand the student.

Similarly:

* **Token** → Word/Subword
* **Token ID** → Number
* **Token Embedding** → Meaningful numerical representation

---


> **Token Embeddings convert each token into a dense numerical vector that captures its meaning and serves as the input to the Transformer.**
