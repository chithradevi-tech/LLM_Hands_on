# Attention Score

## What is an Attention Score?

An **Attention Score** is a **number that tells how important one word is to another word**.

It measures **how well the Query (Q) matches the Key (K)**.

* **Higher score** → More attention (more relevant)
* **Lower score** → Less attention (less relevant)

---

## Simple Definition

> **Attention Score is a similarity score between the Query (Q) and Key (K). It determines how much attention the model should pay to each word.**

---

## Example

Sentence:

```text
"The cat drank the milk because it was hungry."
```

Suppose the model is processing the word **"it"**.

The Query of **"it"** is compared with the Keys of every word.

| Word    | Attention Score |
| ------- | --------------: |
| The     |            0.02 |
| Cat     |      **0.85 ⭐** |
| Drank   |            0.10 |
| Milk    |            0.05 |
| Because |            0.03 |
| Hungry  |            0.15 |

Since **"Cat"** has the **highest Attention Score**, the model understands:

> **"it" → "cat"**

---

## How is the Attention Score Calculated?

The Transformer uses the **dot product** between the **Query (Q)** and **Key (K)**.

### Formula

```text
Attention Score = Q × Kᵀ
```

Where:

* **Q** = Query vector
* **Kᵀ** = Transpose of the Key vector

A **higher dot product** means the Query and Key are more similar.

---

## After Calculating the Scores

The Attention Scores are:

1. **Scaled** (divided by √dₖ) to keep values stable.
2. Passed through **Softmax** to convert them into probabilities.
3. Used to assign weights to the **Value (V)** vectors.

```text
Query (Q)
      │
      ▼
Compare with Keys (K)
      │
      ▼
Attention Scores
      │
      ▼
Softmax
      │
      ▼
Attention Weights
      │
      ▼
Multiply with Values (V)
      │
      ▼
Final Output
```

---

## Why is the Attention Score Important?

* Helps identify the most relevant words.
* Improves context understanding.
* Enables long-range dependency learning.
* Makes Transformers more accurate than RNNs/LSTMs.

---

> **An Attention Score is a similarity score between the Query and Key vectors. It tells the model how much attention to give to each word in the sentence. The higher the score, the more relevant that word is. After calculating the scores, the model applies Softmax to convert them into attention weights, which are then used to combine the Value vectors and produce a context-aware output.**
