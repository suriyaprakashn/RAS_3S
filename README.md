# RAG_S3: Retrieval-Augmented Generation with AstraDB

RAG_S3 is a modular Python application enabling semantic search and intelligent Q&A over project documents by embedding content into AstraDB Vector Store and querying with LangChain and OpenAI models. The application uses Flask for a web interface and implements a hybrid retrieval pipeline for precise contextual answers.

---

## Features

- Semantic retrieval leveraging OpenAI text embeddings and AstraDB vector store.
- Document ingestion with rich DOCX text and hyperlink extraction.
- Hybrid retrieval combining BM25 and semantic search.
- Modular design for easy extension and maintenance.
- PEP8-compliant codebase and clean project structure.

---

## File Structure

RAG_S3/
├── .venv/ # Virtual environment
├── cli/ # Command-line interface scripts
│   └── main.py # Basic CLI entrypoint/demo
├── core/ # Core application logic modules
│   ├── init.py
│   ├── db.py # AstraDB client, collection, vector store setup
│   ├── embedding.py # Document chunking, embedding, and ingestion
│   ├── docx_reader.py # DOCX text, link, and metadata extraction
│   └── prompt.py # Prompt templates, RAG orchestration & retrieval
├── static/ # Static assets (images, css, videos)
│   ├── guvi.jpg
│   ├── style.css
│   └── vecteezy_robot.mp4
├── templates/ # Flask HTML templates
│   ├── basic.html
│   ├── home.html
│   └── query.html
├── utils/ # Utility functions
│   ├── init.py
│   ├── io_utils.py # File operations and helpers
│   └── markdown_utils.py # Markdown to HTML conversion
├── .env
├── app.py # Flask application entrypoint
├── config.py # Configuration and secrets
└── requirements.txt

---

## Modules Description

### config.py
Contains all environment variable loading and configuration constants such as API keys and endpoints for AstraDB and OpenAI.

---

### app.py
Flask web server routing:
- `/` Home page.
- `/query` Interactive chat-like project query interface supporting session-based chat history.

---

### core/db.py
Encapsulates AstraDB connection establishment, vector store initialization, and project list retrieval.

---

### core/embedding.py
Handles document chunking, embedding with OpenAI models, and insertion into AstraDB vector collections.

---

### core/docx_reader.py
Robust extraction of full text, hyperlinks, and table metadata from DOCX files. Converts documents into LangChain-compatible Document objects.

---

### core/prompt.py
Manages prompt templates for skills extraction and resource summarization, hybrid retrieval combining BM25 and vector search, and generation of final answers formatted in Markdown.

---

### cli/main.py
A simple command-line entrypoint for executing or testing core functions.

---

### utils/markdown_utils.py
Functions for converting Markdown content to HTML for web rendering.

---

## Setup Instructions

1. Clone the repository:
    ```
    git clone https://github.com/your-username/RAG_S3.git
    cd RAG_S3
    ```
2. Create and activate a virtual environment:
    ```
    python3 -m venv .venv
    source .venv/bin/activate
    ```
3. Install dependencies:
    ```
    pip install -r requirements.txt
    ```
4. Configure environment variables in `.env` or directly in `config.py`:
    - `OPENAI_API_KEY`
    - `OPENAI_API_BASE`
    - `ASTRA_DB_API_ENDPOINT`
    - `ASTRA_DB_APPLICATION_TOKEN`
5. Run the Flask app:
    ```
    python app.py
    ```
6. Access the web interface at `http://localhost:5000/`.

---

## Usage Overview

- Upload project documents via the UI or use the ingestion functions programmatically.
- Query project content with natural language questions; the system performs semantic retrieval and returns enriched answers.
- View and interact with chat history stored within the user session.

---

## Contribution Guidelines

Contributions are welcome! Please:

- Follow PEP8 coding style.
- Write clear, modular code.
- Include descriptive commit messages.
- Open pull requests against the `main` branch.

---

## License

This project is licensed under the MIT License.

---