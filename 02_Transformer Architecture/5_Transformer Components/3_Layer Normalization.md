# Transformer Component – Layer Normalization (LayerNorm)

## What is Layer Normalization?

**Layer Normalization (LayerNorm)** is a technique used to **normalize the values of a token's features**, making the training process **more stable and faster**.

It prevents values from becoming too large or too small as they pass through the network.

---

## Simple Definition

> **Layer Normalization normalizes the output of a layer so that the Transformer trains faster, more stably, and more accurately.**

---

# Why Do We Need Layer Normalization?

During training, the values produced by different layers can vary a lot.

For example:

```text
Token A → [120, 250, 15, 80]
```

These values have very different scales.

LayerNorm adjusts them to a similar scale, making learning easier.

After LayerNorm:

```text
Token A → [-0.8, 1.2, -1.1, 0.7]
```

Now the values are normalized.

---

# Where is LayerNorm Used?

In a Transformer block, LayerNorm is applied around the major sub-layers.

```text
Input
   │
   ▼
Multi-Head Attention
   │
   ▼
Add (Residual Connection)
   │
   ▼
Layer Normalization
   │
   ▼
Feed Forward Network
   │
   ▼
Add (Residual Connection)
   │
   ▼
Layer Normalization
   │
   ▼
Output
```

> Modern Transformers often use **Pre-LayerNorm**, where LayerNorm is applied **before** the attention and FFN blocks, but the goal remains the same: stable training.

---

# How Layer Normalization Works

For each token:

1. Compute the **mean** of its features.
2. Compute the **variance** (or standard deviation).
3. Normalize the features.
4. Apply learnable scale (**γ**) and shift (**β**) parameters.

---

# Example

Suppose a token has these values:

```text
[10, 20, 30, 40]
```

LayerNorm converts them into normalized values such as:

```text
[-1.34, -0.45, 0.45, 1.34]
```

The exact numbers depend on the calculation, but the idea is that the values are centered and scaled.

---

# Advantages

* ✅ Makes training more stable.
* ✅ Speeds up convergence.
* ✅ Reduces exploding or shrinking values.
* ✅ Improves model performance.
* ✅ Works well even with small batch sizes.

---

# Layer Normalization vs Batch Normalization

| Layer Normalization                 | Batch Normalization            |
| ----------------------------------- | ------------------------------ |
| Normalizes each token independently | Normalizes across the batch    |
| Works well for NLP and Transformers | Common in CNNs and image tasks |
| Does not depend on batch size       | Depends on batch statistics    |
| Used in Transformers                | Used mainly in computer vision |

---


> **Layer Normalization is a technique used in Transformers to normalize the features of each token. It stabilizes the values flowing through the network, leading to faster and more stable training. Unlike Batch Normalization, Layer Normalization works independently for each token and does not rely on batch statistics, making it well suited for NLP models like Transformers.**

---

# Easy Memory Trick

Imagine students taking an exam.

* One exam is **too easy** (very high marks).
* Another exam is **too difficult** (very low marks).

To compare students fairly, the teacher **normalizes** the marks.

Similarly, **Layer Normalization normalizes the feature values** so the Transformer can learn consistently and efficiently.


> **Layer Normalization normalizes each token's features to stabilize and speed up Transformer training.**
