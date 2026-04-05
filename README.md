# 🧠 Blog Writing Agent  
### *A Planning-First AI System for Structured, Research-Aware Blog Generation*

---

## 📌 Abstract

This project presents a **planning-based AI agent system** that generates high-quality blog content through a structured, multi-stage pipeline.  

Unlike conventional Large Language Model (LLM) applications that directly produce responses, this system introduces a **planner-executor architecture** that ensures:

- Logical structure  
- Reduced hallucination  
- Context-aware content generation  
- Modular execution  

The agent dynamically decides whether external research is required, gathers relevant information, constructs a plan, and executes it step-by-step, ultimately producing a **fully formatted blog with optional AI-generated images**.

---

## 🎥 Demo

📽️ **End-to-End Working Demo**  
See the agent in action: from initial topic analysis and web research to structured planning and final markdown generation.

<div align="center">
<video src="https://github.com/Manya-singh2001/Blog-Writing-Agent/raw/main/content/demo.MP4" width="100%" controls>
Your browser does not support the video tag.
</video>
</div>

---

## 🏗️ System Architecture

<p align="center">
  <img src="https://github.com/Manya-singh2001/Blog-Writing-Agent/blob/main/content/system%20architecture.png">
</p>


Unlike traditional LLM apps, this agent **does not jump directly to answers** — it first creates a structured plan and then executes it step by step.

---

## 🔍 Key Characteristics

- 🧠 Multi-step reasoning pipeline  
- 🌐 Dynamic research integration (DuckDuckGo)  
- ⚡ Parallel content generation  
- 📐 Structured outputs using schemas (Pydantic)  
- 🎨 AI-powered image generation (Gemini)  

---

## 🔄 Execution Pipeline

### 1️⃣ Router Node
- Decides if research is needed  
- Selects mode:
  - `closed_book`
  - `hybrid`
  - `open_book`

---

### 2️⃣ Research Node
- Uses **DuckDuckGo (free search)**
- Extracts:
  - Title
  - URL
  - Snippet

---

### 3️⃣ Orchestrator (Planner)

- Creates structured plan:
  Plan = {Title,
          Audience,
          Tone,
          Tasks[]
          }
- 
Each task = one blog section

---

### 4️⃣ Fanout (Parallelization)

- Tasks → Multiple Workers


---

### 5️⃣ Worker Nodes

Each worker:
- Writes one section
- Uses:
  - Task metadata
  - Research evidence

---

### 6️⃣ Reducer Node

- Final Blog = Sum of All Sections
  
---

### 7️⃣ Image Planning
- Detects where images are needed  
- Inserts placeholders  

---

### 8️⃣ Image Generation
- Uses **Gemini API**
- Generates diagrams/visuals
- Replaces placeholders  

---

### 9️⃣ Final Output
- Markdown blog  
- Embedded images  
- Downloadable bundle  

---

### 🖥️ Frontend Features (Streamlit)
🚀 Interactive UI
- Topic input
- Date selection
- One-click execution

### 📊 Real-Time Execution Tracking

Displays:
- Active node
= Pipeline progress
- State updates

### 📂 Past Blogs Feature

- Automatically loads .md files
- Reload previous blogs
- Enables iteration

### 🧠 Memory Feature
Stores last output in session
Allows:
- Reloading results
- Viewing past runs

### ⬇️ Download Options
- Markdown file (.md)
- ZIP bundle (blog + images)
- Images only

### 🛠️ Tech Stack
🧠 AI & Backend
- LangGraph
- LangChain
- OpenRouter (LLM API)
- Gemini API (Image Generation)
  
🌐 Search
- DuckDuckGo
  
⚙️ Backend
- Python
- Pydantic
  
🎨 Frontend
- Streamlit

### 🔑 Environment Setup
Create .env file 
OPENROUTER_API_KEY=your_openrouter_key
GOOGLE_API_KEY=your_gemini_key
