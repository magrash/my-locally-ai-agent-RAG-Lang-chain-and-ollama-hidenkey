# Local AI Agent RAG with LangChain and Ollama

![Project Screenshot](Screenshot%202025-05-10%20061128.png)

This project implements a Retrieval-Augmented Generation (RAG) AI agent focused on answering questions about a pizza restaurant. The agent functions completely locally without the need for external API keys (no more hidden keys!), ensuring data privacy and offline capability.

## Features

- **Local Inference**: Uses [Ollama](https://ollama.ai/) to run LLMs (`llama3.2` for generation and `mxbai-embed-large` for embeddings) locally.
- **RAG Pipeline**: Leverages [LangChain](https://langchain.com/) to connect the LLM with a local vector database.
- **Vector Database**: Uses ChromaDB to store and retrieve embedded restaurant reviews from a CSV file.
- **Interactive Chat**: A simple CLI interface to ask questions about the restaurant's reviews.

## Prerequisites

- Python 3.8+
- [Ollama](https://ollama.ai/) installed and running locally.
- You must pull the necessary models within Ollama before running:
  ```bash
  ollama pull llama3.2
  ollama pull mxbai-embed-large
  ```

## Installation

1. Clone this repository (or copy the files).
2. Install the required Python packages:

```bash
pip install -r requirements.txt
```

## Usage

Run the main script to start the interactive chat:

```bash
python main.py
```

On the first run, the script will parse `realistic_restaurant_reviews.csv`, generate embeddings, and build the local Chroma vector database in a `./chrome_langchain_db` directory. Subsequent runs will use the existing database to quickly retrieve context.

## Files Structure

- `main.py`: The entry point for the interactive CLI chat agent. Constructs the LLM chain and handles the continuous prompt loop.
- `vector.py`: Handles reading the CSV dataset, generating embeddings, and storing them in a local Chroma vector database. It also provides the `retriever` used by the main script.
- `realistic_restaurant_reviews.csv`: The dataset containing synthetic reviews and ratings for the pizza restaurant.
- `requirements.txt`: Python package dependencies.
