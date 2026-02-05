# 🌐 PubliQ – AI-Powered Public Information Assistant

🚀 PubliQ is an AI-driven civic information platform designed to democratize access to government schemes, policies, and public service documents across India using Retrieval-Augmented Generation (RAG) powered by AWS Bedrock.

---

## 📌 Problem Statement

Millions of Indian citizens struggle to access and understand government scheme documents due to:

- Complex and lengthy documentation
- Language barriers
- Low digital literacy
- Scattered information across multiple sources
- Lack of conversational and accessible interfaces

This leads to citizens missing critical benefits, services, and opportunities.

---

## 💡 Our Solution

PubliQ converts government documents into an intelligent conversational knowledge system.

Users can:

- Upload scheme documents (PDF/DOCX/TXT)
- Ask questions in natural language
- Receive verified answers with source citations
- Access multilingual AI assistance
- Get real-time responses even on low-bandwidth networks

PubliQ uses Retrieval-Augmented Generation (RAG) to ensure responses are accurate, grounded, and trustworthy.

---

## 🎯 Target Users

- Rural Citizens
- Community NGOs
- Government Field Workers
- Social Welfare Volunteers
- Local Administrative Bodies

---

## ⭐ Key Features

### 📤 Document Upload & Processing
- Supports PDF, DOCX, TXT formats
- Automated text extraction and preprocessing
- Batch upload support

### 🔍 Semantic Search Engine
- Context-aware query understanding
- Multi-document knowledge retrieval
- Vector-based document indexing

### 💬 Conversational AI Interface
- Multi-turn dialogue support
- Memory-based contextual responses
- Natural language interaction

### 🌍 Multilingual Accessibility
- Hindi and English support
- Regional language expansion ready
- Voice integration ready architecture

### 📎 Source-Verified Responses
- Chunk-level citation references
- Transparent and trustworthy answers
- Reduces AI hallucinations

### 🔐 Security & Privacy First
- Local vector database storage
- IAM restricted AWS Bedrock access
- Cost-controlled AI model invocation

---

## 🏗️ System Architecture Overview

PubliQ follows a scalable Retrieval-Augmented Generation architecture:

1. Users upload government documents
2. Backend extracts and chunks document text
3. Text converted into semantic embeddings
4. Stored inside ChromaDB vector store
5. User queries retrieve relevant document chunks
6. AWS Bedrock generates grounded AI responses
7. Answers returned with source citations

---

## ☁️ AWS Services Used

- AWS Bedrock (Claude / Titan Models)
- AWS IAM (Security & Access Control)
- AWS CloudWatch (Monitoring)
- AWS Serverless Ready Backend Architecture

---

## 🧩 Technology Stack

### Backend
- Python
- FastAPI
- LangChain

### AI & NLP
- AWS Bedrock
- Sentence Transformers
- Retrieval-Augmented Generation (RAG)

### Database
- ChromaDB (Vector Database)

### Frontend
- HTML
- CSS
- JavaScript
- Streamlit / Web UI (Prototype)

---

## 📂 Project Structure

PubliQ/
│
├── docs/
│ ├── requirements.md
│ └── design.md
│
├── diagrams/
│ ├── architecture.mmd
│ └── process_flow.mmd
│
├── src/
│
└── README.md

---

## ⚙️ Installation & Setup

### Step 1: Clone Repository
```bash
git clone https://github.com/your-username/publiq.git
cd publiq
