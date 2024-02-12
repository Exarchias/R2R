# SciPhi r2r

SciPhi r2r (RAG to Riches) is a Python framework designed for the rapid construction and deployment of AI retrieval systems. This semi-opinionated framework accelerates the process of transitioning from experimental stages to production-grade Retrieval-Augmented Generation (RAG) systems.

## Installation

The project uses Poetry for dependency management. To install the project, you need to have Poetry installed on your system. If you don't have it, you can install it by following the instructions on the [official Poetry website](https://python-poetry.org/docs/#installation).

Once you have Poetry installed, you can install the project dependencies by running:

```bash
poetry install
```

This will create a virtual environment and install all the necessary dependencies.

## Core Abstractions

The framework primarily revolves around three core abstractions:

- The **Embedding Pipeline**: Utilizes a `DatasetProvider` for input data, an `EmbeddingProvider` for generating embeddings, and a `VectorDBProvider` for storing these embeddings. The implementation can be found in [`embedding.py`](sciphi_r2r/core/pipelines/embedding.py).

- The **RAG Pipeline**: Combines a `EmbeddingProvider`, `VectorDBProvider`, and a `LLMProvider` to process input queries or context and generate outputs based on retrieved context. The implementation can be found in [`rag.py`](sciphi_r2r/core/pipelines/rag.py).

Each pipeline incorporates a logging database for operation tracking.
## Running the Examples

The project includes three basic examples that demonstrate the usage of the embedding and completion pipelines:

1. [`rag_pipeline.py`](sciphi_r2r/examples/basic/rag_pipeline.py): This example demonstrates the usage of the completion pipeline. It takes a query as input and returns a completion generated by the OpenAI API.

    To run this example, use the following command:

    ```bash
    poetry run python -m sciphi_r2r.examples.basic.rag_pipeline
    ```

2. [`embedding_pipeline.py`](sciphi_r2r/examples/basic/embedding_pipeline.py): This example demonstrates the usage of the embedding pipeline. It loads datasets from HuggingFace, generates embeddings for the data using the OpenAI API, and stores the embeddings in a PostgreSQL vector database.

    To run this example, use the following command:

    ```bash
    poetry run python -m sciphi_r2r.examples.basic.embedding_pipeline
    ```

3. [`app.py`](sciphi_r2r/examples/basic/app.py): This is the main application that sets up both the embedding and completion pipelines and starts a Uvicorn server.

    To run this example, use the following command:

    ```bash
    poetry run python -m sciphi_r2r.examples.basic.app
    ```
