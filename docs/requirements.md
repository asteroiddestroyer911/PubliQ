# PubliQ - Requirements Document

**AI-Powered Civic Assistant for Government Scheme Discovery**

**AWS AI for Bharat Hackathon | February 2026**

---

## 1. Project Title

**PubliQ** – AI-powered community assistant for government scheme access

An intelligent civic assistant that democratizes access to government welfare schemes through conversational AI, enabling citizens to understand complex policies in their native language with verifiable source citations.

---

## 2. Problem Statement

Citizens across India face significant barriers in accessing government welfare schemes:

- **Information Complexity**: Lengthy technical documents scattered across multiple PDFs and portals with no centralized search
- **Language Barriers**: Most documents only in English, limited regional language support, low digital literacy
- **Trust Issues**: Misinformation spreads through unofficial channels without verifiable source citations
- **Accessibility**: Limited rural connectivity, complex portal navigation, no conversational interface

**Impact**: Millions of eligible citizens miss out on welfare benefits, leading to scheme underutilization and perpetuating inequality.

---

## 3. Project Goal

Bridge the information gap between citizens and government schemes through an AI-powered conversational assistant that provides accurate, source-cited answers.

**Core Objectives**:
1. Enable document upload (PDF, DOCX, HTML) and automatic processing into searchable knowledge base
2. Provide grounded AI responses using RAG to prevent hallucinations
3. Support Hindi and English with cross-lingual retrieval
4. Include verifiable citations (document name, section, page number)
5. Optimize for low-bandwidth rural environments

**Success Vision**: Empower citizens to discover schemes through simple conversations, reducing intermediary dependency and increasing enrollment.

---

## 4. Target Users

**Primary Users**:
1. **Rural Citizens**: Low digital literacy, Hindi speakers; need simple explanations for scheme discovery
2. **NGOs & Community Workers**: Field workers assisting multiple beneficiaries with quick lookups
3. **Local Administrators**: Panchayat officials needing accurate policy interpretation

**Secondary Users**: Students, researchers, journalists for policy analysis and fact-checking

---

## 5. Key Use Cases

| Use Case | User | Query Example | Expected Output |
|----------|------|---------------|-----------------|
| **Eligibility Check** | Rural citizen | "क्या मैं PM-KISAN के लिए पात्र हूं?" | Eligibility criteria with citations |
| **Document Requirements** | NGO worker | "What documents needed for Ayushman Bharat?" | Checklist with source references |
| **Process Explanation** | Administrator | "MGNREGA application process?" | Step-by-step guide with timelines |
| **Policy Interpretation** | Journalist | "What changed in NEP 2024?" | Key changes with document references |
| **Scheme Comparison** | Researcher | "Compare PM-KISAN and PM-KUSUM" | Side-by-side comparison with citations |

---

## 6. Functional Requirements

### FR-1: Document Management

- Support PDF, DOCX, TXT, HTML (max 50 MB, batch upload up to 10 files)
- Capture metadata: scheme name, category, publication date, source URL
- Validate format, check duplicates, provide error messages
- Store in AWS S3 with version history and admin-authorized deletion

### FR-2: Document Processing

- Extract text preserving structure (headings, sections, tables)
- Clean text (remove headers/footers), normalize whitespace, detect language
- Chunk into ~1000 tokens with 100-token overlap
- Retain metadata: document ID, page number, section, language

### FR-3: Embedding & Vector Storage

- Generate 384-dim vectors using multilingual Sentence Transformers
- Store in ChromaDB with metadata: `document_id`, `chunk_id`, `scheme_name`, `page_number`, `language`, `source_url`
- Support incremental indexing and index rebuild

---

### FR-4: Query Processing

- Accept Hindi/English text queries (max 500 chars) with multi-turn context retention
- Convert query to embedding and perform cosine similarity search in ChromaDB
- Retrieve top-K chunks (K=5-10) with relevance score >0.5
- Assemble context with metadata for LLM prompt

### FR-5: Answer Generation

- Use AWS Bedrock (Claude 3/Titan) with grounding prompt: "Answer ONLY from context"
- Generate response in user's query language
- Validate citations and assign confidence score
- Return "No information found" with suggested queries when no relevant docs exist

### FR-6: Citation & Source Attribution

- Include scheme name, document title, section/page number with clickable links
- Display relevance scores for transparency
- Enable viewing original document sections with highlighted text

### FR-7: Conversational Interface

- Maintain last 5 exchanges for follow-up questions
- Display typing indicators, progressive loading, copy-to-clipboard
- Support feedback (thumbs up/down) and conversation reset
- Auto-detect language with manual switching option

### FR-8: Administration

- Admin dashboard: view documents, monitor queries, review feedback, access metrics
- Analytics: track popular schemes, identify knowledge gaps, generate usage reports

---

## 7. Non-Functional Requirements

### NFR-1: Performance
- Query response: <2s (95th percentile), semantic search: <500ms, LLM: <1.5s
- Support 100 concurrent users, 10,000 queries/day, 50 document uploads/day

### NFR-2: Scalability
- Stateless FastAPI with AWS ECS/Lambda auto-scaling
- Support 10,000+ documents, 1M+ vectors, 100,000+ users
- CDN for static content

### NFR-3: Reliability
- 99.5% uptime with graceful degradation and automatic failover
- Retry logic for transient failures, comprehensive error logging

### NFR-4: Security
- AWS IAM least-privilege policies, role-based admin access
- Rate limiting: 100 requests/hour per IP
- TLS encryption, no PII storage, query anonymization
- Audit logging, 90-day log retention

### NFR-5: Cost Efficiency
- Target: <₹15,000/month for 10,000 users
- Open-source components, AWS Free Tier, LLM caching, batch processing

### NFR-6: Usability
- Mobile-responsive (320px+ screens), WCAG 2.1 Level AA target
- Low-bandwidth optimized (2G/3G), zero training required

### NFR-7: Maintainability
- Modular architecture, >80% test coverage, automated deployment
- CloudWatch monitoring with alerting and dashboards

### NFR-8: Compatibility
- Browsers: Chrome, Firefox, Safari, Edge (latest 2 versions)
- Devices: Desktop, tablet, mobile (320px+ width)

---

## 8. Constraints

**Technical**:
- Only retrieved chunks sent to LLM (max 8,000 tokens context window)
- Initial release: Hindi/English only (regional languages future)
- Supported formats: PDF, DOCX, TXT, HTML (OCR for scanned PDFs future)

**Business**:
- Budget: <₹15,000/month for NGO affordability
- Timeline: MVP in 4-6 weeks, pilot 2 months post-hackathon

**Regulatory**:
- No PII storage without consent, comply with Indian data protection laws
- Responses grounded in official documents with verification disclaimer
- No medical/legal/financial advice

**Operational**:
- AWS-based deployment with Bedrock LLM (hackathon requirement)
- Automated processing with minimal manual intervention

---

## 9. Success Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| **Answer Accuracy** | ≥90% | Expert review of 100 random responses (weekly) |
| **Citation Accuracy** | ≥95% | Automated validation + spot checks (daily) |
| **Hallucination Rate** | ≤2% | Automated detection + user feedback (continuous) |
| **Response Latency** | ≤2s (95th percentile) | API response time tracking (real-time) |
| **System Uptime** | ≥99.5% | Health check monitoring (continuous) |
| **User Satisfaction** | ≥4.0/5.0 | Post-query feedback (weekly aggregation) |
| **Query Success Rate** | ≥85% | "No info found" rate + feedback (daily) |
| **Return User Rate** | ≥60% within 7 days | Session tracking (weekly) |
| **Document Coverage** | 100+ schemes | Knowledge base count (monthly) |
| **Query Volume** | 10,000+/day at scale | API logs (daily) |
| **PDF Reading Reduction** | 70% time saved | User surveys (monthly) |

---

## 10. Acceptance Criteria

| Criteria | Validation Method |
|----------|-------------------|
| **Document Upload** | Upload 10 PDFs/DOCX; verify processing <30s, dashboard display, error handling |
| **Query & Response** | Test 50 diverse queries; verify <2s response, citations included, fallback handling |
| **Multilingual** | Test 20 Hindi + 20 English queries; verify cross-lingual retrieval, ≥95% language detection |
| **Citations** | Verify 30 random responses; check ≥95% accuracy, clickable links, document references |
| **Multi-Document** | Upload 5 related schemes; test comparison queries, verify synthesis and distinct citations |
| **Conversation Context** | Test 10 multi-turn conversations; verify 5-exchange history, follow-ups, reset option |
| **Performance** | Load test 100 concurrent users for 10 min; verify 95% <2s response, no crashes |
| **Security** | Security audit; verify authentication, rate limiting, no PII storage, TLS encryption |
| **Error Handling** | Test invalid inputs, network failures; verify clear messages, retry logic, logging |
| **User Experience** | Test on mobile with 3G throttling; verify 320px+ responsive, <3s load, feedback option |

---

## 11. Out of Scope (Future Enhancements)

Voice I/O, regional languages, WhatsApp/Telegram bots, offline mode, personalized recommendations, OCR for scanned PDFs, native mobile apps, government portal integration, advanced analytics, multi-tenancy

## 12. Assumptions & Dependencies

**Assumptions**: Digital documents available (PDF/DOCX), basic device access, internet connectivity, stable AWS pricing, no legal restrictions on document use, users verify critical decisions, admin technical literacy

**Dependencies**:
- AWS: Bedrock (Claude 3/Titan), S3, IAM, ECS/EC2, CloudWatch
- Open-source: ChromaDB, FastAPI, Sentence Transformers, LangChain
- HuggingFace for embedding models

---

**AWS AI for Bharat Hackathon | February 2026 | v1.0**
