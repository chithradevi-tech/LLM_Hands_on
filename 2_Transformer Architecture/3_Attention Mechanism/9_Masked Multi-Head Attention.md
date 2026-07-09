# Masked Multi-Head Attention

## What is Masked Multi-Head Attention?

**Masked Multi-Head Attention** is a special type of **Self-Attention** used in the **decoder** of a Transformer.

It **prevents the model from looking at future words** while predicting the next word.

---

## Simple Definition

> **Masked Multi-Head Attention allows the model to attend only to the current and previous words, but not future words.**

---

## Why is Masking Needed?

When generating text, the model should predict the next word **without knowing future words**.

For example:

Sentence:

```text
I love AI
```

While predicting **"love"**, the model should **not** look at **"AI"**.

Otherwise, it would be cheating because it already knows the answer.

---

## Example

Sentence:

```text
I love AI
```

### Predicting "love"

The model can see:

```text
I   love
```

❌ It **cannot** see:

```text
AI
```

---

### Predicting "AI"

The model can see:

```text
I   love   AI
```

Because "AI" is now the current word.

---

## Masking Visualization

Without Mask:

```text
          I   Love   AI
I         ✔    ✔     ✔
Love      ✔    ✔     ✔
AI        ✔    ✔     ✔
```

Every word can attend to every other word.

---

With Mask:

```text
          I   Love   AI
I         ✔    ✖     ✖
Love      ✔    ✔     ✖
AI        ✔    ✔     ✔
```

* ✔ = Allowed
* ✖ = Blocked (future words)

This is called a **causal mask** or **look-ahead mask**.

---

## How It Works

1. Create **Query (Q), Key (K), and Value (V)**.
2. Calculate Attention Scores.
3. Apply a **mask** to block future positions.
4. Apply **Softmax**.
5. Multiply with **Value (V)**.
6. Produce the output.

---

## Flow Diagram

```text
Input
   │
   ▼
Create Q, K, V
   │
   ▼
Attention Scores
   │
   ▼
Apply Mask
(Block Future Words)
   │
   ▼
Softmax
   │
   ▼
Multiply with Values
   │
   ▼
Output
```

---

## Where is Masked Multi-Head Attention Used?

| Model          | Uses Masked Attention?                           |
| -------------- | ------------------------------------------------ |
| **Encoder**    | ❌ No                                             |
| **Decoder**    | ✅ Yes                                            |
| **GPT Models** | ✅ Yes (decoder-only architecture)                |
| **BERT**       | ❌ No (uses bidirectional self-attention instead) |

---

## Why is it Important?

* ✅ Prevents the model from cheating.
* ✅ Enables next-word prediction.
* ✅ Makes text generation possible.
* ✅ Used in autoregressive language models like GPT.

---

## Self-Attention vs Masked Self-Attention

| Self-Attention             | Masked Self-Attention         |
| -------------------------- | ----------------------------- |
| Can attend to all words    | Cannot attend to future words |
| Mainly used in the encoder | Used in the decoder           |
| Bidirectional              | Left-to-right (causal)        |

---

> **Masked Multi-Head Attention is a decoder attention mechanism that prevents the model from attending to future words during text generation. A causal mask is applied to the attention scores before Softmax so that each word can only attend to itself and the previous words. This enables the model to generate text one token at a time without using future information.**

---

## Easy Memory Trick

Imagine you're taking an exam.

* You can see the **current question**.
* You can remember the **previous questions**.
* ❌ You **cannot** see the **next questions**.

**Masked Multi-Head Attention works the same way—it allows the model to look only at the current and previous words, never future words.**
