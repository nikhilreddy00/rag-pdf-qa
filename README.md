# RAG-based PDF Question Answering (LangChain + FAISS/Chroma + Groq)

A complete **Retrieval-Augmented Generation (RAG)** project that lets you ask questions over **PDF documents** (single or multiple PDFs) and get **grounded answers** using **LangChain** + **vector search** + a **Groq-powered LLM**.

> Why RAG?  
> LLMs don’t “know” your PDFs by default. RAG retrieves the most relevant parts of your PDFs and feeds them to the LLM so the answer is based on your documents (reducing hallucinations).

---

## ✅ What this project does

### You can:
- Upload / load PDF documents (single or multiple)
- Extract text from PDFs
- Split text into chunks (so long PDFs fit into the model context)
- Convert chunks into embeddings (vector representations)
- Store embeddings in a vector database (FAISS or Chroma)
- Retrieve the most relevant chunks for a user query
- Send retrieved context to the LLM (Groq) to generate an answer
- (Optional) Run the same pipeline in notebooks for experimentation

---

## 🧠 RAG Pipeline (Step-by-step)

This project follows a standard RAG pipeline:

### 1) Document Loading (PDF → text)
PDFs are loaded using libraries like:
- **PyPDF** (simple and widely used)
- **PyMuPDF** (often faster and better with complex PDFs)

**Goal:** extract raw text from each page.

---

### 2) Text Splitting (text → chunks)
PDFs can be very long. LLMs have input limits, so we break text into chunks.

**Why chunking matters:**
- Smaller chunks = more precise retrieval
- Overlap helps preserve meaning across chunk boundaries

**Typical parameters:**
- `chunk_size`: e.g., 800–1500 characters
- `chunk_overlap`: e.g., 100–200 characters

---

### 3) Embeddings (chunks → vectors)
Each chunk is converted into a numeric vector using **SentenceTransformers**.

**Why embeddings?**
- They represent meaning, not exact words.
- So queries like “project goal” will match “objective” chunks too.

---

### 4) Vector Store (vectors → searchable DB)
Vectors are stored in a database that supports similarity search:

- **FAISS**: fast local in-memory similarity search
- **ChromaDB**: persistent local DB (stores vectors + metadata)

**Result:** we can quickly find which chunks are most similar to the question.

---

### 5) Retrieval (question → relevant chunks)
Given a query like:
> “What methodology is used in this paper?”

The retriever finds the top-k matching chunks based on semantic similarity.

**Optional retrieval improvements:**
- MMR (Max Marginal Relevance) to reduce duplicate chunks
- Metadata filtering (doc name, page number)

---

### 6) Generation (relevant chunks + question → answer)
Finally, the retrieved chunks are passed to the LLM (Groq) in a prompt like:

- **Context:** retrieved text chunks
- **Question:** user query
- **Instruction:** answer only using context

This produces a grounded final response.

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



