# GenAI-Chat_With_Your_Code

Chat With Your Code is a Retrieval-Augmented Generation (RAG) system that lets developers **converse with their C/C++ codebase in natural language**. It provides explanations, Q&A, and even **Mermaid-based flow diagrams** to visualize code logic.  

This project has **two parallel approaches**:  
1. **Local Model Approach**   
2. **API Approach**  

---

### Local Model Approach
This version of Chat With Code runs entirely on your local machine using Qwen 1.5-0.5B-Chat model for understanding and answering questions about a C/C++ codebase. It leverages FastAPI for serving the backend, FAISS for efficient vector-based retrieval of code chunks, and implements a RAG (Retrieval-Augmented Generation) pipeline to provide context-aware, accurate responses.

### Features 

- **Privacy-Preserving** – Runs entirely on a local machine or private server, with no dependency on external APIs.  
- **API-First Design** – Qwen is encapsulated within a FastAPI service, allowing seamless interaction through REST endpoints without requiring users to install or manage the model directly.  
- **Plug-and-Play Deployment** – Functions like a hosted API (similar to Gemini), but fully self-contained and self-hosted.  
- **High-Performance Retrieval** – FAISS ensures efficient semantic search across large and complex C/C++ codebases.  
- **Semantic Embeddings** – SentenceTransformers (`all-MiniLM-L6-v2`) provide robust vector representations of code and documentation.  
- **Context-Enriched Responses** – Retrieval-Augmented Generation (RAG) pipeline combines embeddings with Qwen’s reasoning for accurate and grounded answers.  
- **Extensible Architecture** – Built with FastAPI, enabling easy integration of authentication, logging, monitoring, and enterprise-grade extensions.  


### 🛠️ Tech Stack  
- **Programming Language** – Python (backend), C/C++ (knowledge base)  
- **Backend Framework** – [FastAPI](https://fastapi.tiangolo.com/) for serving queries  
- **Vector Database** – [FAISS](https://github.com/facebookresearch/faiss) for efficient similarity search  
- **Embedding Model** – [SentenceTransformers](https://www.sbert.net/) (`all-MiniLM-L6-v2`) for code embeddings  
- **Local LLM** – [Qwen 1.5-0.5B-Chat](https://huggingface.co/Qwen) for explanation & reasoning  
- **Environment** – `venv` or `conda` for dependency management  
- **Version Control** – Git & GitHub for collaboration


### ▶️ Running the Project

#### Run Backend (FastAPI)

uvicorn app.main:app --reload --host 0.0.0.0 --port 8000

#### Run Frontend (React.js)
cd frontend 

npm install

npm run dev


---



### API Approach
ChatWithCode is a Retrieval-Augmented Generation (RAG) using Gemini API , system that lets developers chat with a C/C++ codebase in natural language. It helps in understanding unfamiliar codebases by answering queries, generating explanations, and visualizing logic flow through Mermaid diagrams.

### 🚀 Features

- **C/C++ Code Understanding** – Ask natural language questions about functions, modules, and logic in C/C++ codebases.  
- **Function & Comment Chunking** – Extracts semantically meaningful chunks (functions, docstrings, comments) from source code.  
- **Vector Search with ChromaDB** – Retrieves the most relevant code sections for a user’s query using embeddings.  
- **LLM-powered Explanations** – Uses **Gemini 1.5 Flash** (via Google Generative AI) to generate clear, grounded answers.  
- **Mermaid Flow Diagrams** – Automatically generates **Mermaid flowcharts** to visualize function logic and control flow.  
- **React.js Frontend** – Interactive web interface with Mermaid.js rendering for diagrams and chat history.  
- **FastAPI Backend** – Provides a secure `/ask` endpoint to handle queries via the RAG pipeline.  

### ⚙️ Tech Stack

- **Programming Language** – Python (backend + preprocessing), C/C++ (knowledge base).  
- **Backend Framework** – [FastAPI](https://fastapi.tiangolo.com/) for API and RAG orchestration.  
- **Frontend Framework** – [React.js](https://react.dev/) for building the chat interface and rendering diagrams.  
- **Vector Database** – [ChromaDB](https://www.trychroma.com/) for storing and retrieving code embeddings.  
- **Embedding Model** – [SentenceTransformers](https://www.sbert.net/) for generating vector representations of code and comments.  
- **Large Language Model (LLM)** – [Gemini 1.5 Flash](https://ai.google.dev/) via Google Generative AI API for explanations and diagram generation.  
- **Visualization** – [Mermaid.js](https://mermaid.js.org/) for rendering flowcharts and diagrams inside the UI.  
- **Environment Management** – `venv` or `conda` for Python dependencies.  
- **Version Control** – Git & GitHub for collaboration. 


### ▶️ Running the Project
#### Run Backend (FastAPI)
uvicorn main:app --reload


#### Run Frontend (React.js)
cd frontend

npm install

npm run dev

---
  
- ### Frontend using react and tailwind 
- Built with React 18 + TypeScript, Tailwind CSS, Vite, and Lucide React, featuring responsive design, reusable components, and theme support (dark/light).
- Secure signup/login with bcrypt password hashing, Flask-Session for session management, and persistent user preferences.
- Drag-and-drop C/C++ file uploads with validation, syntax-highlighted viewer, file statistics, Mermaid diagram visualizations, and localStorage persistence.
- Animated landing page, gradient and glassmorphism effects, micro-interactions, and chat interface for seamless user engagement.
- AI-driven natural language responses for code explanation, documentation generation, and RAG-based query handling.

---
### 👩‍💻 Contributors

This project was developed collaboratively:

- **Shreya C Bharadwaj** – Local Model RAG pipeline, Qwen model integration, FAISS setup, FastAPI backend
- **Manasa K. and Likhith Gowda A S** – API approach using Gemini, Tree-Sitter RAG pipeline for extraction of code chunks
- **Laasya Priya and Siva Vaishali** – Interactive frontend using React, Tailwind, and TypeScript


