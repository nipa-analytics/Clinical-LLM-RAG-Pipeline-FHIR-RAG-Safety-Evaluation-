# Clinical-LLM-RAG-Pipeline-FHIR-RAG-Safety-Evaluation-
A production-style **Clinical Retrieval-Augmented Generation (RAG) system** that converts **FHIR R4 patient data into structured clinical narratives**, enables **semantic search via vector embeddings**, and provides **safe, explainable clinical question answering with hallucination detection and evaluation metrics**.

## 🚀 Project Highlights

This project simulates a **real-world clinical AI system** similar to solutions built at:

- 🏥 Abridge (Clinical AI Scribe)
- 🏥 Microsoft DAX (Clinical Documentation AI)
- 🏥 Google Health (Clinical NLP Systems)
- 🏥 IQVIA (Healthcare Analytics Platforms)

---

## ⚡ Key Features

### 🔹 1. FHIR → Clinical Text Generation
- Parses **FHIR R4 JSON bundles (Synthea format)**
- Extracts:
  - Patient demographics
  - Conditions (SNOMED → ICD-10 mapping)
  - Medications
  - Observations (LOINC vitals/labs)
  - Encounters & procedures
- Converts structured EHR data → **LLM-ready clinical narrative**

---

### 🔹 2. Smart Clinical Chunking
- Uses **semantic-aware chunking**
- Preserves medical structure:
  - Diagnoses
  - Medications
  - Labs
  - Clinical events
- Optimized for embedding models (~600 token chunks)

---

### 🔹 3. Vector Embeddings + Retrieval
- Embedding models:
  - `all-MiniLM-L6-v2` (baseline)
  - Compatible with BioBERT / PubMedBERT (production upgrade)
- Vector DB:
  - ChromaDB (persistent storage)
- Enables **semantic clinical search**

---

### 🔹 4. Clinical RAG Pipeline
- Retrieval-Augmented Generation system:
  - Query → embedding → vector search → context retrieval
  - Prompt engineering with strict clinical constraints
- Prevents hallucinations using context grounding

---

### 🔹 5. Clinical Safety Layer (Hallucination Detection)
- Medical entity extraction:
  - Diseases
  - Medications
  - Lab terms
- Evidence validation between:
  - Query vs retrieved context
- Outputs:
  - Confidence score
  - Hallucination risk (LOW / MEDIUM / HIGH)
  - Missing evidence detection

---

### 🔹 6. RAG Evaluation Framework
Implements lightweight evaluation metrics:

- 📊 Recall@K (retrieval performance)
- 📊 Context Precision
- 📊 Faithfulness score
- 📊 System-level summary metrics

Simulates **RAGAS-style evaluation pipeline**

---

### 🔹 7. FastAPI Clinical Deployment
Production-style API:

- `/query` → Clinical Q&A endpoint
- `/health` → system status

Returns structured output:
```json
{
  "question": "Does the patient have diabetes?",
  "answer": "...",
  "patient_id": "P12345",
  "confidence": 0.87,
  "hallucination_risk": "LOW",
  "evidence_snippet": "..."
}
