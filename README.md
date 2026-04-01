# LangGraph PDF RAG Chatbot

A **Streamlit** application that answers user questions using a **LangGraph** workflow: questions are routed either to a **retrieval-augmented** path over embedded PDFs or to a **direct LLM** path when general knowledge suffices. Document chunks use an ensemble retriever; retrieval quality and answers are graded with LLM-based checks.

## Features

- PDF ingestion from a local `./docs` folder (embeddings + chunking)
- LangGraph state machine: route → retrieve → grade documents → generate or rewrite query
- Streamlit UI for interactive Q&A
- OpenAI-compatible models via LangChain (`langchain_openai`)

## Prerequisites

- Python 3.10+ recommended  
- An OpenAI API key (or compatible endpoint) and `LLM_MODEL` set in the environment  
- PDFs placed under `./docs`

## Setup

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Create a `.env` file with at least:

```
OPENAI_API_KEY=sk-...
LLM_MODEL=gpt-4o-mini
```

Adjust variable names if your fork uses different conventions (see `src/llm_srz.py`).

## Run

```bash
streamlit run main.py
```

## Layout

| Path | Purpose |
|------|---------|
| `main.py` | Streamlit app and document initialization |
| `src/graph.py` | LangGraph workflow definition |
| `src/nodes.py` | Node implementations (retrieve, grade, generate, …) |
| `src/utils.py` | PDF loading, splitting, embeddings, retriever setup |
| `src/llm_srz.py` | Prompted chains and graders |

## License

See the repository license file if present.
