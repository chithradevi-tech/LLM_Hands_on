# Self-Attention

## What is Self-Attention?

**Self-Attention** is a mechanism that allows **each word in a sentence to look at all the other words** in the same sentence and decide **which ones are most important** for understanding its meaning.

In simple words:

> **Self-Attention helps each word focus on the most relevant words in the same sentence.**

---

## Why is Self-Attention Needed?

Some words depend on other words to understand their meaning.

For example:

> **"The animal didn't cross the street because it was tired."**

Question:

> **What does "it" refer to?**

The model looks at all the words and realizes that **"it"** refers to **"animal"**.

```text
The   animal   didn't   cross   the   street   because   it   was   tired
        ↑                                            │
        └────────────────────────────────────────────┘
             Self-Attention
```

Without Self-Attention, the model may not correctly understand the relationship.

---

## How Self-Attention Works

For every word:

1. Create **Query (Q)**.
2. Create **Key (K)**.
3. Create **Value (V)**.
4. Compare the **Query** with all **Keys**.
5. Calculate **Attention Scores**.
6. Apply **Softmax** to convert scores into probabilities.
7. Multiply the probabilities with the **Values**.
8. Produce a context-aware output.

---

## Flow Diagram

```text
Sentence
     │
     ▼
Create Q, K, V
     │
     ▼
Compare Q with all K
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
Multiply with V
     │
     ▼
Context-Aware Output
```

---

## Another Example

Sentence:

> **"I deposited money in the bank."**

The word **"bank"** has two meanings:

* Financial institution
* River bank

Self-Attention notices the word **"money"**, so it understands that **"bank"** means a **financial institution**.

---

## Advantages of Self-Attention

* ✅ Understands context better.
* ✅ Captures relationships between distant words.
* ✅ Processes all words in parallel (faster than RNN/LSTM).
* ✅ Improves translation, summarization, question answering, and text generation.
* ✅ Forms the foundation of Transformers and modern LLMs.

---

## Interview Answer (30 Seconds)

> **Self-Attention is a mechanism in Transformers that allows each word in a sentence to attend to every other word in the same sentence. It uses Query, Key, and Value vectors to calculate how important each word is to the current word. This helps the model understand context, capture long-range relationships, and generate more accurate outputs.**

---

## Easy Memory Trick

Think of a classroom:

* A **student (current word)** asks,

  > **"Who in the class has the information I need?"** (**Query**)
* Every other student says,

  > **"This is the information I have."** (**Key**)
* The most relevant students then share their knowledge.

  > **This shared information is the Value.**

**Self-Attention** decides **which students (words) the current student should pay the most attention to.**
