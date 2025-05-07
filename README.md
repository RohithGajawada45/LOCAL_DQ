# Local Document QA (RAG System)

A Retrieval-Augmented Generation (RAG) system that allows you to query PDF documents using natural language.

## Features
- PDF document ingestion and processing
- Vector database storage (ChromaDB)
- Natural language querying using Mistral via Ollama
- Simple command line interface

## Prerequisites
- Python 3.8+
- Ollama running locally (for Mistral LLM)
- PDF documents to query (place in `data/` directory)

## Installation
1. Clone this repository
2. Install dependencies:
```bash
pip install -r requirements.txt
```
3. Install Ollama (if not already installed):
```bash
brew install ollama
ollama pull mistral
ollama serve
```

## Usage
1. **Populate the database** with your PDF documents:
```bash
python populate_database.py
```
   - Place PDFs in the `data/` directory first
   - Use `--reset` flag to clear existing database

2. **Query your documents**:
```bash
python query_data.py "Your question here"
```

3. **Run tests** (optional):
```bash
python -m pytest test_rag.py
```

## Customization
- Change the LLM model in `query_data.py` (line 43)
- Adjust chunking parameters in `populate_database.py` (lines 36-41)
- Modify embedding model in `get_embedding_function.py`

## Project Structure
- `data/` - Store PDF documents here
- `chroma/` - Vector database storage (auto-created)
- `populate_database.py` - Ingests and processes PDFs
- `query_data.py` - Handles natural language queries
- `get_embedding_function.py` - Manages text embeddings
- `test_rag.py` - Test cases

## Notes
- The system currently uses ChromaDB for vector storage and Mistral via Ollama for generation
- All deprecation warnings are safe to ignore but should be addressed in future updates