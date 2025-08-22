# GenAI-Chat_With_Your_Code

### Local Model Approach
This version of Chat With Code runs entirely on your local machine using Qwen 1.5-0.5B-Chat model for understanding and answering questions about a C/C++ codebase. It leverages FastAPI for serving the backend, FAISS for efficient vector-based retrieval of code chunks, and implements a RAG (Retrieval-Augmented Generation) pipeline to provide context-aware, accurate responses.


### API Approach
ChatWithCode is a Retrieval-Augmented Generation (RAG) using Gemini API , system that lets developers chat with a C/C++ codebase in natural language. It helps in understanding unfamiliar codebases by answering queries, generating explanations, and visualizing logic flow through Mermaid diagrams.

## 🚀 Features

- **C/C++ Code Understanding** – Ask natural language questions about functions, modules, and logic in C/C++ codebases.  
- **Function & Comment Chunking** – Extracts semantically meaningful chunks (functions, docstrings, comments) from source code.  
- **Vector Search with ChromaDB** – Retrieves the most relevant code sections for a user’s query using embeddings.  
- **LLM-powered Explanations** – Uses **Gemini 1.5 Flash** (via Google Generative AI) to generate clear, grounded answers.  
- **Mermaid Flow Diagrams** – Automatically generates **Mermaid flowcharts** to visualize function logic and control flow.  
- **React.js Frontend** – Interactive web interface with Mermaid.js rendering for diagrams and chat history.  
- **FastAPI Backend** – Provides a secure `/ask` endpoint to handle queries via the RAG pipeline.  

## ⚙️ Tech Stack

- **Programming Language** – Python (backend + preprocessing), C/C++ (knowledge base).  
- **Backend Framework** – [FastAPI](https://fastapi.tiangolo.com/) for API and RAG orchestration.  
- **Frontend Framework** – [React.js](https://react.dev/) for building the chat interface and rendering diagrams.  
- **Vector Database** – [ChromaDB](https://www.trychroma.com/) for storing and retrieving code embeddings.  
- **Embedding Model** – [SentenceTransformers](https://www.sbert.net/) for generating vector representations of code and comments.  
- **Large Language Model (LLM)** – [Gemini 1.5 Flash](https://ai.google.dev/) via Google Generative AI API for explanations and diagram generation.  
- **Visualization** – [Mermaid.js](https://mermaid.js.org/) for rendering flowcharts and diagrams inside the UI.  
- **Environment Management** – `venv` or `conda` for Python dependencies.  
- **Version Control** – Git & GitHub for collaboration. 

## Run Backend (FastAPI)
uvicorn main:app --reload

## Run Frontend (React.js)
cd frontend
npm install
npm run dev


### Credits

This project was developed collaboratively:

- ## Shreya C Bharadwaj – Local Model RAG pipeline, Qwen model integration, FAISS setup, FastAPI backend  
- ## Manasa K and  Likhith – API approach 
**Backend Development (RAG, LLM, FastAPI)** 
- Implemented the **Retrieval-Augmented Generation (RAG)** pipeline for C/C++ codebases.  
- Developed **chunking logic** for functions and comments using **tree-sitter**.  
- Integrated **ChromaDB** vector search and **SentenceTransformers** embeddings.  
- Connected **Gemini 1.5 Flash** for LLM-powered explanations.  
- Built **FastAPI backend** with secure `/ask` endpoint.  
- Generated **Mermaid flowcharts** for function logic visualization.  
- ## Laasya and Siva Vaishali – Frontend using react and tailwind (elaborate)
- Built with React 18 + TypeScript, Tailwind CSS, Vite, and Lucide React, featuring responsive design, reusable components, and theme support (dark/light).
- Secure signup/login with bcrypt password hashing, Flask-Session for session management, and persistent user preferences.
- Drag-and-drop C/C++ file uploads with validation, syntax-highlighted viewer, file statistics, Mermaid diagram visualizations, and localStorage persistence.
- Animated landing page, gradient and glassmorphism effects, micro-interactions, and chat interface for seamless user engagement.
- Advanced vector embeddings enable intelligent, context-aware search across entire codebases for precise snippet retrieval.
- AI-driven natural language responses for code explanation, documentation generation, and RAG-based query handling.



