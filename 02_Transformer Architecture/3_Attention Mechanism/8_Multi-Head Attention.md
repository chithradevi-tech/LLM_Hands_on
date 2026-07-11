# Multi-Head Attention

## What is Multi-Head Attention?

**Multi-Head Attention** is an extension of the Attention mechanism where the Transformer uses **multiple attention heads** instead of just one.

Each attention head **focuses on different relationships** in the same sentence.

Finally, the outputs from all heads are **combined** to produce a richer understanding of the sentence.

---

## Simple Definition

> **Multi-Head Attention allows the model to look at a sentence from multiple perspectives at the same time.**

---

## Why Do We Need Multiple Heads?

If we use **only one attention head**, the model may focus on only one type of relationship.

With **multiple heads**, each head can learn something different, such as:

* Grammar
* Meaning
* Subject–verb relationships
* Long-distance dependencies

This helps the model understand language more accurately.

---

## Example

Sentence:

> **"The cat sat on the mat because it was tired."**

Different attention heads may focus on different things:

| Attention Head | Focus                                     |
| -------------- | ----------------------------------------- |
| **Head 1**     | "it" → "cat" (pronoun reference)          |
| **Head 2**     | "sat" → "cat" (subject–verb relationship) |
| **Head 3**     | "on" → "mat" (location relationship)      |
| **Head 4**     | Overall sentence meaning                  |

Each head captures a different aspect of the sentence.

---

## How Multi-Head Attention Works

1. Create **Query (Q), Key (K), and Value (V)**.
2. Split them into multiple heads.
3. Each head performs **Scaled Dot-Product Attention** independently.
4. Concatenate (combine) the outputs from all heads.
5. Apply a final linear transformation to produce the output.

---

## Flow Diagram

```text
Input
   │
   ▼
Create Q, K, V
   │
   ▼
Split into Multiple Heads
   │
   ├──► Head 1 → Attention
   ├──► Head 2 → Attention
   ├──► Head 3 → Attention
   └──► Head 4 → Attention
          │
          ▼
Concatenate Outputs
          │
          ▼
Linear Layer
          │
          ▼
Final Output
```

---

## Formula

[
\text{MultiHead}(Q,K,V)=\text{Concat}(head_1,;head_2,;\ldots,;head_h)W^O
]

Where:

* **head₁, head₂, ...** = Outputs from each attention head
* **Concat** = Combine all head outputs
* **Wᴼ** = Final weight matrix

---

## Advantages

* ✅ Learns different relationships simultaneously.
* ✅ Improves context understanding.
* ✅ Captures both local and global information.
* ✅ Produces more accurate language representations.
* ✅ Forms a key component of modern Transformers and LLMs.

---

## Single Head vs Multi-Head

| Single Head Attention  | Multi-Head Attention                       |
| ---------------------- | ------------------------------------------ |
| One perspective        | Multiple perspectives                      |
| Limited understanding  | Richer understanding                       |
| May miss relationships | Captures many relationships simultaneously |
| Lower performance      | Better performance                         |

---

> **Multi-Head Attention is a mechanism where the Transformer uses multiple attention heads instead of one. Each head independently performs Scaled Dot-Product Attention and learns different relationships in the input, such as grammar, context, or semantic meaning. The outputs from all heads are combined to create a richer and more accurate representation of the sentence.**

---

## Easy Memory Trick

Imagine **four teachers** reading the same essay:

* 👩‍🏫 Teacher 1 checks **grammar**.
* 👨‍🏫 Teacher 2 checks **meaning**.
* 👩‍🏫 Teacher 3 checks **sentence structure**.
* 👨‍🏫 Teacher 4 checks the **overall idea**.

Each teacher notices something different. Combining all their feedback gives a much better evaluation.

**Multi-Head Attention works the same way—it uses multiple "heads" to understand different aspects of the same sentence at the same time.**
