# 🧠 Retrieval-Augmented Generation (RAG) Using PocketFlow  
**Zero LangChain • Explicit Orchestration • Gemini + FAISS**

---

## 📌 Overview

This repository implements a **complete Retrieval-Augmented Generation (RAG) system** using a **custom PocketFlow orchestration engine**.  
The system loads a PDF, builds a vector index, retrieves relevant context, and generates grounded answers using **Google Gemini** — **without LangChain or hidden abstractions**.

Everything is explicit, debuggable, and framework-free.

---

## 🚀 What This Project Does

- Loads a PDF document
- Extracts raw text from pages
- Splits text into overlapping chunks
- Generates vector embeddings
- Stores embeddings in **FAISS**
- Accepts user questions via terminal
- Retrieves relevant document chunks
- Builds a grounded prompt
- Generates answers using **Gemini**
- Loops until the user exits

---

## 🛠️ Tech Stack

### Core Libraries
- **Python**
- **FAISS (faiss-cpu)** — vector similarity search
- **pypdf** — PDF text extraction
- **sentence-transformers** — embedding generation
- **google-generativeai** — Gemini LLM access

### Architecture
- **PocketFlow (custom implementation)** — workflow orchestration
- **No LangChain**
- **No implicit pipelines**
- **Explicit data flow**

---

## 🧠 Why PocketFlow?

PocketFlow is used instead of LangChain to achieve:

- Full control over execution
- Explicit step-by-step logic
- Conditional routing
- Easy debugging
- Interview- and production-friendly architecture

This project demonstrates **how RAG works internally**, not just how to call a framework.

---

## 🧩 High-Level Architecture

User Input
↓
FAISS Retriever
↓
Prompt Builder
↓
Gemini LLM
↓
Answer Display
↓
Repeat


Input
  → Retrieve
      → Prompt
          → Gemini
              → Display
                  → Input

---

## 🔐 API Key Setup (Google Colab)

- Open **Colab → Settings → Secrets**
- Add the following secret:


- The API key is loaded securely at runtime  
- No API keys are hard-coded in the source code

---

## 📄 PDF Processing

### PDF Loading

- Uses **pypdf** to extract text from each page
- Combines all extracted text into a single string

### Text Chunking

- Chunk size: **200 characters**
- Overlap: **50 characters**
- Preserves semantic continuity across chunks

---

## 🧬 Embeddings & Vector Storage

### Embeddings

- Model: **all-MiniLM-L6-v2**
- Converts text chunks into dense numerical vectors

### FAISS Vector Store

- Index type: **IndexFlatL2**
- Enables fast semantic similarity search
- Stores all embeddings in memory

---

## 🔍 Retrieval Logic

- User question is converted into an embedding
- FAISS performs similarity search
- Top-K relevant chunks are returned
- Retrieved chunks are used as context

This represents the **retrieval** stage of RAG.

---

## 🤖 Gemini Generation

- Model: **Gemini 2.5 Flash**

### Input
- Retrieved context
- User question

### Prompt Rules
- Use **only** the provided context
- Do **not** hallucinate

### Output
- Grounded, document-based answer

---

## 🧩 PocketFlow Engine

### Core Concepts

- **Node** — one unit of work
- **Flow** — orchestrates node execution
- **Actions** — control transitions between nodes
- **Shared State** — passes data across nodes

This replaces LangChain’s implicit chains with **explicit orchestration logic**.

---

## 🧱 PocketFlow Nodes Used

### InputNode
- Accepts user questions
- Detects exit command
- Stores current question

### RetrieveNode
- Queries FAISS
- Retrieves relevant document chunks
- Stores `{question, context}`

### PromptNode
- Builds the RAG prompt
- Enforces context-only answers

### GeminiNode
- Calls the Gemini API
- Handles empty or blocked responses
- Stores the generated answer

### DisplayNode
- Prints the final answer
- Clears shared state
- Loops back to input

---

## 🔗 Flow Wiring

Input
→ Retrieve
→ Prompt
→ Gemini
→ Display
→ Input


### Conditional Transitions Enable

- Continuous interaction
- Clean exit handling
- Safe execution paths

---

## ▶️ How to Run

1. Upload a PDF to Google Drive
2. Update the PDF path in the code
3. Add the Gemini API key to Colab Secrets
4. Run all notebook cells
5. Ask questions in the terminal
6. Type `exit` to stop

---

## ✅ What This Project Demonstrates

- RAG without frameworks
- Direct FAISS usage
- Manual prompt engineering
- Gemini LLM integration
- Explicit agent-style orchestration
- Production-grade reasoning flow

---

## 🧠 Interview Explanation

> *“I built a Retrieval-Augmented Generation system using a custom PocketFlow engine.  
> I manually implemented PDF parsing, chunking, embedding generation, FAISS indexing, retrieval, prompt construction, and Gemini-based generation — without using LangChain abstractions.”*

---

## 🔮 Possible Extensions

- Async PocketFlow RAG
- Conversation memory
- Multi-document retrieval
- Tool-augmented RAG
- Streamlit or web UI
- Query routing agents
- RAG evaluation metrics

---

## 📌 Final Note

This repository focuses on **understanding over shortcuts**.  
If you understand this code, you understand RAG.

