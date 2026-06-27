# 🏥 Clinical LLM RAG Pipeline (FHIR + Safety-Aware Healthcare AI)

A production-style **Retrieval-Augmented Generation (RAG) system for clinical EHR data** built using **FHIR R4, vector databases, and biomedical NLP models**.

---

## 🚀 Key Features

- 🏥 **FHIR R4 Clinical Data Ingestion (Synthea-compatible)**
- 🧠 **Clinical Document Generation from EHR Bundles**
- ✂️ **Smart Clinical Chunking for Medical Context Preservation**
- 🔍 **Vector Search using Sentence Transformers**
- 🗂️ **ChromaDB Vector Store (local, HIPAA-safe design pattern)**
- 🤖 **RAG-based Clinical Question Answering**
- 📄 **Automated EHR Summarization**
- ⚠️ **Clinical Hallucination Detection Layer (Safety-Aware AI)**
- 🧪 **Retrieval Evaluation across clinical scenarios**

---

## 🏗️ System Architecture
FHIR R4 Bundles (Synthea)
↓
Clinical Data Extraction (Python)
↓
Clinical Document Construction
↓
Text Chunking (LangChain)
↓
Embeddings (SentenceTransformers / BGE / ClinicalBERT)
↓
Vector Store (ChromaDB)
↓
RAG Retrieval Engine
↓
LLM Answer + Safety Layer
↓
Clinical Output (QA / Summary / Risk Insights)



---

## 🧪 Tech Stack

- **Python 3.10**
- **FHIR R4 (HL7 Standard)**
- **LangChain**
- **SentenceTransformers (all-MiniLM / BGE models)**
- **ChromaDB**
- **FAISS (optional extension)**
- **NumPy / Pandas**
- **Jupyter Notebooks**
- **FastAPI (for deployment-ready API layer)**

---

## 📁 Project Structure

```

clinical-llm-rag-pipeline/
│
├── 01\_clinical\_rag\_pipeline.ipynb     # FHIR ingestion + preprocessing
├── 02\_chunking\_embeddings.ipynb       # Chunking + vector embedding
├── 03\_rag\_qa\_pipeline.ipynb           # Clinical question answering
├── 04\_safety\_layer.ipynb              # Hallucination detection layer
│
├── data/
│   └── fhir/                           # Synthea FHIR R4 bundles
│
├── output/
│   ├── vectorstore/                    # ChromaDB persistence
│   └── reports/                        # Evaluation outputs
│
├── app/
│   └── api.py                          # FastAPI inference endpoint
│
├── requirements.txt
└── README.md

⚙️ How It Works
1. FHIR Data Ingestion
Parses Synthea-generated FHIR R4 bundles
Extracts:
Conditions (SNOMED → ICD-10 mapping)
Medications
Observations (LOINC labs/vitals)
Encounters & Procedures

2. Clinical Document Construction
Converts structured EHR → LLM-readable clinical narrative
Preserves medical context (diagnosis, labs, medications)

3. Chunking Strategy
Uses clinical-aware recursive chunking
Preserves:
Diagnosis blocks
Medication sections
Vitals & labs continuity

4. Vector Embedding Layer
Model: all-MiniLM-L6-v2 (lightweight baseline)
Optional upgrade:
BioBERT
ClinicalBERT
BGE-large-medical

5. Retrieval-Augmented Generation (RAG)
Queries clinical embeddings
Retrieves top-k patient context
Feeds into LLM for:
Question Answering
Clinical summarization

6. Safety Layer (Key Differentiator)
Detects hallucinated or unsupported medical claims
Flags:
Unsupported diagnoses
Missing evidence in retrieved context
Overconfident LLM outputs


--- Author
Nipa Shah
MS Business Analytics
Healthcare AI | Clinical NLP | Responsible AI
GitHub: https://github.com/nipa-analytics
