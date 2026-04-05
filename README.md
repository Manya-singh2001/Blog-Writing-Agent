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
👉 *(Insert your video link here — YouTube / GitHub assets)*

---

## 🏗️ System Architecture

```mermaid
graph TD
    A[User Input] --> B[Router Node]
    B -->|No Research| D[Orchestrator]
    B -->|Needs Research| C[Research Node]
    C --> D
    D --> E[Fanout]
    E --> F[Worker Nodes]
    F --> G[Reducer]
    G --> H[Image Planner]
    H --> I[Image Generator]
    I --> J[Final Blog Output]

\section{🧩 Project Overview}

The \textbf{Blog Writing Agent} is designed to simulate how expert writers approach content creation:

\[
\text{Plan} \rightarrow \text{Research} \rightarrow \text{Execute} \rightarrow \text{Refine}
\]

\subsection{🔍 Key Characteristics}
\begin{itemize}
\item Multi-step reasoning pipeline
\item Dynamic research integration
\item Parallel content generation
\item Structured outputs using schemas
\item AI-powered image augmentation
\end{itemize}

\section{🔄 Execution Pipeline}

\subsection{1️⃣ Router Node}
Determines:
\begin{itemize}
\item Whether research is required
\item Execution mode:
\begin{itemize}
\item \texttt{closed\_book}
\item \texttt{hybrid}
\item \texttt{open\_book}
\end{itemize}
\end{itemize}

\subsection{2️⃣ Research Node}
\begin{itemize}
\item Uses DuckDuckGo (free search engine)
\item Extracts structured evidence:
\begin{itemize}
\item Title
\item URL
\item Snippet
\end{itemize}
\end{itemize}

\subsection{3️⃣ Orchestrator (Planner)}

Generates a structured plan:

\[
\text{Plan} = \{ \text{Title}, \text{Audience}, \text{Tone}, \text{Tasks} \}
\]

Each task represents a section of the blog.

\subsection{4️⃣ Fanout (Parallelization)}

\[
\text{Tasks} \rightarrow \text{Multiple Workers}
\]

\subsection{5️⃣ Worker Nodes}

Each worker:
\begin{itemize}
\item Writes a section
\item Uses:
\begin{itemize}
\item Task metadata
\item Research evidence
\end{itemize}
\end{itemize}

\subsection{6️⃣ Reducer Node}

Combines all sections:

\[
\text{Final Blog} = \sum \text{Sections}
\]

\subsection{7️⃣ Image Planning}
\begin{itemize}
\item Identifies where images are needed
\item Inserts placeholders
\end{itemize}

\subsection{8️⃣ Image Generation}
\begin{itemize}
\item Uses Gemini API
\item Generates diagrams and visuals
\item Replaces placeholders
\end{itemize}

\subsection{9️⃣ Final Output}
\begin{itemize}
\item Markdown blog
\item Embedded images
\item Downloadable bundle
\end{itemize}

\section{🖥️ Frontend Features (Streamlit)}

\subsection{🚀 Interactive Interface}
\begin{itemize}
\item Topic input
\item Date selection
\item One-click execution
\end{itemize}

\subsection{📊 Real-Time Execution Tracking}
Displays:
\begin{itemize}
\item Active node
\item Pipeline progress
\item State updates
\end{itemize}

\subsection{📑 Tabs Overview}
\begin{tabular}{|c|c|}
\hline
\textbf{Tab} & \textbf{Description} \\
\hline
🧩 Plan & Blog structure \\
🔎 Evidence & Research data \\
📝 Preview & Final markdown \\
🖼️ Images & Generated visuals \\
🧾 Logs & Execution logs \\
\hline
\end{tabular}

\subsection{📂 Past Blogs Feature}
\begin{itemize}
\item Automatically detects \texttt{.md} files
\item Reloads previous outputs
\item Enables reuse and iteration
\end{itemize}

\subsection{🧠 Memory Feature}
\begin{itemize}
\item Stores last generated output in session state
\item Allows:
\begin{itemize}
\item Reloading results
\item Viewing past runs
\end{itemize}
\item Simulates short-term memory for the agent
\end{itemize}

\subsection{⬇️ Download Options}
\begin{itemize}
\item Markdown file (.md)
\item ZIP bundle (blog + images)
\item Images only
\end{itemize}

\section{🧠 Design Philosophy}

\subsection{❌ Traditional Approach}
\[
\text{Input} \rightarrow \text{LLM} \rightarrow \text{Output}
\]

Problems:
\begin{itemize}
\item Hallucinations
\item No structure
\item No transparency
\end{itemize}

\subsection{✅ Agent-Based Approach}
\[
\text{Input} \rightarrow \text{Plan} \rightarrow \text{Execute} \rightarrow \text{Output}
\]

Advantages:
\begin{itemize}
\item Structured reasoning
\item Modular execution
\item Better reliability
\end{itemize}

\section{🛠️ Tech Stack}

\subsection{🧠 AI \& Backend}
\begin{itemize}
\item LangGraph
\item LangChain
\item OpenRouter (LLM API)
\item Gemini API (Image Generation)
\end{itemize}

\subsection{🌐 Search}
\begin{itemize}
\item DuckDuckGo (free alternative to Tavily)
\end{itemize}

\subsection{⚙️ Backend}
\begin{itemize}
\item Python
\item Pydantic (schema validation)
\end{itemize}

\subsection{🎨 Frontend}
\begin{itemize}
\item Streamlit
\end{itemize}

\section{📁 Project Structure}

\begin{verbatim}
blog-writing-agent/
│
├── bwa_backend.py        # LangGraph pipeline
├── bwa_frontend.py       # Streamlit UI
├── images/               # Generated images
├── *.md                  # Generated blogs
├── requirements.txt
└── README.md
\end{verbatim}

\section{🔑 Environment Setup}

Create a \texttt{.env} file:

\begin{verbatim}
OPENROUTER_API_KEY=your_openrouter_key
GOOGLE_API_KEY=your_gemini_key
\end{verbatim}

\section{⚙️ Installation}

\begin{verbatim}
python -m venv venv

# Activate
venv\Scripts\activate
# OR
source venv/bin/activate

pip install -r requirements.txt
\end{verbatim}

\section{▶️ Run the Application}

\begin{verbatim}
streamlit run bwa_frontend.py
\end{verbatim}

\section{🌟 Key Features}
\begin{itemize}
\item ✔ Planning-first AI agent
\item ✔ Multi-step execution pipeline
\item ✔ Free web search integration
\item ✔ AI-generated images
\item ✔ Real-time UI tracking
\item ✔ Downloadable outputs
\end{itemize}

\section{🚀 Project Standouts}
\begin{itemize}
\item 🧠 True Agent Architecture (LangGraph)
\item 🔄 Planner → Executor workflow
\item ⚡ Parallel processing (workers)
\item 🔍 Integrated search system
\item 🎨 Image generation pipeline
\item 📊 Transparent execution logs
\end{itemize}

\section{📚 Learning Outcomes}
\begin{itemize}
\item Agent-based system design
\item LangGraph workflows
\item LLM orchestration
\item Tool integration (search + images)
\item State management
\item Full-stack AI application development
\end{itemize}

\section{🔮 Future Improvements}
\begin{itemize}
\item Vector database (RAG)
\item Better citation system
\item Multi-language support
\item Cloud deployment (AWS / Vercel)
\item User authentication
\end{itemize}

\section{👨‍💻 Author}

\textbf{Your Name} \\
AI Engineer | Agentic AI | LLM Systems \\

\textbf{GitHub:} your-link \\
\textbf{LinkedIn:} your-link
