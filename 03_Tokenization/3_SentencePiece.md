# Tokenization – SentencePiece

## What is SentencePiece?

**SentencePiece** is a **subword tokenization algorithm** that tokenizes **raw text directly**, without requiring the text to be split into words first.

It can use algorithms such as **BPE** or **Unigram Language Model** internally.

---

## Simple Definition

> **SentencePiece is a tokenization method that learns subword units directly from raw text, without depending on spaces between words.**

---

# Why Do We Need SentencePiece?

Many languages (like **Japanese, Chinese, and Thai**) do not use spaces between words.

Example:

```text id="vsudw6"
私は学生です
```

Where does one word end and the next begin?

Traditional tokenizers struggle because they first split on spaces.

SentencePiece works directly on the raw text, so it can tokenize such languages effectively.

---

# How SentencePiece Works

### Step 1: Input Raw Text

```text id="gnjlwm"
I love AI
```

SentencePiece does **not** first split into words.

---

### Step 2: Learn Subwords

It learns common subwords from the training data.

Example:

```text id="vrgxj0"
I
love
AI
```

or

```text id="cl5n7u"
play
ing
```

depending on what it learns.

---

### Step 3: Tokenize

Word:

```text id="xscf1h"
playing
```

↓

Possible tokens:

```text id="5gzngz"
play
ing
```

or

```text id="xj8p9e"
playing
```

depending on the learned vocabulary.

---

# Special Character "▁"

SentencePiece uses the symbol **`▁`** (underscore-like character) to represent the **beginning of a new word**.

Example:

Sentence:

```text id="6dfmsb"
I love AI
```

Tokenization:

```text id="4jx84l"
▁I
▁love
▁AI
```

Example:

```text id="eiybch"
playing football
```

↓

```text id="w8mmpa"
▁playing
▁football
```

Here:

* **`▁`** = Start of a new word.

Unlike WordPiece, SentencePiece **does not use `##`**.

---

# Flow Diagram

```text id="9g4kpm"
Raw Text
     │
     ▼
Learn Subwords
     │
     ▼
Create Vocabulary
     │
     ▼
Tokenize Text
     │
     ▼
Token IDs
```

---

# Example

Sentence:

```text id="ewb7rc"
Machine learning is amazing
```

Possible tokens:

```text id="0wpjlwm"
▁Machine
▁learn
ing
▁is
▁amazing
```

---

# Advantages

* ✅ Works directly on raw text.
* ✅ Does not depend on spaces.
* ✅ Supports many languages.
* ✅ Handles unknown words well.
* ✅ Creates an efficient subword vocabulary.

---

# Disadvantages

* ❌ Requires training to build its vocabulary.
* ❌ A word may be split differently depending on the learned vocabulary.

---

# BPE vs WordPiece vs SentencePiece

| Feature                           | BPE       | WordPiece | SentencePiece |
| --------------------------------- | --------- | --------- | ------------- |
| Uses subwords                     | ✅         | ✅         | ✅             |
| Splits by spaces first            | ✅ Usually | ✅ Usually | ❌ No          |
| Works on raw text                 | ❌         | ❌         | ✅             |
| Special marker                    | None      | `##`      | `▁`           |
| Good for languages without spaces | ❌         | ❌         | ✅             |

---

# Models That Use SentencePiece

Examples include:

* T5
* Llama
* Gemma

---

> **SentencePiece is a subword tokenization algorithm that learns subword units directly from raw text without relying on spaces. It supports algorithms like BPE and Unigram internally and is especially useful for multilingual models and languages that do not use spaces between words. SentencePiece marks the beginning of each word using the `▁` symbol.**

---

# Easy Memory Trick

Imagine reading a paragraph **without spaces**.

Traditional tokenizers first look for spaces to split words.

SentencePiece says:

> **"I don't need spaces. I'll learn the word boundaries myself."**

Also remember:

* **WordPiece** → `##` = continuation of a word.
* **SentencePiece** → `▁` = start of a new word.

---

> **SentencePiece is a language-independent subword tokenizer that learns tokens directly from raw text without relying on spaces, making it ideal for multilingual LLMs.**
