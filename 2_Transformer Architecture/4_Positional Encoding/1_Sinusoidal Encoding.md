# Positional Encoding – Sinusoidal Encoding

## Why Do We Need Positional Encoding?

Transformers process **all words at the same time (in parallel)**.

Unlike RNNs, they **do not know the order of the words**.

For example:

```text
Sentence 1:
I love AI

Sentence 2:
AI love I
```

Both sentences contain the same words, but the meanings are different.

So, the Transformer needs information about **the position of each word**.

This is the purpose of **Positional Encoding**.

---

# What is Sinusoidal Encoding?

**Sinusoidal Encoding** is a method of generating positional information using **sine (sin)** and **cosine (cos)** mathematical functions.

Instead of learning the position, the model **calculates** a unique position vector for each token.

---

## Simple Definition

> **Sinusoidal Encoding uses sine and cosine functions to generate a unique positional vector for every word, helping the Transformer understand the order of words.**

---

# Example

Sentence:

```text
I love AI
```

### Step 1: Token Embeddings

```text
I      → Embedding
Love   → Embedding
AI     → Embedding
```

---

### Step 2: Generate Position Vectors

```text
Position 0 → Sin/Cos values
Position 1 → Sin/Cos values
Position 2 → Sin/Cos values
```

Example (illustrative values):

| Position | Positional Vector         |
| -------- | ------------------------- |
| 0        | [0.00, 1.00, 0.00, 1.00]  |
| 1        | [0.84, 0.54, 0.01, 0.99]  |
| 2        | [0.91, -0.42, 0.02, 0.99] |

Each position gets a **different vector**.

---

### Step 3: Add Embedding + Positional Encoding

```text
Final Input = Word Embedding + Positional Encoding
```

So,

```text
Embedding("I")
      +
Position Vector(0)
      ↓
Final Representation
```

---

# Why Use Sine and Cosine?

Sine and cosine create **smooth and repeating patterns**.

This helps the Transformer:

* Learn the **relative distance** between words.
* Generalize to longer sequences.
* Assign a unique representation to every position.

---

# Formula (for Reference)

For even dimensions:

[
PE(pos,2i)=\sin\left(\frac{pos}{10000^{2i/d}}\right)
]

For odd dimensions:

[
PE(pos,2i+1)=\cos\left(\frac{pos}{10000^{2i/d}}\right)
]

Where:

* **pos** = Position of the word.
* **i** = Dimension index.
* **d** = Embedding dimension.

> **Interview tip:** You usually don't need to memorize these formulas unless you're interviewing for a research-focused role.

---

# Flow Diagram

```text
Sentence
     │
     ▼
Tokenization
     │
     ▼
Word Embeddings
     │
     ▼
Generate Sinusoidal Position Vectors
     │
     ▼
Add Embeddings + Position Vectors
     │
     ▼
Input to Transformer
```

---

# Advantages

* ✅ Gives the Transformer information about word order.
* ✅ No extra parameters need to be learned.
* ✅ Can generalize to sequences longer than those seen during training.
* ✅ Produces unique positional vectors.

---

# Learned vs Sinusoidal Positional Encoding

| Learned Positional Encoding                    | Sinusoidal Positional Encoding                      |
| ---------------------------------------------- | --------------------------------------------------- |
| Position vectors are learned during training   | Position vectors are computed using sine and cosine |
| Adds trainable parameters                      | No trainable parameters                             |
| Used in many modern LLMs                       | Used in the original Transformer paper              |
| May not generalize as well to longer sequences | Better at extrapolating to unseen sequence lengths  |

---


> **Sinusoidal Encoding is a positional encoding technique introduced in the original Transformer paper. It uses sine and cosine functions to generate a unique positional vector for each token. This positional vector is added to the token embedding so that the Transformer can understand the order of words. Unlike learned positional embeddings, sinusoidal encoding does not require any trainable parameters and can generalize to longer sequences.**

---

## Easy Memory Trick

Imagine every seat in a classroom has a **unique number**.

* The **student** = Word Embedding.
* The **seat number** = Positional Encoding.

Even if the same student changes seats, you know their **position** because of the seat number.

Similarly:

* **Word Embedding** tells the Transformer **what the word is**.
* **Sinusoidal Positional Encoding** tells the Transformer **where the word is**.
