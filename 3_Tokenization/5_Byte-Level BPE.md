# Tokenization – Byte-Level BPE

## What is Byte-Level BPE?

**Byte-Level BPE (Byte-Level Byte Pair Encoding)** is a tokenization algorithm that first converts text into **bytes** and then applies **BPE (Byte Pair Encoding)** on those bytes.

Unlike normal BPE, it can tokenize **any text**, even if it contains unseen words, emojis, or special characters.

---

## Simple Definition

> **Byte-Level BPE converts text into bytes first and then applies BPE, allowing it to tokenize any text without producing unknown (`<UNK>`) tokens.**

---

# Why Do We Need Byte-Level BPE?

Normal BPE may struggle with:

* Rare words
* Emojis 😊
* Symbols (@, #, %)
* Different languages

Byte-Level BPE avoids this because **every character can be represented as bytes**.

Example:

```text id="c6t2yt"
Hello 😊
```

↓

Convert to bytes

↓

Apply BPE

↓

Generate tokens

So, **every input can be tokenized**.

---

# How Byte-Level BPE Works

### Step 1: Input Text

```text id="21zhrk"
playing
```

---

### Step 2: Convert to Bytes

Every character is converted into bytes.

```text id="vuyy9x"
p
l
a
y
i
n
g
```

↓

Byte values (example):

```text id="tl0bjlwm"
112
108
97
121
105
110
103
```

---

### Step 3: Apply BPE

Frequently occurring byte pairs are merged repeatedly.

Example:

```text id="6u0gmm"
play
ing
```

---

### Step 4: Convert to Token IDs

```text id="m8pyjd"
play → 1456
ing  → 982
```

These token IDs are sent to the Transformer.

---

# Flow Diagram

```text id="dn2yjlwm"
Text
 │
 ▼
Convert to Bytes
 │
 ▼
Apply Byte Pair Encoding
 │
 ▼
Subword Tokens
 │
 ▼
Token IDs
```

---

# Example

Input:

```text id="0pm7u8"
ChatGPT 😊
```

Even though 😊 is an emoji, Byte-Level BPE can tokenize it because it is first converted into bytes.

There is **no need for an `<UNK>` token**.

---

# Advantages

* ✅ Can tokenize any Unicode text.
* ✅ Handles emojis and special characters.
* ✅ No unknown (`<UNK>`) tokens.
* ✅ Smaller and efficient vocabulary.
* ✅ Good for multilingual text.

---

# Disadvantages

* ❌ Tokenization can be slightly more complex.
* ❌ Common words may sometimes be split into more tokens than with other methods.

---

# BPE vs Byte-Level BPE

| Feature                    | BPE      | Byte-Level BPE           |
| -------------------------- | -------- | ------------------------ |
| Works on characters        | ✅ Yes    | ❌ No (works on bytes)    |
| Handles unknown characters | Limited  | ✅ Yes                    |
| Handles emojis             | Limited  | ✅ Yes                    |
| Uses bytes                 | ❌ No     | ✅ Yes                    |
| `<UNK>` tokens             | Possible | Very rare or unnecessary |

---

# Models That Use Byte-Level BPE

Examples include:

* GPT-2
* RoBERTa

---

> **Byte-Level BPE is a tokenization algorithm that first converts text into bytes and then applies Byte Pair Encoding. Since every character can be represented as bytes, it can tokenize any text, including rare words, emojis, and special symbols, without relying on unknown (`<UNK>`) tokens. It is used in models like GPT-2 and RoBERTa.**

---

# Easy Memory Trick

Imagine two approaches:

* **BPE** → Works with **letters**.
* **Byte-Level BPE** → Works with **computer bytes**.

Since every character is stored as bytes in a computer:

```text id="rmjlwm"
Text
 ↓
Bytes
 ↓
BPE
 ↓
Tokens
```

No matter what the input is, Byte-Level BPE can process it.

---

# Quick Comparison

| Tokenizer          | Main Idea                              | Example Model         |
| ------------------ | -------------------------------------- | --------------------- |
| **BPE**            | Merge frequent character pairs         | GPT-2 (basic concept) |
| **Byte-Level BPE** | Convert text to bytes, then apply BPE  | GPT-2, RoBERTa        |
| **WordPiece**      | Probability-based subword tokenization | BERT                  |
| **SentencePiece**  | Learns subwords directly from raw text | Llama, T5             |
| **Unigram**        | Removes low-probability subwords       | T5, ALBERT            |

---

> **Byte-Level BPE is a tokenizer that converts text into bytes before applying BPE, enabling it to handle any Unicode text—including emojis and rare characters—without unknown tokens.**
