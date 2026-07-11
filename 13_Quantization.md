# Quantization

## What is Quantization?

**Quantization** is a technique that **reduces the precision of a model's weights and activations** (for example, from **32-bit floating point (FP32)** to **16-bit (FP16)** or **8-bit (INT8)**). This makes the model **smaller, faster, and more memory-efficient**.

---

## Simple Definition

> **Quantization reduces the size of an LLM by storing its numbers with fewer bits, making inference faster and using less memory.**

---

# Why Do We Need Quantization?

Large LLMs require:

* Large GPU memory
* More storage
* More computation

Quantization reduces these requirements.

Example:

```text id="6bk5f2"
Original Model
FP32 (32 bits)
```

↓

```text id="9d6p0q"
Quantized Model
INT8 (8 bits)
```

The model becomes much smaller while often maintaining similar performance.

---

# How Quantization Works

### Step 1: Original Model

Weights:

```text id="hlvzh5"
0.345678
-0.891234
1.234567
```

↓

### Step 2: Convert to Lower Precision

```text id="7crd49"
0.35
-0.89
1.23
```

or store them as 8-bit integers after scaling.

↓

### Step 3: Run Inference

The quantized model generates responses using less memory and computation.

---

# Flow Diagram

```text id="hzux20"
Trained Model
      │
      ▼
FP32 Weights
      │
      ▼
Quantization
      │
      ▼
INT8 / FP16 / INT4
      │
      ▼
Smaller & Faster Model
```

---

# Example

Suppose a model is:

```text id="clu6fu"
8 GB
```

After INT8 quantization:

```text id="18g6rx"
≈ 2 GB
```

The exact size depends on the quantization method and whether all parts of the model are quantized.

---

# Common Quantization Types

| Type | Bits | Memory Usage | Speed     | Accuracy               |
| ---- | ---- | ------------ | --------- | ---------------------- |
| FP32 | 32   | High         | Slower    | Highest                |
| FP16 | 16   | Medium       | Faster    | Very High              |
| INT8 | 8    | Low          | Fast      | High                   |
| INT4 | 4    | Very Low     | Very Fast | May lose more accuracy |

---

# Types of Quantization

### 1. Post-Training Quantization (PTQ)

* Quantize **after** the model has been trained.
* Simple and widely used.
* No retraining required.

---

### 2. Quantization-Aware Training (QAT)

* Simulates quantization **during training**.
* Helps the model adapt to lower precision.
* Often provides better accuracy than PTQ.

---

# Applications

Quantization is used for:

* ✅ Running LLMs on laptops
* ✅ Mobile devices
* ✅ Edge AI
* ✅ Faster inference
* ✅ Lower cloud costs
* ✅ Reduced GPU memory usage

---

# Advantages

* ✅ Smaller model size.
* ✅ Faster inference.
* ✅ Lower memory usage.
* ✅ Lower deployment cost.

---

# Disadvantages

* ❌ Small accuracy loss may occur.
* ❌ Very aggressive quantization (e.g., INT4) can reduce model quality more noticeably.
* ❌ Some hardware supports certain quantization formats better than others.

---

# Quantization vs Pruning

| Quantization                          | Pruning                                        |
| ------------------------------------- | ---------------------------------------------- |
| Reduces the precision of weights      | Removes unnecessary weights or neurons         |
| Keeps the model architecture the same | Changes the effective model structure          |
| Makes the model smaller and faster    | Makes the model smaller and potentially faster |

---

> **Quantization is the process of reducing the numerical precision of a model's weights and activations, such as converting FP32 values to FP16 or INT8. This reduces memory usage, speeds up inference, and lowers deployment costs while typically maintaining most of the model's accuracy. Common approaches include Post-Training Quantization (PTQ) and Quantization-Aware Training (QAT).**

---

# Easy Memory Trick

Imagine storing photos on your phone.

* 📷 **High quality** → Larger file size.
* 📷 **Compressed quality** → Smaller file size, still looks good.

Similarly:

```text id="tdlcpq"
FP32
   │
   ▼
Quantization
   │
   ▼
INT8
   │
   ▼
Smaller + Faster
```

The model is **compressed**, but still works well.

---

> **Quantization reduces the precision of an LLM's weights and activations to make the model smaller, faster, and more memory-efficient with minimal impact on accuracy.**
