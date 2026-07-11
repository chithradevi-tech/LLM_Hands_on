# Tokenization – Unigram Language Model

## What is Unigram?

**Unigram** is a **subword tokenization algorithm** that starts with a **large vocabulary** and **removes the least useful subwords** until it reaches the desired vocabulary size.

Unlike **BPE**, which builds the vocabulary by **merging** tokens, **Unigram builds it by removing** tokens.

---

## Simple Definition

> **Unigram is a probability-based tokenization algorithm that chooses the most likely combination of subwords for a word.**

---

# Why Do We Need Unigram?

Suppose we have the word:

```text
unhappiness
```

Instead of using one fixed split, Unigram considers **multiple possible ways** to split the word and selects the one with the **highest probability**.

Example:

```text
Option 1:
un + happy + ness

Option 2:
unhappi + ness

Option 3:
un + happi + ness
```

The model picks the **best (most probable)** segmentation.

---

# How Unigram Works

### Step 1: Start with a Large Vocabulary

Example vocabulary:

```text
un
happy
happi
ness
playing
play
ing
runner
run
ner
```

---

### Step 2: Assign a Probability

Each subword is given a probability based on the training data.

Example:

| Subword | Probability |
| ------- | ----------: |
| play    |        0.90 |
| ing     |        0.85 |
| playing |        0.20 |

---

### Step 3: Tokenize the Word

Word:

```text
playing
```

Possible splits:

```text
Option 1:
play + ing

Option 2:
playing
```

Since:

```text
P(play) × P(ing)
>
P(playing)
```

The tokenizer chooses:

```text
play + ing
```

---

### Step 4: Remove Low-Probability Tokens

The least useful subwords are removed until the vocabulary reaches the desired size.

---

# Flow Diagram

```text
Large Vocabulary
        │
        ▼
Assign Probabilities
        │
        ▼
Find Best Subword Split
        │
        ▼
Remove Low-Probability Tokens
        │
        ▼
Final Vocabulary
```

---

# Example

Word:

```text
unbelievable
```

Possible tokenization:

```text
un
believe
able
```

Another example:

```text
internationalization
```

↓

```text
inter
nation
al
ization
```

The tokenizer selects the segmentation with the **highest overall probability**.

---

# Advantages

* ✅ Handles unknown words well.
* ✅ Produces natural subword splits.
* ✅ Probability-based, not just frequency-based.
* ✅ Works well for multilingual models.
* ✅ Flexible and robust.

---

# Disadvantages

* ❌ Slightly slower than BPE.
* ❌ Requires estimating probabilities during training.
* ❌ More computationally expensive.

---

# BPE vs WordPiece vs Unigram

| Feature                       | BPE                    | WordPiece               | Unigram                           |
| ----------------------------- | ---------------------- | ----------------------- | --------------------------------- |
| Builds vocabulary by          | Merging frequent pairs | Selecting useful merges | Removing low-probability subwords |
| Based on                      | Frequency              | Probability             | Probability                       |
| Multiple tokenization options | ❌ No                   | ❌ No                    | ✅ Yes                             |
| Chooses best segmentation     | ❌                      | ❌                       | ✅                                 |

---

# Models That Use Unigram

Examples include:

* T5
* ALBERT

> **Note:** Unigram is commonly implemented using **SentencePiece**.

---

> **Unigram is a probability-based subword tokenization algorithm. It starts with a large vocabulary and gradually removes low-probability subwords. During tokenization, it evaluates multiple possible segmentations of a word and chooses the one with the highest probability. This makes it effective for handling rare words and multilingual text.**

---

# Easy Memory Trick

Imagine you have a box of LEGO pieces.

* **BPE** → Keeps **adding** pieces together.
* **Unigram** → Starts with **many pieces** and **removes** the unnecessary ones.

So remember:

* **BPE = Merge**
* **WordPiece = Best Merge (probability-guided)**
* **Unigram = Remove low-probability pieces**

---

# Quick Comparison (Interview)

| Tokenizer         | Main Idea                                                               | Used By          |
| ----------------- | ----------------------------------------------------------------------- | ---------------- |
| **BPE**           | Merge the most frequent pairs                                           | GPT-2            |
| **WordPiece**     | Choose subwords based on probability                                    | BERT             |
| **SentencePiece** | Learn subwords directly from raw text                                   | Llama, T5, Gemma |
| **Unigram**       | Remove low-probability subwords and choose the most likely segmentation | T5, ALBERT       |

---


> **Unigram is a probability-based subword tokenization algorithm that starts with a large vocabulary, removes low-probability tokens, and selects the most likely subword segmentation for each word.**
