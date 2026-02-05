# PubliQ – Requirements Specification

## 1. Project Overview

### 1.1 Project Name
PubliQ – AI-powered community assistant for government scheme and public service document access.

### 1.2 Objective
PubliQ aims to bridge the information accessibility gap between government documentation and citizens by providing a conversational AI interface that delivers accurate, source-verified responses from official scheme documents.

---

## 2. Problem Statement

Millions of citizens in India are eligible for government welfare schemes but fail to benefit due to:

- Complex and lengthy policy documents
- Language and literacy barriers
- Scattered information across multiple sources
- Lack of reliable verification methods
- Dependency on intermediaries for guidance

---

## 3. Target Users

### Primary Users
- Rural and semi-urban citizens
- Community workers and NGOs
- Local administrative staff

### Secondary Users
- Social workers
- Policy awareness volunteers
- Public service support organizations

---

## 4. Goals & Success Criteria

### Goals
- Simplify access to government scheme information
- Provide trustworthy, source-backed responses
- Support multilingual interaction
- Ensure low bandwidth accessibility

### Success Metrics
- ≥ 90% answer accuracy
- ≤ 2 seconds average response time
- Ability to handle multiple documents
- High user satisfaction and usability

---

## 5. Key Use Cases

1. Scheme eligibility verification
2. Required documentation clarification
3. Application process explanation
4. Policy interpretation and comparison
5. Multi-document information retrieval

---

## 6. Functional Requirements

### 6.1 Document Management
- Upload PDF, DOCX, TXT, and HTML files
- Batch document upload
- Maximum file size up to 100MB
- Persistent document storage

### 6.2 Document Processing
- Text extraction from uploaded files
- Chunking of documents into semantic segments
- Embedding generation for vector search

### 6.3 Conversational AI
- Natural language query support
- Multi-turn conversation memory
- Source-cited responses
- Semantic search across documents

### 6.4 Language Support
- Hindi and English queries
- Code-mixed language understanding
- Expandable to regional languages

### 6.5 Response Transparency
- Citation of document name and section
- Extract display for verification

---

## 7. Non-Functional Requirements

### Performance
- Query response time < 2 seconds
- Efficient vector retrieval

### Scalability
- Serverless-compatible backend
- Ability to scale to large user bases

### Security
- IAM-based least privilege access
- Secure Bedrock model invocation
- Privacy-first data storage

### Reliability
- 99.9% service availability
- Fault-tolerant backend design

### Accessibility
- Mobile-friendly UI
- Low-bandwidth optimization

---

## 8. Constraints

- Only retrieved document chunks sent to LLM
- System must remain cost-efficient
- Must prevent hallucinated responses
- Must support community-level deployment

---

## 9. Assumptions

- Government documents are publicly available
- Users possess basic smartphone or web access
- AWS Bedrock models provide multilingual capability

---

## 10. Future Scope

- Voice-based interaction
- WhatsApp chatbot integration
- Offline document querying
- Expanded regional language support
