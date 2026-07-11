# LLM Architecture – Dense Models

## What are Dense Models?

A **Dense Model** is an LLM in which **all the model parameters (weights) are activated for every input token**.

This means **every layer and every neuron participates in processing every token**.

---

## Simple Definition

> **A Dense Model uses all of its parameters to process every input token.**

---

# Why is it Called "Dense"?

Suppose a model has:

```text
7 Billion Parameters
```

When you ask:

```text
What is AI?
```

👉 The model uses **all 7 billion parameters** to generate the answer.

No parameters are skipped.

---

# How Dense Models Work

Example input:

```text
The cat sat.
```

↓

The input passes through:

* Embedding Layer
* Attention Layers
* Feed Forward Networks

↓

Every layer is used.

↓

Every neuron is active.

↓

Generate output.

---

# Architecture Diagram

```text
Input
  │
  ▼
Embedding Layer
  │
  ▼
Transformer Layer 1
(All Neurons Active)
  │
  ▼
Transformer Layer 2
(All Neurons Active)
  │
  ▼
Transformer Layer 3
(All Neurons Active)
  │
  ▼
...
  │
  ▼
Output Layer
```

Every layer participates for every token.

---

# Example

Prompt:

```text
Explain Machine Learning.
```

The model processes it using:

```text
✓ Layer 1
✓ Layer 2
✓ Layer 3
✓ Layer 4
...
✓ Final Layer
```

Nothing is skipped.

---

# Characteristics

* ✅ All parameters are used.
* ✅ Simple architecture.
* ✅ Easy to train and deploy.
* ✅ Consistent computation for every input.

---

# Advantages

* ✅ Simple and reliable.
* ✅ Stable performance.
* ✅ High-quality responses.
* ✅ Easier to implement than sparse architectures.

---

# Disadvantages

* ❌ Higher computational cost.
* ❌ More GPU memory required.
* ❌ Slower inference compared to sparse models with similar total parameter counts.

---

# Dense Models vs Sparse Models (MoE)

| Dense Models                 | Sparse Models (MoE)                              |
| ---------------------------- | ------------------------------------------------ |
| All parameters are active    | Only a subset of parameters (experts) are active |
| Higher computation per token | Lower computation per token                      |
| Simpler architecture         | More complex routing mechanism                   |
| Easier to train              | More difficult to train                          |

---

# Popular Dense Models

Examples include:

* GPT-2
* Llama 2
* BERT

> **Note:** Many earlier LLMs and many current open models are dense models, while some newer large models use Mixture of Experts (MoE).

---

> **A Dense Model is a Transformer architecture in which all model parameters are activated for every input token. Every layer and neuron participates in processing the input, making the architecture simple and consistent. Dense models generally provide strong performance but require more computation and memory compared to sparse models such as Mixture of Experts (MoE).**

---

# Easy Memory Trick

Imagine a classroom with **100 teachers**.

Whenever a student asks a question:

* 👨‍🏫 **All 100 teachers** help answer it.

No teacher is skipped.

Similarly:

```text
Input
   │
   ▼
All Parameters
   │
   ▼
Output
```

That's a **Dense Model**.

---

> **A Dense Model activates all of its parameters for every input token, meaning every layer participates in processing the input.**
