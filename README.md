# 🌐 PubliQ – AI-Powered Civic Information Assistant

**AWS AI for Bharat Hackathon 2026 Submission**

PubliQ is a Retrieval-Augmented Generation (RAG) based AI assistant designed to make government schemes and public service information accessible, understandable, and verifiable for citizens across India.

---

## 🚀 Vision

To democratize access to government welfare schemes through conversational AI that is:

- Transparent  
- Multilingual  
- Accurate  
- Source-cited  
- Rural-friendly  

---

## 📌 Problem Statement

Millions of Indian citizens struggle to access and understand government schemes due to:

- Complex documentation and legal language  
- Language barriers  
- Low digital literacy  
- Information scattered across multiple PDFs and portals  
- Lack of conversational interfaces  

As a result, eligible citizens often miss critical benefits.

---

## 💡 Our Solution

PubliQ converts official government documents into an intelligent conversational knowledge system.

Using Retrieval-Augmented Generation (RAG), PubliQ:

1. Ingests government scheme documents  
2. Converts them into semantic embeddings  
3. Stores them in a vector database  
4. Retrieves relevant context based on user queries  
5. Generates grounded, citation-backed responses using AWS Bedrock  

Every response is traceable to official source documents.

---

## 🏗️ System Architecture Overview

PubliQ follows a scalable RAG architecture:

1. Document Upload & Parsing  
2. Text Chunking & Embedding Generation  
3. Storage in ChromaDB Vector Store  
4. Semantic Retrieval  
5. AWS Bedrock LLM for grounded answer generation  
6. Source-cited response delivery  

📄 Full technical details available in:

- `docs/design.md`
- `docs/requirements.md`

---

## 🎯 Target Users

- Rural Citizens  
- NGOs & Community Workers  
- Local Government Officials  
- Social Welfare Volunteers  
- Researchers & Journalists  

---

## ⭐ Key Features

### 🔍 Semantic Search
Context-aware retrieval across multiple government documents.

### 💬 Conversational AI
Natural language queries in Hindi and English.

### 📎 Source-Cited Responses
Every answer includes document references and traceable citations.

### 🌍 Multilingual Ready
Designed for Hindi and English, expandable to regional languages.

### 🔐 Security & Cost Efficiency
- IAM-restricted Bedrock access  
- Only retrieved chunks sent to LLM  
- Designed for low-bandwidth environments  

---

## ☁️ AWS Services Used

- AWS Bedrock (LLM inference)
- AWS IAM (Access Control)
- AWS S3 (Document Storage)
- AWS CloudWatch (Monitoring & Audit)

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

### Frontend (Planned)
- Web Interface (Lightweight UI)
- Mobile-ready architecture

---

## 📂 Repository Structure

```text
PubliQ
├── README.md
└── docs
    ├── requirements.md
    └── design.md
```



