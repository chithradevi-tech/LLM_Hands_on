# 🎤 AI Interview Simulator (LLM Project – Free API)

## 📌 Overview

**AI Interview Simulator** is an interactive application that simulates real interview scenarios using a Large Language Model (LLM).

It allows users to:

* Receive interview questions
* Submit answers
* Get AI-based evaluation
* Track performance over time

This project uses a **free LLM API** from **Google AI Studio**, so no billing or credit card is required.

---

## 🎯 Goal

The goal of this project is to:

* Learn **context handling in LLM applications**
* Implement **multi-step prompting**
* Build **evaluation-based AI systems**
* Understand **structured output (JSON parsing)**

---

## 🚀 Features

* 🎯 Generate interview questions (role + level based)
* ✍️ Accept user answers
* 📊 Evaluate answers using LLM
* ⭐ Provide score, feedback, and improvements
* 🧠 Maintain session-based interview history
* 📂 Display previous responses in sidebar

---

## 🏗️ Architecture

```text
User Input (Role, Level)
        ↓
Question Generation (LLM)
        ↓
User Answer
        ↓
Evaluation Prompt
        ↓
LLM Evaluation
        ↓
Structured JSON Output
        ↓
Display Results (Streamlit UI)
```

---

## 🛠️ Tech Stack

* Python
* Streamlit (UI)
* Gemini API (LLM)
* python-dotenv (env management)

---

## 📁 Project Structure

```text
ai-interview-simulator/
│
├── app.py              # Main Streamlit UI
├── llm.py              # LLM integration
├── prompts.py          # Prompt templates
├── config.py           # API configuration
├── requirements.txt
├── .env
└── history.json        # (optional) store interview data
```

---

## ⚙️ Installation Steps

### 1️⃣ Clone the Repository

```bash
git clone <your-repo-url>
cd ai-interview-simulator
```

---

### 2️⃣ Create Virtual Environment

```bash
python -m venv venv
```

#### Activate:

**Windows (CMD):**

```bash
venv\Scripts\activate
```

**PowerShell (if blocked):**

```bash
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
venv\Scripts\Activate.ps1
```

---

### 3️⃣ Install Dependencies

```bash
python -m pip install -r requirements.txt
```

---

## 🔑 Setup Free API Key

Get your API key from **Google AI Studio**

### Steps:

1. Go to: https://aistudio.google.com/app/apikey
2. Click **Create API Key**
3. Copy the key

---

### Create `.env` file

```env
GOOGLE_API_KEY=your_api_key_here
```

---

## ▶️ Run the Application

```bash
streamlit run app.py
```

👉 The app will open in your browser.

---

## 🧪 Example Workflow

### Step 1: Select Role & Level

* Role: Frontend Developer
* Level: Beginner

---

### Step 2: Generate Question

Example:

```
Explain useState in React.
```

---

### Step 3: Submit Answer

Example:

```
useState is a hook used to manage state in functional components...
```

---

### Step 4: Get Evaluation

```json
{
  "score": 7,
  "feedback": "Good explanation but lacks real-world example",
  "improvement": "Add example and explain re-render behavior"
}
```

---

## 🧠 Key Concepts Learned

* Context management using session state
* Multi-step prompting (question → answer → evaluation)
* Structured JSON output from LLM
* Error handling for invalid responses
* Real-world AI system design

---

## ⚠️ Common Issues & Fixes

### ❌ Invalid JSON Response

**Cause:** LLM returns extra text or markdown

**Fix:**

* Clean response before parsing
* Use strict prompt rules

---

### ❌ API Errors (429 / quota)

**Cause:** Free tier limit exceeded

**Fix:**

* Reduce requests
* Optimize prompt size

---

## 🚀 Future Improvements

* Multi-question interview flow
* Final cumulative score
* Timer for answers
* Domain-specific question bank
* Export interview report (PDF)
* Add React frontend

---




