# ALiBi (Attention with Linear Biases)

## What is ALiBi?

**ALiBi (Attention with Linear Biases)** is a positional encoding technique that **adds a linear bias to the attention scores** instead of adding positional embeddings or rotating vectors.

It helps the Transformer understand **how far apart two words are**.

---

## Simple Definition

> **ALiBi is a positional encoding method that adds a distance-based linear bias to the attention scores, allowing the model to understand relative positions without using positional embeddings.**

---

# Why Do We Need ALiBi?

Transformers process all words in parallel, so they don't know the order of words.

Example:

```text
I love AI
AI love I
```

The same words appear, but the meanings are different.

ALiBi helps the model understand:

* Word order
* Distance between words

---

# How ALiBi Works

### Step 1: Create Q, K, and V

```text
Sentence
      ↓
Q   K   V
```

---

### Step 2: Calculate Attention Scores

Normally:

```text
Attention Score = Q × Kᵀ
```

---

### Step 3: Add Linear Bias

Instead of adding positional embeddings, ALiBi subtracts a bias based on the distance between words.

Example:

```text
Current Word → Cat

Nearby word
Distance = 1
Bias = Small

Far word
Distance = 5
Bias = Larger
```

Nearby words receive less penalty than distant words.

---

### Step 4: Apply Softmax

```text
Attention Score
      +
Linear Bias
      ↓
Softmax
      ↓
Attention Weights
```

---

# Flow Diagram

```text
Sentence
      │
      ▼
Create Q, K, V
      │
      ▼
Q × Kᵀ
      │
      ▼
Add Linear Bias
      │
      ▼
Softmax
      │
      ▼
Multiply with V
      │
      ▼
Output
```

---

# Example

Sentence:

```text
The cat sat on the mat.
```

Suppose the model is processing **"sat"**.

Words close to **"sat"**:

```text
cat
on
```

receive a **small bias**.

Words farther away:

```text
The
mat
```

receive a **larger bias**.

So the model naturally pays more attention to nearby words while still being able to attend to distant words if needed.

---

# Advantages

* ✅ No positional embeddings required.
* ✅ No extra trainable parameters.
* ✅ Handles long sequences well.
* ✅ Better extrapolation to longer contexts than many learned positional embeddings.
* ✅ Simple and computationally efficient.

---

# ALiBi vs RoPE

| Feature                       | ALiBi       | RoPE        |
| ----------------------------- | ----------- | ----------- |
| Adds positional embeddings    | ❌ No        | ❌ No        |
| Rotates Q & K                 | ❌ No        | ✅ Yes       |
| Adds bias to attention scores | ✅ Yes       | ❌ No        |
| Trainable parameters          | ❌ No        | ❌ No        |
| Supports long context         | ✅ Excellent | ✅ Excellent |

---

# Positional Encoding Comparison

| Method                          | How Position is Added                      |
| ------------------------------- | ------------------------------------------ |
| **Sinusoidal Encoding**         | Adds sine and cosine vectors to embeddings |
| **Learned Positional Encoding** | Adds trainable position embeddings         |
| **RoPE**                        | Rotates the Query and Key vectors          |
| **ALiBi**                       | Adds a linear bias to the attention scores |

---

# Interview Answer (30 Seconds)

> **ALiBi, or Attention with Linear Biases, is a positional encoding technique that adds a distance-based linear bias directly to the attention scores instead of using positional embeddings. This helps the Transformer understand the relative distance between tokens, improves performance on long sequences, and does not require any additional trainable parameters.**

---

# Easy Memory Trick

Imagine you're talking to people in a room.

* People **sitting close to you** are easier to hear.
* People **far away** are harder to hear.

ALiBi works similarly:

* **Nearby words** get a **small penalty**, so they receive more attention.
* **Farther words** get a **larger penalty**, so they receive less attention (unless they are very important).


> **ALiBi adds a distance-based linear bias to attention scores, allowing Transformers to understand relative token positions without using positional embeddings.**
