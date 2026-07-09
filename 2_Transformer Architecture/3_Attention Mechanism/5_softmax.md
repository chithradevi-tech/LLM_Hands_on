# Softmax

## What is Softmax?

**Softmax** is an activation function that **converts a list of numbers (scores) into probabilities**.

The probabilities are:

* Between **0 and 1**
* Always add up to **1 (100%)**

In the Attention mechanism, **Softmax converts the Attention Scores into Attention Weights**.

---

## Simple Definition

> **Softmax converts raw scores into probabilities, showing how much attention should be given to each word.**

---

## Example

Suppose the Attention Scores are:

| Word   | Score |
| ------ | ----: |
| Cat    |     8 |
| Milk   |     2 |
| Street |     1 |

These are just scores, not probabilities.

After applying **Softmax**:

| Word   | Probability |
| ------ | ----------: |
| Cat    |    **0.84** |
| Milk   |    **0.11** |
| Street |    **0.05** |

Notice:

```text
0.84 + 0.11 + 0.05 = 1.00
```

Now the model knows:

* Give **84% attention** to **Cat**
* Give **11% attention** to **Milk**
* Give **5% attention** to **Street**

---

## Why is Softmax Needed?

Without Softmax:

```text
Scores:
8, 2, 1
```

The model doesn't know how important each score is relative to the others.

With Softmax:

```text
Probabilities:
0.84, 0.11, 0.05
```

Now the model has normalized weights that can be used to combine the **Value (V)** vectors.

---

## Softmax in Attention

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
Attention Weights (Probabilities)
      │
      ▼
Multiply with Values (V)
      │
      ▼
Final Output
```

---

## Softmax Formula

[
\text{Softmax}(x_i)=\frac{e^{x_i}}{\sum_{j=1}^{n}e^{x_j}}
]

Where:

* **e** = Euler's number (≈ 2.718)
* **xᵢ** = Current score
* **Σ** = Sum of all exponential scores

You don't need to memorize the formula for most interviews—understanding the concept is usually enough.

---

## Advantages of Softmax

* ✅ Converts scores into probabilities.
* ✅ All probabilities are between **0 and 1**.
* ✅ The probabilities always sum to **1**.
* ✅ Helps the model decide which words deserve more attention.

---

## Interview Answer (30 Seconds)

> **Softmax is an activation function that converts raw attention scores into probabilities. These probabilities, called attention weights, indicate how much attention the model should give to each word. The values are between 0 and 1, and they always sum to 1, making it easy for the Transformer to focus on the most relevant words.**

---

## Easy Memory Trick

* **Attention Score** → Raw marks in an exam.
* **Softmax** → Converts those marks into percentages.
* **Attention Weight** → The final percentage used to decide which words are most important.

### Flow to Remember

```text
Query + Key
      ↓
Attention Scores
      ↓
Softmax
      ↓
Attention Weights (Probabilities)
      ↓
Multiply with Value
      ↓
Final Output
```

> **Softmax converts attention scores into probabilities so the Transformer knows how much attention to give to each word.**
