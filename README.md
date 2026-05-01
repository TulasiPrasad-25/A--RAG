#  Advanced RAG with LangChain

A hands-on, modular repository covering the core building blocks of **Retrieval-Augmented Generation (RAG)** using LangChain — from ingesting documents to querying with advanced retrievers.

> Built by [D. Tulasi Prasad](https://github.com/TulasiPrasad-25) · B.Tech CSE (AI & Data Science)

---

##  What is RAG?

**Retrieval-Augmented Generation (RAG)** is a technique that enhances Large Language Models (LLMs) by grounding their responses in an external knowledge base. Instead of relying solely on parametric knowledge (training data), RAG retrieves relevant documents at query time and passes them as context to the LLM — reducing hallucinations and improving factual accuracy.

---

##  Repository Structure

```
A--RAG/
├── langchain-document-loaders-main/   # Load data from various sources
├── langchain-text-splitters-main/     # Chunk documents for embedding
├── vector-Store/                      # Embed & index chunks in vector DBs
└── Retrivers/                         # Query strategies & retriever types
```

Each folder represents a standalone stage in the RAG pipeline, progressing from data ingestion through to retrieval.

---

##  Module Breakdown

### 1. 📄 Document Loaders — `langchain-document-loaders-main/`

Covers how to ingest data from multiple sources and convert them into LangChain `Document` objects.

| Loader | Source |
|--------|--------|
| `TextLoader` | Plain `.txt` files |
| `PyPDFLoader` | PDF documents |
| `CSVLoader` | Structured tabular data |
| `WebBaseLoader` | Live web pages / URLs |
| `DirectoryLoader` | Bulk load from folders |

---

### 2.  Text Splitters — `langchain-text-splitters-main/`

Large documents must be chunked before embedding. This module explores splitting strategies that preserve semantic coherence.

- `RecursiveCharacterTextSplitter` — splits by hierarchy of separators (recommended default)
- `CharacterTextSplitter` — splits by a single delimiter
- `TokenTextSplitter` — splits by token count (LLM-aware)
- Configurable `chunk_size` and `chunk_overlap` for controlling context continuity

---

### 3.  Vector Stores — `vector-Store/`

Embeddings are stored in vector databases optimized for similarity search. This module covers:

- Generating embeddings with **OpenAI / HuggingFace** models
- Storing and indexing with **FAISS** and/or **Chroma**
- Performing `similarity_search` and `MMR` (Maximal Marginal Relevance) queries
- Persisting vector stores to disk for reuse

---

### 4.  Retrievers — `Retrivers/`

Retrievers are the interface between the vector store and the LLM. This module explores multiple retrieval strategies:

- **VectorStoreRetriever** — basic top-k similarity search
- **MultiQueryRetriever** — generates multiple query variants to improve recall
- **ContextualCompressionRetriever** — filters and compresses retrieved docs to only relevant passages
- **ParentDocumentRetriever** — embeds small chunks but retrieves full parent documents
- **SelfQueryRetriever** — parses natural language into structured metadata filters

---

##  RAG Pipeline Overview

```
Raw Data
   │
   ▼
Document Loaders  ──→  Documents
   │
   ▼
Text Splitters    ──→  Chunks
   │
   ▼
Embedding Model   ──→  Vectors
   │
   ▼
Vector Store      ──→  Indexed DB (FAISS / Chroma)
   │
   ▼
Retriever         ──→  Relevant Chunks
   │
   ▼
LLM + Context     ──→  Grounded Answer
```

---

##  Tech Stack

| Tool | Purpose |
|------|---------|
|  **LangChain** | RAG orchestration framework |
|  **HuggingFace / OpenAI** | Embedding models |
|  **FAISS** | Fast local vector similarity search |
|  **Chroma** | Persistent local vector store |
|  **Python** | Core language (100%) |
|  **Jupyter Notebooks** | Interactive exploration |

---

##  Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/TulasiPrasad-25/A--RAG.git
cd A--RAG
```

### 2. Install dependencies
```bash
pip install langchain langchain-community openai faiss-cpu chromadb \
            sentence-transformers pypdf tiktoken
```

### 3. Set your API key (if using OpenAI)
```bash
export OPENAI_API_KEY="your-api-key-here"
```

### 4. Run notebooks
Open any `.ipynb` file inside the module folder of your choice with Jupyter:
```bash
jupyter notebook
```

---

##  Learning Path

Recommended order for exploring this repo:

```
1. langchain-document-loaders-main  →  How to load data
2. langchain-text-splitters-main    →  How to chunk data
3. vector-Store                     →  How to embed & store
4. Retrivers                        →  How to retrieve smartly
```

---

##  Author

**D. Tulasi Prasad**    
 tulasiprasad2526@gmail.com  
 [LinkedIn](https://linkedin.com/in/tulasi-prasad-077350284) · [GitHub](https://github.com/TulasiPrasad-25)

---


This repository is for educational purposes. Feel free to fork, learn, and build on it.
