# Attention Mechanism – Query (Q)

## What is Query (Q)?

A **Query (Q)** is a **question or request** that a word asks to find the most relevant words in the sentence.

Think of it as:

> **"Which other words should I pay attention to in order to understand my meaning?"**

---

## Easy Analogy

Imagine you are in a library.

* **Query (Q)** → The book title you are searching for.
* **Key (K)** → The labels on all the books.
* **Value (V)** → The actual content inside each book.

You compare your **Query** with all the **Keys** to find the best match, then read the corresponding **Value**.

---

## Example

Sentence:

```text
The cat drank the milk because it was hungry.
```

Suppose the model is processing the word **"it"**.

### Query (Q)

The word **"it"** asks:

> **"Who am I referring to?"**

The Query of **"it"** is compared with the Keys of all the other words.

```
The   cat   drank   the   milk   because   it   was   hungry
              ↑
           Query (it)
```

The model finds that **"cat"** is the best match.

So **"it" → "cat"**.

---

## Simple Definition

> **Query (Q) is a vector representing what the current word is looking for from the other words in the sentence.**

---

## In Self-Attention

Every token generates three vectors:

* **Q (Query)** → What am I looking for?
* **K (Key)** → What information do I have?
* **V (Value)** → What information should I provide?

The model compares **Query** with all **Keys**.

The best matching **Values** are used to understand the word.

---

## Flow

```text
Current Word
      ↓
Create Query (Q)
      ↓
Compare with all Keys (K)
      ↓
Find highest match
      ↓
Take corresponding Values (V)
      ↓
Generate better representation
```

---


> **Query (Q) is a vector that represents what the current word is searching for in the sentence. During self-attention, the Query of the current word is compared with the Keys of all words to identify the most relevant ones. The corresponding Values are then combined to produce a context-aware representation of the word.**

### Easy Memory Trick

* **Q (Query)** = **Question** → *"What am I looking for?"*
* **K (Key)** = **Keyword** → *"What information do I have?"*
* **V (Value)** = **Value** → *"What information should I provide?"*
