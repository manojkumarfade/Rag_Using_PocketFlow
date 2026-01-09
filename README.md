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

- Open **Google Colab → Settings → Secrets**
- Add the following secret:

```text
RAGAGENTKEY = YOUR_GEMINI_API_KEY

