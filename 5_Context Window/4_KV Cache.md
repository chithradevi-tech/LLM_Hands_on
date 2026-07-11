# KV Cache (Key-Value Cache)

## What is KV Cache?

**KV Cache (Key-Value Cache)** is a technique used during **LLM inference (text generation)** to **store the previously computed Key (K) and Value (V) vectors**. This avoids recalculating them for every new token, making generation much faster.

---

## Simple Definition

> **KV Cache stores previously computed Key and Value vectors so the model doesn't have to recompute them while generating text.**

---

# Why Do We Need KV Cache?

Suppose the model has already generated:

```text
I love
```

Now it wants to generate the next word.

Without KV Cache, the model recomputes attention for:

```text
I
love
```

every time a new token is generated.

This wastes computation.

With KV Cache, the model reuses the previously computed **Key** and **Value** vectors and computes only for the **new token**.

---

# How KV Cache Works

### Step 1: Input

```text
I
```

↓

Compute:

* Query (Q)
* Key (K)
* Value (V)

↓

Store:

```text
K(I)
V(I)
```

---

### Step 2: Next Token

Input:

```text
I love
```

Without KV Cache:

```text
Recompute:
K(I)
V(I)
K(love)
V(love)
```

With KV Cache:

```text
Use cached:
K(I)
V(I)

Compute only:
K(love)
V(love)
```

---

### Step 3: Next Token

Input:

```text
I love AI
```

Without KV Cache:

```text
Compute everything again.
```

With KV Cache:

```text
Use cached:
K(I)
V(I)
K(love)
V(love)

Compute only:
K(AI)
V(AI)
```

---

# Flow Diagram

```text
Token 1
   │
   ▼
Compute Q, K, V
   │
   ▼
Store K & V in Cache
   │
   ▼
Next Token
   │
   ▼
Reuse Cached K & V
   │
   ▼
Compute K & V Only for New Token
   │
   ▼
Generate Next Token
```

---

# Example

Prompt:

```text
The cat
```

The model caches:

```text
K(The)
V(The)

K(cat)
V(cat)
```

When generating:

```text
sat
```

The model:

* Uses cached K and V for **The** and **cat**
* Computes K and V only for **sat**

This makes generation much faster.

---

# Why Cache Only K and V?

In self-attention:

* **Query (Q)** is needed only for the **current token**.
* **Key (K)** and **Value (V)** from previous tokens are reused by future tokens.

Therefore:

* ❌ Query is **not cached**
* ✅ Key is cached
* ✅ Value is cached

---

# Advantages

* ✅ Faster text generation
* ✅ Avoids repeated computation
* ✅ Reduces latency
* ✅ Essential for chatbots and streaming responses

---

# Disadvantages

* ❌ Uses additional GPU/CPU memory
* ❌ Larger conversations require a larger cache

---

# Where is KV Cache Used?

KV Cache is used during:

* ✅ ChatGPT-style conversations
* ✅ Text generation
* ✅ Code generation
* ✅ AI assistants
* ✅ Any autoregressive Transformer (decoder-only models like GPT)

> **Note:** KV Cache is mainly used during **inference**, not during training.

---

# KV Cache vs Context Window

| KV Cache                              | Context Window                               |
| ------------------------------------- | -------------------------------------------- |
| Stores previous Key and Value vectors | Stores the tokens available to the model     |
| Speeds up generation                  | Limits how many tokens the model can process |
| Optimization technique                | Model capability/limit                       |

---

> **KV Cache is an inference optimization used in Transformer models. It stores the previously computed Key and Value vectors for earlier tokens, so when generating the next token, the model only computes the Key and Value for the new token instead of recomputing everything. This significantly speeds up text generation while using additional memory.**

---

# Easy Memory Trick

Imagine solving a math problem.

Without KV Cache:

* Every time the teacher asks the next question, you solve **all previous questions again**.

With KV Cache:

* You **keep your previous answers** and solve **only the new question**.

Similarly:

```text
Previous K & V
      │
      ▼
Store in Cache
      │
      ▼
Next Token
      │
      ▼
Reuse Cached K & V
      │
      ▼
Compute Only New K & V
```

---

> **KV Cache stores previously computed Key and Value vectors during inference, allowing the Transformer to reuse them and generate new tokens much faster.**
