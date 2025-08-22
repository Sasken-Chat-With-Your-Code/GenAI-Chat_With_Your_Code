# Chat with Your Code

An AI-powered assistant that helps developers understand and navigate C, C++, and header file codebases using **Retrieval Augmented Generation (RAG)**. Upload your source code files and ask natural language questions to get contextual explanations of functions, classes, structs, and overall logic.

---

## Table of Contents
1. [About the Project](#about-the-project)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Getting Started](#getting-started)
5. [Prerequisites](#prerequisites)
6. [Installation](#installation)
7. [Environment Variables](#environment-variables)
8. [Running the Backend](#running-the-backend)
9. [Running the Frontend](#running-the-frontend)
10. [Usage](#usage)
11. [Project Structure](#project-structure)
12. [API Endpoints](#api-endpoints)
13. [Contributing](#contributing)
14. [License](#license)
15. [Acknowledgments](#acknowledgments)

---

## 1. About the Project
**Chat with Your Code** is designed to assist developers in exploring and understanding large C/C++ projects.

The system leverages:
- **Tree-sitter** for parsing code into semantic chunks.
- **ChromaDB** for vector storage of embeddings.
- **Google Gemini 1.5 Flash** for contextual, natural-language answers.

With RAG, code is broken into meaningful chunks, stored in a vector database, and queried intelligently to provide developer-friendly explanations.

---

## 2. Features
- **Intelligent Code Chunking** – Accurate parsing of functions, classes, structs, and comments.
- **Semantic Search (RAG)** – Retrieves the most relevant code snippets.
- **Natural Language Interaction** – Ask questions in plain English.
- **LLM-Powered Explanations** – Uses Gemini 1.5 Flash for concise answers.
- **Persistent Vector Database** – Stores embeddings across sessions.
- **Codebase Management** – Upload new files or clear existing ones.
- **Configurable Parameters** – Control retrieval depth, similarity thresholds, and generation randomness.
- **CORS Support** – Easy frontend integration.

---

## 3. Technologies Used

### Backend (Python FastAPI)
- FastAPI, Uvicorn
- ChromaDB
- Sentence-Transformers (all-MiniLM-L6-v2)
- Tree-sitter & tree-sitter-languages
- Google Generative AI SDK
- Pydantic
- Python-dotenv

### Frontend (React + TypeScript)
- React 18, Vite, Tailwind CSS, Lucide React
- Secure login with bcrypt + Flask-Session
- Drag-and-drop file uploads, syntax-highlighted viewer, Mermaid diagrams
- Animated landing page, chat UI, light/dark themes

---

## 4. Getting Started
Follow the steps below to run the project locally.

---

## 5. Prerequisites
- **Python 3.9+**
- **pip** (comes with Python)
- **Node.js (LTS)**
- **npm**
- **Google Gemini API Key**

---

## 6. Installation

### Clone Repository
```bash
git clone [https://github.com/Sasken-Chat-With-Your-Code/GenAI-Chat_With_Your_Code/tree/main/Api_Approach](https://github.com/Sasken-Chat-With-Your-Code/GenAI-Chat_With_Your_Code/tree/main/Api_Approach)
cd Api_Approach
```

### Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate   # (Linux/macOS)
.\venv\Scripts\activate    # (Windows)
pip install -r requirements.txt
cd ..
```

### Frontend Setup
```bash
cd frontend
npm install
cd ..
```

---

## 7. Environment Variables
Create a `.env` file in `backend/`:

```
GEMINI_API_KEY="YOUR_GEMINI_API_KEY_HERE"
```

---

## 8. Running the Backend
```bash
python -m backend.main
```
Runs at: `http://0.0.0.0:8000`

---

## 9. Running the Frontend
```bash
npm run dev
```
Runs at: `http://localhost:3000`

---

## 10. Usage
1. Open the frontend app in your browser.
2. Upload `.c`, `.cpp`, `.h`, `.hpp`, or `.cxx` files.
3. Ask questions in plain English.
4. View answers with highlighted relevant snippets.
5. Clear the codebase to restart with new files.

---

## 11. Project Structure
```
.
├── backend/
│   ├── main.py
│   ├── llm_module.py
│   ├── rag_module.py
│   ├── .env.example
│   ├── .env
│   └── requirements.txt
├── frontend/
│   ├── src/
│   ├── package.json
│   ├── tsconfig.json
│   └── ...
└── README.md
```

---

## 12. API Endpoints
- **`GET /`**
  - Root status endpoint.
  - Response:
  ```json
  {"message": "Chat with Your Code API is running!"}
  ```

- **`POST /upload_code_file`**
  - Uploads and indexes a code file.
  - Allowed file types: `.c`, `.cpp`, `.h`, `.hpp`, `.cxx`

- **`POST /clear_codebase`**
  - Clears all indexed chunks.

- **`POST /ask/`**
  - Asks a question about the codebase.
  - Example request:
  ```json
  {
    "query": "What does this function do?",
    "temperature": 0.2,
    "top_k": 5,
    "similarity_threshold": 0.7
  }
  ```

---

## 13. Contributing
Contributions are welcome via issues and pull requests. Please follow the existing style and conventions.

---

## 14. License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 15. Acknowledgments
- FastAPI
- ChromaDB
- Google Gemini API
- Sentence-Transformers
- Tree-sitter

---

✍️ **Authors**
- Manasa K
- Likhith Gowda A S
