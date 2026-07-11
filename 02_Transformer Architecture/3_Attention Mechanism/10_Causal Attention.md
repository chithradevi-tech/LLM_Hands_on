# Causal Attention

## What is Causal Attention?

**Causal Attention** is an attention mechanism that allows the model to **look only at the current word and previous words**, but **not future words**.

It is mainly used in **decoder-only models** like GPT.

---

## Simple Definition

> **Causal Attention prevents the model from seeing future words while predicting the next word.**

---

## Why is Causal Attention Needed?

When generating text, the model should predict the next word **without knowing future words**.

For example:

Sentence:

```text
I love AI
```

Suppose the model is predicting **"love"**.

It can see:

```text
I
```

It **cannot** see:

```text
AI
```

Otherwise, the model would already know the answer.

---

# Example

Sentence:

```text
I love AI
```

### Predicting "I"

Can see:

```text
I
```

Cannot see:

```text
love AI
```

---

### Predicting "love"

Can see:

```text
I love
```

Cannot see:

```text
AI
```

---

### Predicting "AI"

Can see:

```text
I love AI
```

No future words remain.

---

# Causal Mask

The model uses a **causal mask** (also called a **look-ahead mask**) to block future words.

Without Mask:

```text
        I   Love   AI
I       ✔    ✔     ✔
Love    ✔    ✔     ✔
AI      ✔    ✔     ✔
```

Every word can see every other word.

---

With Causal Mask:

```text
        I   Love   AI
I       ✔    ✖     ✖
Love    ✔    ✔     ✖
AI      ✔    ✔     ✔
```

✔ = Allowed

✖ = Blocked

---

# How It Works

```text
Input
   │
   ▼
Create Q, K, V
   │
   ▼
Calculate Attention Scores
   │
   ▼
Apply Causal Mask
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

# Where is Causal Attention Used?

| Model                  | Uses Causal Attention? |
| ---------------------- | ---------------------- |
| GPT                    | ✅ Yes                  |
| Llama                  | ✅ Yes                  |
| Gemma                  | ✅ Yes                  |
| BERT                   | ❌ No                   |
| Encoder-Decoder Models | ✅ In the decoder only  |

---

# Causal Attention vs Self-Attention

| Self-Attention              | Causal Attention                        |
| --------------------------- | --------------------------------------- |
| Can see all words           | Can see only previous and current words |
| Used in Encoder             | Used in Decoder-only models             |
| Bidirectional               | Left-to-right                           |
| Good for understanding text | Good for generating text                |

---

# Is Causal Attention the Same as Masked Self-Attention?

**Yes.**

These two terms are often used interchangeably.

* **Masked Self-Attention** describes **how** it's implemented (using a mask).
* **Causal Attention** describes **why** it's used (to preserve the left-to-right causal order).

Both prevent the model from looking at future tokens.

---

> **Causal Attention is a type of self-attention where each token can attend only to itself and the previous tokens, but not future tokens. This is achieved using a causal, or look-ahead, mask. It is used in decoder-only models like GPT to ensure the model predicts the next word without accessing future information, enabling autoregressive text generation.**

---

# Easy Memory Trick

Imagine you're **writing a sentence**.

While writing the next word:

* ✅ You can read what you've already written.
* ✅ You know the current word.
* ❌ You cannot read words that you haven't written yet.

**Causal Attention works exactly the same way.** It only allows the model to use the **past and present**, never the **future**.
