# Pinecone Document Ingestion

An n8n workflow that allows users to upload documents through a form and automatically store their content as vector embeddings in a Pinecone vector database.

## Workflow

```text
File Upload Form
       ↓
Document Loader
       ↓
OpenAI Embeddings
       ↓
Pinecone Vector Store
```

## Features

* Upload documents through an n8n form
* Extract document content using the Default Data Loader
* Generate vector embeddings using OpenAI
* Store embeddings in Pinecone
* Prepare documents for semantic search and RAG applications

## Tech Stack

* n8n
* OpenAI Embeddings
* Pinecone
* Vector Database
* Document Loader

## Use Case

This workflow can be used as the **document ingestion pipeline** for RAG-based AI applications, allowing uploaded knowledge-base documents to be converted into searchable vector data.

## Setup

1. Import the workflow JSON into n8n.
2. Configure your **OpenAI** credentials.
3. Configure your **Pinecone** credentials.
4. Select your Pinecone index.
5. Execute the form and upload a document.

## Workflow File

`pinecone-document-ingestion.json`

> **Note:** Credentials are not included in this repository. Configure your own credentials in n8n before running the workflow.
