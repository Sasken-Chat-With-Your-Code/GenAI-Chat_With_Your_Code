# GenAI-Chat_With_Your_Code

## 🖥️ Local Model Approach
This version of Chat With Code runs entirely on your local machine using Qwen 1.5-0.5B-Chat model for understanding and answering questions about a C/C++ codebase. It leverages FastAPI for serving the backend, FAISS for efficient vector-based retrieval of code chunks, and implements a RAG (Retrieval-Augmented Generation) pipeline to provide context-aware, accurate responses.

This setup ensures:  
- **Data Privacy** – All code and queries remain within your local environment.  
- **Self-Contained Deployment** – Packaged as a FastAPI service, allowing API-style interaction without requiring users to directly manage the model.  

## 🔑 Key Features  

- **Privacy-Preserving** – No dependency on third-party APIs; runs locally or on a private server.  
- **API-First Design** – Encapsulates Qwen inside a FastAPI service for easy integration via REST endpoints.  
- **Plug-and-Play Deployment** – Works like a hosted API but fully self-hosted.  
- **High-Performance Retrieval** – Uses **FAISS** for scalable semantic search across large codebases.  
- **Semantic Embeddings** – Employs **SentenceTransformers (all-MiniLM-L6-v2)** for effective code/document representation.  
- **Context-Aware Responses** – RAG pipeline enriches responses with relevant code snippets.  
- **Extensible Architecture** – Built with FastAPI, supporting future extensions (auth, monitoring, logging, etc.).  


---

## 🛠️ Tech Stack  

- **Programming Language** – Python (backend), C/C++ (knowledge base)  
- **Backend Framework** – [FastAPI](https://fastapi.tiangolo.com/)  
- **Vector Database** – [FAISS](https://github.com/facebookresearch/faiss)  
- **Embedding Model** – [SentenceTransformers](https://www.sbert.net/) (`all-MiniLM-L6-v2`)  
- **Local LLM** – [Qwen 1.5-0.5B-Chat](https://huggingface.co/Qwen)  
- **Environment** – `venv` or `conda` for dependency management  
- **Version Control** – Git & GitHub  

---

## ▶️ Running the Project  

### Run Backend (FastAPI)  
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000

### Run Frontend
cd frontend

npm install

npm run dev


---

#### Author - Shreya C Bharadwaj

