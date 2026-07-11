# Tokenization – BPE (Byte Pair Encoding)

## What is BPE?

**Byte Pair Encoding (BPE)** is a tokenization algorithm that **splits text into subwords** instead of only whole words or individual characters.

It builds a vocabulary by **repeatedly merging the most frequent pair of characters or subwords**.

---

## Simple Definition

> **BPE is a tokenization technique that creates subword tokens by repeatedly merging the most frequent character pairs.**

---

# Why Do We Need BPE?

Suppose the model sees this word:

```text
unhappiness
```

If the word is not in the vocabulary:

* Word-level tokenization → ❌ Unknown word
* Character-level tokenization → Too many tokens

BPE solves this by splitting it into meaningful subwords:

```text
un + happiness
```

or

```text
un + happy + ness
```

Now the model can understand new words by combining known subwords.

---

# How BPE Works

Suppose we have these words:

```text
low
lowest
lower
```

---

### Step 1: Split into Characters

```text
l o w
l o w e r
l o w e s t
```

---

### Step 2: Count Frequent Pairs

Most common pairs might be:

```text
l + o
o + w
```

---

### Step 3: Merge the Most Frequent Pair

Merge:

```text
l + o
```

↓

```text
lo
```

Now we have:

```text
lo w
lo w e r
lo w e s t
```

---

### Step 4: Repeat

Merge:

```text
lo + w
```

↓

```text
low
```

Now:

```text
low
lower
lowest
```

The algorithm keeps merging frequent pairs until the desired vocabulary size is reached.

---

# Example

Word:

```text
playing
```

BPE might tokenize it as:

```text
play + ing
```

Word:

```text
unbelievable
```

BPE might tokenize it as:

```text
un + believe + able
```

Even if the complete word has never been seen before, the model still understands its parts.

---

# Flow Diagram

```text
Text
   │
   ▼
Split into Characters
   │
   ▼
Find Most Frequent Pair
   │
   ▼
Merge Pair
   │
   ▼
Repeat Many Times
   │
   ▼
Subword Vocabulary
```

---

# Advantages

* ✅ Handles unknown words.
* ✅ Creates a smaller vocabulary.
* ✅ Reduces the number of `<UNK>` (unknown) tokens.
* ✅ Balances between word-level and character-level tokenization.
* ✅ Efficient for many NLP tasks.

---

# Disadvantages

* ❌ Merges are based on frequency, not meaning.
* ❌ Sometimes splits words in unnatural places.
* ❌ New languages or domains may require retraining the tokenizer.

---

# BPE vs Word-Level Tokenization

| Word-Level                   | BPE                                         |
| ---------------------------- | ------------------------------------------- |
| Uses complete words          | Uses subwords                               |
| Large vocabulary             | Smaller vocabulary                          |
| Unknown words become `<UNK>` | Unknown words are split into known subwords |
| Poor handling of rare words  | Better handling of rare words               |

---


> **Byte Pair Encoding (BPE) is a subword tokenization algorithm that builds its vocabulary by repeatedly merging the most frequent pairs of characters or subwords. It helps reduce vocabulary size, handles unknown words effectively, and allows language models to represent rare or unseen words using known subword units.**

---

# Models That Use BPE

Examples include:

* GPT-2
* RoBERTa

> **Note:** Different LLMs use different tokenizers. For example, GPT-2 uses a byte-level version of BPE, while some newer models use SentencePiece or other tokenization methods.

---

# Easy Memory Trick

Imagine building words with LEGO blocks.

Instead of storing every complete word:

```text
playing
runner
happiness
```

Store reusable pieces:

```text
play
run
happy
ing
er
ness
```

Then combine them whenever needed.

That's exactly what **BPE** does.

---


> **BPE is a subword tokenization algorithm that repeatedly merges the most frequent character pairs to build an efficient vocabulary and handle unknown words.**
