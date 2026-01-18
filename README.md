# RAG-based PDF Question Answering System

An end-to-end Retrieval-Augmented Generation (RAG) application that allows users to ask natural language questions over PDF documents using LangChain, vector databases, and a Groq-powered LLM.

---

## 🚀 Features
- Load and process single or multiple PDF files
- Chunk and embed documents using SentenceTransformers
- Store embeddings in FAISS / ChromaDB vector stores
- Retrieve relevant context using semantic search
- Generate grounded answers with Groq LLM via LangChain
- Supports conversational question answering

---

## 🏗 Architecture
![RAG Pipeline](assets/architecture.svg)

---

## 🛠 Tech Stack
- Python
- LangChain
- FAISS / ChromaDB
- SentenceTransformers
- Groq LLM
- PyPDF / PyMuPDF
- Streamlit (for UI version)

---

## ⚙️ Installation

```bash
git clone https://github.com/nikhilreddy00/rag-pdf-qa.git
cd rag-pdf-qa
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
