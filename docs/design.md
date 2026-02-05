# PubliQ – System Design Document

## 1. System Overview

PubliQ converts government scheme documents into an intelligent conversational knowledge base using Retrieval-Augmented Generation (RAG). The system extracts, indexes, and retrieves relevant document content before generating responses using AWS Bedrock foundation models.

---

## 2. Architecture Design

### 2.1 High-Level Architecture

PubliQ consists of five main layers:

1. User Interface Layer
2. Application Backend Layer
3. Document Processing Layer
4. Data & AI Intelligence Layer
5. Security & Governance Layer

---

## 3. Architecture Diagram

```mermaid
flowchart TB

User[Citizens / NGOs / Admins]
UI[Web & Mobile Interface]
API[FastAPI Backend]

Ingest[Document Ingestion]
Extract[Text Extraction]
Chunk[Chunking]
Embed[Embedding Generator]

VDB[(ChromaDB Vector Store)]
Retrieve[Semantic Retrieval Engine]

Bedrock[AWS Bedrock Models]
Response[Source-Cited AI Response]

IAM[AWS IAM Security]

User --> UI
UI --> API

API --> Ingest
Ingest --> Extract
Extract --> Chunk
Chunk --> Embed
Embed --> VDB

API --> Retrieve
Retrieve --> VDB
VDB --> Retrieve

Retrieve --> Bedrock
Bedrock --> Response
Response --> API
API --> UI

IAM -.-> Bedrock
