# Local AI Agent with Python (Ollama, LangChain, and RAG)

This project demonstrates how to build a fully local AI agent that answers questions about restaurant reviews using Retrieval-Augmented Generation (RAG). It uses Ollama for local models, LangChain for orchestration, and ChromaDB for vector storage.

---

## Features

* Runs entirely locally without external APIs
* Uses Retrieval-Augmented Generation (RAG)
* Stores and retrieves semantic embeddings
* Command-line interface for interaction
* Persistent vector database

---

## Tech Stack

* Python
* Ollama
* LangChain
* ChromaDB
* Pandas

---

## Project Structure

```
.
├── main.py                  # Chat loop and LLM interaction
├── vector.py                # Embeddings and vector store setup
├── realistic_restaurant_reviews.csv
├── chroma_langchain_db/     # Persistent vector database
└── README.md
```

---

## Installation

### 1. Install Ollama

Download and install Ollama from:
https://ollama.com

---

### 2. Pull required models

```bash
ollama pull llama3.2
ollama pull mxbai-embed-large
```

---

### 3. Create a virtual environment

```bash
python -m venv venv
venv\Scripts\activate
```

---

### 4. Install dependencies

```bash
pip install langchain langchain-ollama langchain-chroma pandas
```

---

## How It Works

### 1. Data Loading

Restaurant reviews are loaded from a CSV file.

### 2. Embeddings

Each review is converted into vector embeddings using:
mxbai-embed-large

### 3. Vector Storage

Embeddings are stored in ChromaDB for similarity search.

### 4. Retrieval

When a user asks a question:

* Relevant reviews are retrieved using semantic similarity
* Top 5 results are returned

### 5. Generation

The retrieved reviews and user question are passed to the LLM:
llama3.2

The model generates a final answer based on context.

---

## Usage

Run the application:

```bash
python main.py
```

Example:

```
Ask a question (q to quit): Which pizza is most popular?

Answer:
Customers frequently mention the Margherita pizza as a favorite due to its fresh ingredients and balanced flavor.
```

---

## Core Components

### Embeddings

```python
OllamaEmbeddings(model="mxbai-embed-large")
```

### Language Model

```python
OllamaLLM(model="llama3.2")
```

### Vector Store

```python
Chroma(persist_directory="./chroma_langchain_db")
```

---

## Troubleshooting

### Ollama not recognized

Ensure Ollama is added to your system PATH and restart your terminal.

### Model not found

Run:

```bash
ollama pull <model-name>
```

### Empty or poor responses

* Ensure the vector database is populated
* Delete `chroma_langchain_db` and rerun once if needed

---

## Possible Improvements

* Implement conversation memory
* Add filtering using metadata
* Support multiple datasets
* Improve retrieval strategies

---
