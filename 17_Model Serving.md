# Model Serving

## What is Model Serving?

**Model Serving** is the process of **deploying a trained LLM so users or applications can send requests and receive predictions in real time**.

After training, the model is hosted on a **server** and exposed through an **API**.

---

## Simple Definition

> **Model Serving is the process of making a trained LLM available to users or applications through an API for inference.**

---

# Why Do We Need Model Serving?

A trained model stored on disk cannot be used directly by users.

Model serving:

* ✅ Loads the trained model into memory.
* ✅ Receives user requests.
* ✅ Runs inference.
* ✅ Returns the response.

---

# How Model Serving Works

### Step 1: User Sends a Request

```text
Explain Machine Learning.
```

↓

### Step 2: API Receives the Request

Example:

```text
POST /generate
```

↓

### Step 3: Model Server

* Loads the LLM (if not already loaded).
* Tokenizes the input.
* Runs inference.

↓

### Step 4: Generate Response

```text
Machine Learning is a branch of AI...
```

↓

### Step 5: Send Response to User

---

# Flow Diagram

```text
User
   │
   ▼
Frontend / Client
   │
   ▼
REST API
(FastAPI/Flask)
   │
   ▼
Model Server
(vLLM / TGI / Ollama)
   │
   ▼
LLM
   │
   ▼
Response
```

---

# Components of Model Serving

### 1. Model

The trained LLM.

Example:

* Llama
* Gemma
* Mistral

---

### 2. API Server

Receives requests and sends responses.

Examples:

* FastAPI
* Flask

---

### 3. Inference Engine

Runs the model efficiently.

Examples:

* vLLM
* Hugging Face Text Generation Inference (TGI)
* Ollama

---

### 4. Hardware

The model runs on:

* GPU (preferred for large models)
* CPU (for smaller models)

---

# Example

User asks:

```text
What is Python?
```

↓

FastAPI receives the request.

↓

The model server sends it to the LLM.

↓

LLM generates:

```text
Python is a high-level programming language...
```

↓

FastAPI returns the response as JSON.

---

# Popular Model Serving Frameworks

| Framework            | Purpose                                                                         |
| -------------------- | ------------------------------------------------------------------------------- |
| **vLLM**             | High-performance LLM inference with features like efficient KV cache management |
| **Hugging Face TGI** | Production-ready text generation server                                         |
| **Ollama**           | Run LLMs locally                                                                |
| **FastAPI**          | Build APIs for model serving                                                    |
| **Flask**            | Lightweight Python API framework                                                |
| **TensorRT-LLM**     | GPU-optimized inference for NVIDIA hardware                                     |

---

# Applications

Model serving is used in:

* 🤖 Chatbots
* 💻 Code Assistants
* 📄 Document Summarization
* 🌐 Translation
* 🔍 Search Systems
* 🤖 AI Agents
* 📱 Mobile and Web Applications

---

# Advantages

* ✅ Real-time responses.
* ✅ Easy integration through APIs.
* ✅ Can serve many users simultaneously.
* ✅ Scalable using cloud infrastructure.

---

# Challenges

* ❌ Large models require significant memory.
* ❌ High traffic can increase latency.
* ❌ GPU resources can be expensive.
* ❌ Scaling and load balancing require careful planning.

---

# Model Training vs Model Serving

| Model Training        | Model Serving                       |
| --------------------- | ----------------------------------- |
| Trains the LLM        | Deploys the trained LLM             |
| Updates model weights | Uses fixed weights for inference    |
| Uses massive datasets | Handles user requests               |
| Takes days or weeks   | Responds in seconds or milliseconds |

---

> **Model Serving is the process of deploying a trained LLM so that users or applications can access it through an API. The server receives user requests, performs inference using the model, and returns the generated response. Popular model serving frameworks include vLLM, Hugging Face TGI, Ollama, and FastAPI for API development.**

---

# Easy Memory Trick

Imagine a restaurant:

* 👨‍🍳 **Chef** = Trained LLM
* 🍽️ **Waiter** = API Server
* 🏠 **Restaurant** = Model Server
* 👤 **Customer** = User

Flow:

```text
Customer
   │
   ▼
Waiter (API)
   │
   ▼
Chef (LLM)
   │
   ▼
Food (Response)
```

The chef has already learned how to cook (**training**). The restaurant serves customers (**model serving**).

---


> **Model Serving is the process of deploying a trained LLM behind an API so it can perform inference and provide real-time responses to users or applications.**
