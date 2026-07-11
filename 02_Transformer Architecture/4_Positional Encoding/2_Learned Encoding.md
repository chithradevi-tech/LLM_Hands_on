# Learned Positional Encoding

## What is Learned Positional Encoding?

**Learned Positional Encoding** is a technique where the **position vectors are learned during training** instead of being calculated using sine and cosine functions.

The model treats the position vectors like any other trainable parameters and updates them through **backpropagation**.

---

## Simple Definition

> **Learned Positional Encoding uses trainable vectors to represent the position of each word. These vectors are learned automatically during training.**

---

## Why Do We Need It?

Transformers process all words **in parallel**, so they don't know the order of words.

For example:

```text
I love AI
AI love I
```

Both sentences have the same words but different meanings.

So, the model needs to know the position of each word.

---

# How It Works

Sentence:

```text
I love AI
```

### Step 1: Word Embeddings

```text
I      → [0.2, 0.8, ...]
Love   → [0.5, 0.3, ...]
AI     → [0.7, 0.4, ...]
```

---

### Step 2: Learned Position Embeddings

During training, the model learns a vector for each position.

Example:

| Position   | Learned Vector    |
| ---------- | ----------------- |
| Position 0 | [0.12, 0.45, ...] |
| Position 1 | [0.87, 0.21, ...] |
| Position 2 | [0.33, 0.76, ...] |

These values are **not fixed**. They are updated during training.

---

### Step 3: Add Them Together

```text
Final Input = Word Embedding + Learned Position Embedding
```

Example:

```text
Embedding("I")
        +
Position Embedding(0)
        ↓
Final Representation
```

This final representation is passed into the Transformer.

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
Learn Position Embeddings
     │
     ▼
Add Both Together
     │
     ▼
Input to Transformer
```

---

# Learned vs Sinusoidal Encoding

| Learned Positional Encoding                  | Sinusoidal Positional Encoding                        |
| -------------------------------------------- | ----------------------------------------------------- |
| Position vectors are learned during training | Position vectors are calculated using sine and cosine |
| Trainable parameters                         | No trainable parameters                               |
| Can adapt to the training data               | Fixed mathematical values                             |
| Common in many modern LLMs                   | Used in the original Transformer paper                |

---

# Advantages

* ✅ Learns the best positional representation from data.
* ✅ Can improve performance for many tasks.
* ✅ Adapts to the specific training dataset.
* ✅ Widely used in modern Transformer models.

---

# Disadvantages

* ❌ Adds extra trainable parameters.
* ❌ May not generalize well to sequence lengths longer than those seen during training.

---

# Interview Answer (30 Seconds)

> **Learned Positional Encoding is a method where the Transformer learns a unique embedding vector for each position during training. These position embeddings are added to the word embeddings before they are passed into the Transformer. Unlike sinusoidal encoding, which uses fixed mathematical functions, learned positional encoding uses trainable parameters and can adapt to the training data.**

---

# Easy Memory Trick

Imagine a school.

* **Student** = Word Embedding
* **Seat Number** = Position

### Sinusoidal Encoding

The seat numbers are **fixed** forever.

### Learned Positional Encoding

The teacher can **change and optimize the seat numbers** over time to improve the classroom arrangement.

So:

* **Sinusoidal** = **Fixed positions**
* **Learned** = **Trainable positions**


> **Learned Positional Encoding uses trainable embedding vectors to represent token positions, allowing the Transformer to learn the best positional information directly from the training data.**
