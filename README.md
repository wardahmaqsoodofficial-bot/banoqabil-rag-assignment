# Bano Qabil RAG Assistant — Assignment 02

## Project Overview

This project is a Retrieval-Augmented Generation (RAG) assistant created for Bano Qabil Assignment 02.

The assistant uses Bano Qabil website content as its knowledge base. It retrieves relevant information from the knowledge base and generates answers to users' questions.

## Technologies Used

- Python
- Retrieval-Augmented Generation (RAG)
- Google Gemini Embedding Model
- Pinecone Vector Database
- Groq API for LLM responses

## How It Works

1. Bano Qabil website content is stored in a JSON knowledge base.
2. The knowledge base is divided into smaller text chunks.
3. An embedding model converts the text chunks into vectors.
4. The vectors are stored in a Pinecone index.
5. When a user asks a question, the application retrieves relevant information from Pinecone.
6. The retrieved information is used to generate an answer.

## Main Project Files

| File | Description |
|---|---|
| `banoqabil_kb.json` | Bano Qabil knowledge base |
| `banoqabil_rag.py` | Main RAG application |
| `hallucination_test.md` | Hallucination testing report |
| `screenshots/` | Screenshots of chatbot testing |
| `requirements.txt` | Python dependencies |
| `.env.example` | Example environment variables |

## Hallucination Testing

The assistant was tested with questions related to Bano Qabil and questions outside its knowledge base.

The testing report documents the questions, responses, and observations. During testing, the assistant sometimes responded with "I don't know" when it could not provide a reliable answer.

The report distinguishes between confirmed hallucinations and answers that require further verification.

## Setup Instructions

1. Clone this repository.
2. Create and activate a Python virtual environment.
3. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file using `.env.example`.
5. Add your API keys to the `.env` file.
6. Run the application:

   ```bash
   python banoqabil_rag.py
   ```

## Assignment Submission

This repository contains the code, knowledge base, hallucination testing report, and screenshots for Bano Qabil Assignment 02.