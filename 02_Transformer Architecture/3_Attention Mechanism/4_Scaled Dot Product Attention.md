# Scaled Dot-Product Attention

## What is Scaled Dot-Product Attention?

**Scaled Dot-Product Attention** is the core computation used in the **Transformer's Attention mechanism**.

It determines **which words are most important** by comparing the **Query (Q)** with the **Key (K)** and then uses the **Value (V)** vectors to produce the final output.

---

## Formula

```text
                Q × Kᵀ
Attention = Softmax(────────) × V
                 √dₖ
```

Where:

* **Q** = Query
* **K** = Key
* **V** = Value
* **Kᵀ** = Transpose of the Key matrix
* **dₖ** = Dimension (size) of the Key vector
* **√dₖ** = Scaling factor

---

## Step-by-Step Process

### Step 1: Compute Similarity

Compare **Query (Q)** with all **Keys (K)** using the dot product.

```text
Q × Kᵀ
```

This gives the **Attention Scores**.

Example:

| Word   | Score |
| ------ | ----: |
| Cat    |     8 |
| Milk   |     2 |
| Street |     1 |

Higher score = More relevant.

---

### Step 2: Scale the Scores

Divide each score by **√dₖ**.

```text
(Q × Kᵀ) / √dₖ
```

### Why Scale?

If the vector dimension is large, the dot-product values become very large.

Large values make the **Softmax** function produce extremely peaked probabilities, which can make training unstable and learning slower.

Scaling keeps the values in a reasonable range.

---

### Step 3: Apply Softmax

Convert the scaled scores into probabilities.

Example:

| Word   | Probability |
| ------ | ----------: |
| Cat    |        0.80 |
| Milk   |        0.15 |
| Street |        0.05 |

Now the probabilities add up to **1**.

---

### Step 4: Multiply by Value (V)

Use the probabilities as weights to combine the **Value** vectors.

```text
Output = Attention Weights × V
```

Words with higher probabilities contribute more to the final representation.

---

# Complete Flow

```text
Input
   │
   ▼
Create Q, K, V
   │
   ▼
Q × Kᵀ
   │
   ▼
Divide by √dₖ (Scaling)
   │
   ▼
Softmax
   │
   ▼
Attention Weights
   │
   ▼
Multiply with V
   │
   ▼
Final Output
```

---

## Why is it Called "Scaled Dot-Product Attention"?

* **Dot Product** → Computes the similarity between **Q** and **K**.
* **Scaled** → Divides the score by **√dₖ** to keep values stable.
* **Attention** → Focuses on the most relevant words.

---

## Advantages

* ✅ Understands context better.
* ✅ Focuses on important words.
* ✅ Stable training due to scaling.
* ✅ Fast and efficient because it supports parallel computation.
* ✅ Forms the foundation of modern Transformers and LLMs.

---

> **Scaled Dot-Product Attention is the mechanism used in Transformers to determine how much attention one word should pay to other words. It first computes the similarity between the Query and Key using a dot product, scales the result by dividing it by √dₖ to keep the values stable, applies Softmax to convert the scores into probabilities, and finally uses those probabilities to weight the Value vectors. This helps the model focus on the most relevant words and understand context effectively.**
