# LLM Architecture – Mixture of Experts (MoE)

## What is Mixture of Experts (MoE)?

**Mixture of Experts (MoE)** is a Transformer architecture where **only a small subset of the model's parameters (called experts)** are activated for each input token.

Instead of using **all parameters** like a Dense model, MoE **selects only the most relevant experts**, making the model more efficient.

---

## Simple Definition

> **Mixture of Experts (MoE) activates only a few specialized experts for each input token instead of using the entire model.**

---

# Why Do We Need MoE?

Suppose a model has:

```text id="ih3lwx"
100 Billion Parameters
```

### Dense Model

For every question:

```text id="5x3goj"
Uses all
100 Billion Parameters
```

This requires a lot of computation.

### MoE Model

The model has multiple experts.

Example:

```text id="srqbs3"
Expert 1
Expert 2
Expert 3
Expert 4
Expert 5
Expert 6
Expert 7
Expert 8
```

If you ask:

```text id="m6jzdg"
Write Python code
```

The router may choose:

```text id="2a5gt7"
✓ Expert 2
✓ Expert 6
```

Only these experts process the token.

The remaining experts stay inactive.

---

# How MoE Works

### Step 1: Input Token

```text id="wjlwmv"
Python
```

↓

### Step 2: Router (Gating Network)

The router decides which experts are best.

```text id="cljlwm"
Router
```

↓

### Step 3: Select Top Experts

Example:

```text id="1jlwm4"
Expert 3
Expert 7
```

↓

### Step 4: Experts Process the Token

Only the selected experts compute the output.

↓

### Step 5: Combine Results

The outputs from the selected experts are combined and sent to the next layer.

---

# Architecture Diagram

```text id="79jlwm"
Input Token
      │
      ▼
Embedding Layer
      │
      ▼
Router (Gate)
      │
      ├────────► Expert 1
      ├────────► Expert 2
      ├────────► Expert 3
      ├────────► Expert 4
      └────────► ...

Router selects only a few experts

      │
      ▼
Combine Outputs
      │
      ▼
Next Transformer Layer
```

---

# Real-Life Example

Imagine a hospital.

There are many doctors:

* 👨‍⚕️ Heart Specialist
* 👩‍⚕️ Eye Specialist
* 👨‍⚕️ Skin Specialist
* 👩‍⚕️ Brain Specialist

If you have an eye problem:

✅ Only the **Eye Specialist** examines you.

The other doctors are not involved.

Similarly, in MoE:

* Experts specialize in different patterns or tasks.
* The router sends each token to the most suitable experts.

---

# Advantages

* ✅ Faster inference than an equally sized dense model.
* ✅ Lower computation per token.
* ✅ Can scale to very large parameter counts.
* ✅ High performance with efficient resource usage.

---

# Disadvantages

* ❌ More complex architecture.
* ❌ Requires a router (gating network).
* ❌ Training is more challenging because experts should be used evenly (load balancing).

---

# Dense Model vs MoE

| Dense Model            | Mixture of Experts (MoE)         |
| ---------------------- | -------------------------------- |
| Uses all parameters    | Uses only selected experts       |
| Higher computation     | Lower computation per token      |
| Simpler architecture   | More complex architecture        |
| Every neuron is active | Only selected experts are active |

---

# Popular MoE Models

Examples include:

* Mixtral 8x7B
* Switch Transformer
* DeepSeek-V3

---


> **Mixture of Experts (MoE) is a Transformer architecture where only a small number of specialized expert networks are activated for each input token. A router, also called a gating network, selects the most relevant experts, reducing computation while allowing the model to have a very large total number of parameters. MoE enables efficient scaling compared to dense models.**

---

# Easy Memory Trick

Imagine a company with **100 employees**.

* **Dense Model** → All 100 employees work on every task.
* **MoE Model** → The manager selects only the **2 or 4 employees** who are experts in that task.

```text id="6jlwm9"
Input
   │
   ▼
Router
   │
   ▼
Choose Experts
   │
   ▼
Expert 2 + Expert 5
   │
   ▼
Output
```

Only the required experts work.

---

> **Mixture of Experts (MoE) is an LLM architecture where a router activates only a few specialized experts for each input token, making large models more computationally efficient than dense models.**
