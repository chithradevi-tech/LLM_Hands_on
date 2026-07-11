# Cross-Attention

## What is Cross-Attention?

**Cross-Attention** is an attention mechanism where the model **focuses on information from another sequence** instead of the same sequence.

* **Self-Attention** → A sentence attends to **itself**.
* **Cross-Attention** → One sequence attends to **another sequence**.

---

## Simple Definition

> **Cross-Attention allows one sequence to attend to another sequence to gather relevant information.**

---

## Example (Translation)

Suppose we want to translate:

**English:**

> **"I love AI."**

**French Output:**

> **"J'aime l'IA."**

### Encoder

The encoder processes:

```text id="2wjgbt"
I
Love
AI
```

### Decoder

While generating:

```text id="kz8g2k"
J'aime
```

The decoder asks:

> **"Which words from the English sentence should I look at?"**

It attends to the encoder output.

This is **Cross-Attention**.

---

## How Cross-Attention Works

Unlike Self-Attention:

* **Query (Q)** comes from the **Decoder**.
* **Key (K)** comes from the **Encoder**.
* **Value (V)** also comes from the **Encoder**.

```text id="i0j9ob"
Decoder
   │
 Query (Q)
   │
   ▼
Compare with Encoder Keys (K)
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
Encoder Values (V)
   │
   ▼
Decoder Output
```

---

## Self-Attention vs Cross-Attention

| Feature   | Self-Attention                               | Cross-Attention                    |
| --------- | -------------------------------------------- | ---------------------------------- |
| Query (Q) | Same sequence                                | Decoder                            |
| Key (K)   | Same sequence                                | Encoder                            |
| Value (V) | Same sequence                                | Encoder                            |
| Purpose   | Understand relationships within one sentence | Connect input and output sequences |

---

## Where is Cross-Attention Used?

* 🌍 Machine Translation
* 📝 Text Summarization
* ❓ Question Answering
* 🖼️ Image Captioning
* 🎤 Speech-to-Text
* 📄 Encoder–Decoder Transformer models

---

## Which Transformer Models Use Cross-Attention?

| Model                            | Uses Cross-Attention? |
| -------------------------------- | --------------------- |
| Encoder-only (e.g., BERT)        | ❌ No                  |
| Decoder-only (e.g., GPT)         | ❌ No                  |
| Encoder–Decoder (e.g., T5, BART) | ✅ Yes                 |

---

## Interview Answer (30 Seconds)

> **Cross-Attention is an attention mechanism where the Query comes from one sequence, such as the decoder, while the Key and Value come from another sequence, such as the encoder. It helps the decoder focus on the most relevant parts of the input while generating the output. Cross-Attention is mainly used in encoder–decoder Transformer models for tasks like machine translation and text summarization.**

---

## Easy Memory Trick

* **Self-Attention** = **"Look at yourself."**
* **Cross-Attention** = **"Look at someone else."**

```text id="g4j4zm"
Self-Attention
Sentence A  ─────► Sentence A

Cross-Attention
Sentence B  ─────► Sentence A
      Q            K & V
```

> **Self-Attention learns relationships within the same sequence, whereas Cross-Attention learns relationships between two different sequences.**
