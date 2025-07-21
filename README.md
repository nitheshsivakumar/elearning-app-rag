# 🔍 Retrieval-Augmented Generation (RAG) – Serverless AI Assistant on AWS

This project demonstrates a **Retrieval-Augmented Generation (RAG)** use case using AWS services. It enables users to query AI models that **respond based on your own documents**, rather than generic knowledge.

---

## 📘 What is RAG?

**RAG (Retrieval-Augmented Generation)** is an AI architecture that combines two components:
1. **Retrieval**: Pulls relevant information from external data sources (like documents, PDFs, etc.).
2. **Generation**: Feeds the retrieved content into a Large Language Model (LLM) to generate accurate, context-based responses.

✅ **Why RAG?**
- Ensures the output is grounded in your data  
- Reduces hallucination by LLMs  
- Enables domain-specific Q&A over custom datasets

---

## 📌 Architecture

![RAG Architecture](Screenshot%202025-07-20%20at%209.53.19%20PM.png)

---

## ⚙️ How It Works

### 1. Upload Documents
- PDF files or lecture materials are uploaded to an **Amazon S3 bucket**.

### 2. Chunking & Embeddings
- The content is split into smaller chunks.
- Each chunk is converted into a **vector embedding** using **Amazon Titan Embeddings**.

### 3. Vector Storage
- The embeddings are stored in an **OpenSearch vector database**, making them searchable.

### 4. Knowledge Base Creation
- A **Knowledge Base** is set up in **Amazon Bedrock** linking the S3 documents and OpenSearch vector store.

### 5. API Integration
- Users send a query via **API Gateway**.
- The query is routed to an **AWS Lambda** function which:
  - Invokes Bedrock’s **Retrieve and Generate** API
  - Retrieves relevant context from the knowledge base
  - Passes the context to the **Claude Foundation Model** for response generation
  - Returns the AI-generated, context-rich response back to the user via API Gateway

---
