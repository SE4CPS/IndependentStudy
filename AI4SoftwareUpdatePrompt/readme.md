# AI4SoftwareUpdatePrompt

## Overview

AI4SoftwareUpdatePrompt is an **agent-based Retrieval-Augmented Generation (RAG)** system designed to **retrieve, analyze, and recommend software updates** using **semantic vector search**.

Unlike keyword-based systems, this project leverages **dense embeddings and a persistent local vector database** to improve the relevance, accuracy, and explainability of software update retrieval.

The focus of this work is on **system design, agentic retrieval, and vector database persistence**, rather than UI or cloud deployment.

---

## Key Features

- **Agent-based retrieval pipeline**
- **Semantic search** using dense embeddings
- **Local persistent vector database (ChromaDB)**
- **Top-K similarity retrieval**
- **Reproducible and inspectable storage**
- No cloud dependency required

---

## System Architecture

Text Documents
↓
SentenceTransformer (all-mpnet-base-v2)
↓
Vector Embeddings
↓
ChromaDB (SQLite-backed persistent store)
↓
Top-K Semantic Retrieval

---

## Project Structure

AI4SoftwareUpdatePrompt/
├── app.py                      # Main orchestration / entry point
├── agent_factory_gemini.py     # Agent construction logic
├── requirements.txt            # Dependencies
├── Dockerfile                  # Container configuration
├── src/
│   ├── build_real_chroma.py    # Build persistent vector database
│   ├── open_chroma_db.py       # Inspect collections & counts
│   ├── query_chroma.py         # Semantic search queries
│   └── inspect_chroma.py       # Debug / inspection utilities
├── scripts/                    # Helper scripts
├── documentation/              # Project documentation
└── README.md

> Local vector stores and generated artifacts are excluded from version control via `.gitignore`.

---

## Technologies Used

- Python
- ChromaDB (SQLite-backed vector database)
- FAISS (nearest-neighbor search backend)
- SentenceTransformers (`all-mpnet-base-v2`)
- HuggingFace Datasets

---

## Setup & Installation

### 1️⃣ Create virtual environment
```bash
python3 -m venv venv
source venv/bin/activate

2️⃣ Install dependencies

pip install -r requirements.txt

Build the Vector Database

This step creates a local persistent ChromaDB:

python src/build_real_chroma.py

Expected output:
Loaded dataset rows: 50
Inserted 50/50
Done. Count: 50

Inspect the Database

View collections and document counts:

python src/open_chroma_db.py

Example output:

Collections: ['release_notes']
release_notes -> count=50

Query the Database

Run semantic similarity search:

python src/query_chroma.py

Example query:

October 2024 software update

The system retrieves the most contextually relevant software updates.

⸻

Key Learnings
	•	Semantic embeddings outperform keyword search for update retrieval
	•	Persistent vector databases eliminate repeated re-embedding
	•	ChromaDB enables both API-level and SQLite-level inspection
	•	Agent-based retrieval improves modularity and reasoning flow

⸻

Academic Context

This project was developed as part of an Independent Study focused on:
	•	Agentic AI systems
	•	Vector databases
	•	Retrieval-Augmented Generation (RAG)
	•	Practical and reproducible ML system design

⸻

Author

Mohammed Fahad
Graduate Student – Computer Science
University of the Pacific

