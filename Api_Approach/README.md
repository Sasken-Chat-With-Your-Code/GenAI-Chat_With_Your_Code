### API Approach

Table of Contents
1. About the Project
2. Features
3. Technologies Used
4. Getting Started
5. Prerequisites
6. Installation
7. Environment Variables
8.Running the Backend
9. Running the Frontend
10. Usage
11. Project Structure
12. API Endpoints
13. Contributing
14.License
15.Acknowledgments

1. About the Project
"Chat with Your Code" is an innovative AI-powered assistant designed to help developers quickly understand and navigate C, C++, and header file codebases. This project implements a Retrieval Augmented Generation (RAG) architecture, allowing you to upload your source code files and then ask natural language questions about specific functions, classes, structs, or general code logic.

The system intelligently breaks down your code into semantic chunks, stores them in a vector database (ChromaDB), and retrieves the most relevant snippets based on your query. These retrieved chunks are then used to contextualize a Large Language Model (Google Gemini 1.5 Flash), enabling it to provide accurate, concise, and developer-friendly answers about your codebase.

2. Features
Intelligent Code Chunking: Utilizes Tree-sitter for robust and accurate parsing of C, C++, and header files, identifying functions, classes, structs, and comments.

Semantic Search (RAG): Embeds code chunks into a vector space and retrieves contextually relevant snippets using cosine similarity.

Natural Language Interaction: Ask questions about your code in plain English.

LLM-Powered Explanations: Leverages Google Gemini 1.5 Flash to generate clear, concise, and informative answers based on the retrieved code context.

Persistent Vector Database: Uses ChromaDB to store code embeddings and metadata, allowing you to query your uploaded codebase across sessions.

Codebase Management: Features to upload new code files and clear the entire indexed codebase.

Configurable Parameters: Adjust retrieval (top_k, similarity_threshold) and generation (temperature) parameters for tailored responses.

Cross-Origin Resource Sharing (CORS): Configured for easy integration with frontend applications.

3. Technologies Used
Backend (Python FastAPI):

FastAPI: High-performance web framework for building APIs.

Uvicorn: ASGI server for running FastAPI.

ChromaDB: Lightweight, embedded vector database.

Sentence-Transformers: For generating embeddings from text (all-MiniLM-L6-v2 model).

Tree-sitter & tree-sitter-languages: For advanced, language-aware code parsing and chunking.

Google Generative AI SDK: For interacting with the Gemini LLM.

Pydantic: For data validation and settings management.

Python-dotenv: For loading environment variables.

Frontend (Node.js & TypeScript):

Node.js: JavaScript runtime.

TypeScript: Superset of JavaScript that compiles to plain JavaScript.

(Further frontend libraries would depend on your specific setup, e.g., React, Next.js, Vue, etc.)

4. Getting Started
Follow these steps to set up and run the "Chat with Your Code" project on your local machine.

5.Prerequisites
Before you begin, ensure you have the following installed:

Python 3.9+:

Bash
python --version
pip (Python package installer): Usually comes with Python.

Bash
pip --version
Node.js (LTS recommended):

Bash
node --version
npm (Node Package Manager): Usually comes with Node.js.

Bash
npm --version
Google Gemini API Key: You'll need an API key from Google AI Studio.

6. Installation
Clone the repository:

Bash
git clone https://github.com/Sasken-Chat-With-Your-Code/GenAI-Chat_With_Your_Code/tree/main/Api_Approach
cd Api_Approach
Backend Setup:

Navigate into the backend directory:

Bash
cd backend
Create a Python virtual environment (recommended):

Bash
python -m venv venv
Activate the virtual environment:

On macOS/Linux:

Bash
source venv/bin/activate

On Windows:

Bash
.\venv\Scripts\activate
Install backend dependencies:

Bash

pip install -r requirements.txt
# If you don't have requirements.txt, you can install manually:
# pip install fastapi uvicorn chromadb sentence-transformers python-dotenv google-generativeai tree-sitter tree-sitter-languages
Go back to the project root:

Bash
cd ..
Frontend Setup:

Navigate into your frontend directory (assuming it's named frontend):

Bash
cd frontend
Install frontend dependencies:

Bash
npm install
Go back to the project root:

Bash
cd ..

7. Environment Variables
Create a .env file in the backend directory (Is already created) (i.e., ChatWithYourCode/backend/.env) and add your Google Gemini API key:

GEMINI_API_KEY="YOUR_GEMINI_API_KEY_HERE"
Important: Replace "YOUR_GEMINI_API_KEY_HERE" with your actual API key.

8. Running the Backend
Make sure your Python virtual environment is activated.

From the project root directory (YOUR_REPO_NAME), run the backend:

Bash
python -m backend.main
The backend API will start running on http://0.0.0.0:8000. You should see output similar to:

INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)

9. Running the Frontend
From your frontend directory (e.g., YOUR_REPO_NAME/frontend), run the frontend development server:

Bash
npm run dev
This will typically start your frontend application on http://localhost:3000 or a similar port, as configured in your frontend project.

10. Usage
Once both the backend and frontend are running:

Open your frontend application in your web browser (e.g., http://localhost:3000).

Upload Code Files: Use the provided interface in your frontend to upload C, C++, or header files (.c, .cpp, .h, .hpp, .cxx). The backend will process and index these files into ChromaDB.

Ask Questions: Type your natural language questions about the uploaded codebase into the query input field.

Explore Answers: The system will retrieve relevant code snippets and generate an answer. You can examine the generated answer and the retrieved code context.

Clear Codebase: If you wish to index a completely new set of files, use the "Clear Codebase" functionality (if exposed in your frontend) to remove all existing data from ChromaDB.

11. Project Structure
.
├── backend/
│   ├── main.py                     # FastAPI application entry point
│   ├── llm_module.py               # Handles interactions with the Google Gemini LLM
│   ├── rag_module.py               # Core RAG logic: chunking, embedding, retrieval
│   ├── .env.example                # Example for environment variables
│   ├── .env                        # Your actual environment variables (Gitignored)
│   └── requirements.txt            # Python dependencies
├── frontend/                       # Your Node.js/TypeScript frontend application
│   ├── src/
│   │   └── ...                     # Frontend source code
│   ├── package.json
│   ├── tsconfig.json
│   └── ...
└── README.md

12. API Endpoints
The backend exposes the following API endpoints:

GET /
Description: Root endpoint, returns a simple status message.
Response: {"message": "Chat with Your Code API is running!"}

POST /upload_code_file
Description: Uploads a code file (C, C++, or header) for processing and indexing into ChromaDB.
Request Body: multipart/form-data with a file field.
Allowed File Types: .c, .cpp, .h, .hpp, .cxx
Response: {"message": "File '{filename}' processed and indexed successfully."}
Error: 400 Bad Request if file type is not allowed. 500 Internal Server Error on processing failure.

POST /clear_codebase
Description: Clears all indexed code chunks from the ChromaDB collection.
Response: {"message": "ChromaDB codebase cleared successfully."}
Error: 500 Internal Server Error on clearing failure.

POST /ask/

Description: Asks a natural language question about the indexed codebase.
Request Body (JSON):

JSON

{
  "query": "string",
  "temperature": 0.2,            // Optional, controls LLM randomness (default 0.2)
  "top_k": 5,                  // Optional, number of chunks to retrieve (default 5)
  "similarity_threshold": 0.7, // Optional, minimum similarity for retrieved chunks (default 0.7)
  "filter_type": "string"      // Optional, filter retrieved chunks by type (e.g., "function", "class", "struct", "comment", "test_case_function", "array_init")
}
Response (JSON):

JSON

{
  "answer": "string",
  "retrieved_context": [
    {
      "content": "string",
      "source": "string",
      "start_line": 0,
      "type": "string",
      "distance": 0.0,           // Optional
      "function_name": "string", // Optional
      "class_name": "string",    // Optional
      "struct_name": "string"    // Optional
    }
  ],
  "debug_info": {
    "retrieved_chunk_count": 0,
    "query_top_k": 0,
    "query_similarity_threshold": 0.0,
    "llm_temperature": 0.0,
    "filter_type_applied": "string", // If filter was used
    "retrieved_chunks_summary": [
      {
        "type": "string",
        "name": "string",
        "source": "string",
        "line": 0,
        "distance": "string"
      }
    ]
  }
}
Error: 500 Internal Server Error on query processing failure.

13. Contributing
Contributions are welcome! If you have suggestions for improvements, bug fixes, or new features, please open an issue or submit a pull request.

Please ensure your code adheres to the existing style and conventions.

14. License
This project is licensed under the MIT License - see the LICENSE file for details.
(You'll need to create a LICENSE file in your repository if you haven't already. A simple way is to choose MIT when creating a new repo on GitHub, or copy an MIT license template.)

15.Acknowledgments
FastAPI

ChromaDB

Google Gemini API

Sentence-Transformers

Tree-sitter

  
- ### Frontend using react and tailwind 
- Built with React 18 + TypeScript, Tailwind CSS, Vite, and Lucide React, featuring responsive design, reusable components, and theme support (dark/light).
- Secure signup/login with bcrypt password hashing, Flask-Session for session management, and persistent user preferences.
- Drag-and-drop C/C++ file uploads with validation, syntax-highlighted viewer, file statistics, Mermaid diagram visualizations, and localStorage persistence.
- Animated landing page, gradient and glassmorphism effects, micro-interactions, and chat interface for seamless user engagement.
- AI-driven natural language responses for code explanation, documentation generation, and RAG-based query handling.

---
