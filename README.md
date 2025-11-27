RAG + LangChain + Ollama — Local AI Chat Application (SPA)

A fully local Retrieval-Augmented Generation (RAG) chat application running completely offline and leveraging:

Python + Flask backend

LangChain for orchestration

ChromaDB as vector store

Sentence-Transformers for embeddings

Ollama for local LLM inference

HTML + Bootstrap + Vanilla JavaScript Single-Page Application (SPA) frontend

The system lets you load PDFs, convert them into embeddings, store them in ChromaDB, and chat with an AI model that retrieves the most relevant context from those documents.

No API keys. 100% offline. Full privacy.

1. Install Required Software
✔ Install Python (3.10+)

Download from:
https://www.python.org/downloads/

During installation, enable:

Add Python to PATH

Install pip

2. Install Ollama

Download & install Ollama:
https://ollama.com/download

Verify installation:

ollama --version


Pull the required LLM (example: Gemma 3:1B):

ollama pull gemma3:1b
ollama run gemma3:1b

3. Setup Python Environment

Move to the backend folder:

cd backend


Create and activate virtual environment:

macOS / Linux
python3 -m venv venv
source venv/bin/activate

Windows (if needed)
python -m venv venv
venv\Scripts\activate

4. Install Dependencies

Install project requirements:

pip install -r requirements.txt


Contents of requirements.txt include:

flask
langchain>=0.0.300
chromadb
sentence-transformers
pypdf
ollama
uvicorn
aiofiles
python-multipart

5. Ingest PDFs Into ChromaDB

The ingestion process:

Extracts text from PDFs

Splits text into chunks

Generates embeddings

Stores everything in ChromaDB

Run:

python ingest.py


PDFs must be stored inside:

backend/pdfs/

6. Start Backend Server

Run the Flask application:

python app.py


The server will start at:

http://127.0.0.1:5000/


Endpoints:

UI: GET /

Chat API: POST /query

7. Use the Frontend (Chat UI)

Open the UI in your browser:

http://127.0.0.1:5000/

Features:

✔ Enter your question
✔ System embeds your query
✔ Retrieves relevant text chunks from PDFs
✔ LLM (via Ollama) generates an answer grounded in your documents
