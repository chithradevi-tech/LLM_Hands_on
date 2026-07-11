# Tokenization – WordPiece

## What is WordPiece?

**WordPiece** is a **subword tokenization algorithm** that splits words into **smaller meaningful subwords**.

Unlike **BPE**, which merges the most frequent character pairs, **WordPiece chooses merges that maximize the probability of the training data** (i.e., it selects the most useful subwords for the language model).

---

## Simple Definition

> **WordPiece is a subword tokenization algorithm that breaks words into meaningful subwords to efficiently handle unknown and rare words.**

---

# Why Do We Need WordPiece?

Suppose the model sees this word:

```text
unhappiness
```

If it doesn't exist in the vocabulary:

* Word-level tokenization → ❌ Unknown word
* Character-level tokenization → Too many tokens

WordPiece splits it into known subwords:

```text
un + ##happy + ##ness
```

The model understands the word by combining the meanings of these subwords.

---

# How WordPiece Works

Suppose the vocabulary contains:

```text
play
##ing
run
##ner
happy
##ness
un
```

Now tokenize:

```text
playing
```

↓

```text
play + ##ing
```

Tokenize:

```text
runner
```

↓

```text
run + ##ner
```

Tokenize:

```text
unhappiness
```

↓

```text
un + ##happy + ##ness
```

---

# What does "##" mean?

The prefix **`##`** means:

> **This subword continues the previous token.**

Example:

```text
playing
```

↓

```text
play
##ing
```

* `play` → Start of a word
* `##ing` → Continuation of the same word

---

# Flow Diagram

```text
Text
   │
   ▼
Split into Words
   │
   ▼
Find Matching Subwords
   │
   ▼
Break into WordPieces
   │
   ▼
Token IDs
```

---

# Example

Sentence:

```text
I am playing football.
```

Tokenization:

```text
I
am
play
##ing
football
```

Another example:

```text
unbelievable
```

↓

```text
un
##believe
##able
```

---

# Advantages

* ✅ Handles unknown words.
* ✅ Reduces vocabulary size.
* ✅ Learns meaningful subwords.
* ✅ Better handling of rare words.
* ✅ Widely used in NLP models.

---

# Disadvantages

* ❌ Can split words into multiple tokens.
* ❌ Slightly slower than word-level tokenization.
* ❌ Vocabulary must be trained beforehand.

---

# BPE vs WordPiece

| BPE                                      | WordPiece                                                      |
| ---------------------------------------- | -------------------------------------------------------------- |
| Merges the most frequent character pairs | Chooses merges that best improve the language model likelihood |
| Frequency-based                          | Probability-based                                              |
| Creates subword vocabulary               | Creates subword vocabulary                                     |
| Used in GPT-2 (byte-level BPE)           | Used in BERT                                                   |

---

# Models That Use WordPiece

Examples include:

* BERT
* DistilBERT

---

> **WordPiece is a subword tokenization algorithm that splits words into smaller meaningful units. It selects subwords based on how well they improve the language model rather than just frequency. This helps reduce vocabulary size, handle unknown words, and improve the model's understanding of rare words. In WordPiece, subwords that continue a word are prefixed with `##`, such as `play` and `##ing`.**

---

# Easy Memory Trick

Imagine a puzzle.

Instead of storing every complete word:

```text
playing
runner
unhappiness
```

Store reusable puzzle pieces:

```text
play
##ing
run
##ner
un
##happy
##ness
```

The model joins these pieces whenever it encounters a new word.

---

> **WordPiece is a probability-based subword tokenization algorithm that splits words into meaningful subwords, helping models handle unknown and rare words efficiently.**
