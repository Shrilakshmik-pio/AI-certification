RAG + LangChain + Ollama — Local AI Chat Application (SPA)

A fully local Retrieval-Augmented Generation (RAG) chat application running completely offline and leveraging:

Python + Flask backend

LangChain for orchestration

ChromaDB as vector store

Sentence-Transformers for embeddings

Ollama for local LLM inference

HTML + Bootstrap + Vanilla JavaScript SPA frontend

The system lets you load PDFs, convert them into embeddings, store them in ChromaDB, and chat with an AI model that retrieves the most relevant context from those documents.

✔ No API keys
✔ 100% offline
✔ Full privacy

1. Install Required Software

✔ Install Python (3.10+)
Download: https://www.python.org/downloads/

During installation, enable:

Add Python to PATH

Install pip

2. Install Ollama

Download & install:
https://ollama.com/download

Verify installation:

ollama --version


Pull the required LLM (example: Gemma 3:1B):

ollama pull gemma3:1b
ollama run gemma3:1b

3. Setup Python Environment

Move to backend folder:

cd backend


Create + activate virtual environment:

macOS / Linux
python3 -m venv venv
source venv/bin/activate

Windows
python -m venv venv
venv\Scripts\activate

4. Install Dependencies (UPDATED)

Install project requirements:

pip install -r requirements.txt


Updated requirements.txt contents:

flask
langchain==0.1.12
chromadb==0.5.0
sentence-transformers==2.7.0
pypdf==4.2.0
ollama==0.6.1
huggingface-hub==0.22.2
transformers==4.40.1
numpy==1.26.4
torch==2.2.2 --index-url https://download.pytorch.org/whl/cpu

5. Ingest PDFs Into ChromaDB

The ingestion process:

Extracts text from PDFs

Splits text into chunks

Generates embeddings

Stores everything in ChromaDB

Run:

python ingest.py


Store PDFs here:

backend/pdfs/

6. Start Backend Server

Run the Flask server:

python app.py


Server URL:

http://127.0.0.1:5000/


Endpoints:

UI: GET /

Chat API: POST /query

7. Use the Frontend (Chat UI)

Open in your browser:

http://127.0.0.1:5000/

Features:

✔ Ask questions
✔ Query gets embedded
✔ Relevant chunks retrieved
✔ LLM (via Ollama) answers grounded in your PDFs
