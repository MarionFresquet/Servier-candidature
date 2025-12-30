Retrieval-Augmented Generation (RAG) — Technical Project

This repository contains a Retrieval-Augmented Generation (RAG) pipeline developed as part of a technical test for an apprenticeship position.
The goal of the project is to enable a Large Language Model (LLM) to answer questions using external documents stored and indexed locally.

The pipeline is built using:

llama-index for document ingestion and vector retrieval

HuggingFace embeddings for text encoding

A GPTQ-compressed Mistral 7B model with PEFT fine-tuning for text generation

The main script is:

final_rag.py

🚀 How It Works

Documents are placed in the articles/ folder

They are split into chunks and converted to embeddings

A vector index is created

When a user asks a question:

the most relevant chunks are retrieved

they are injected as context to the LLM

The model generates an answer grounded in the retrieved content

📂 Project Structure
.
├── final_rag.py          # Main script
├── articles/             # Folder for source documents
└── README.md


Add your PDF / TXT / article files inside the articles/ folder.

🛠️ Requirements

Python 3.9+ recommended.

Install dependencies
pip install llama-index llama-index-embeddings-huggingface peft auto-gptq optimum bitsandbytes transformers accelerate


💡 The script uses a GPTQ-optimized model, so it can run on CPU.

▶️ Running the Project

1️⃣ Add your documents to:

articles/


2️⃣ Run the script:

python final_rag.py


3️⃣ The script will:

✔ index the documents
✔ retrieve the most relevant passages
✔ build a prompt
✔ generate an answer using the LLM
✔ print both the context and the response

🔍 Default Query Example

The default query is:

"What are the two main challenges that hinder the widespread application of the 'LLM-as-a-Judge' approach?"


The pipeline:

retrieves the top 3 most relevant chunks (top_k = 3)

filters results below a similarity threshold (cutoff = 0.5)

builds a context prompt

generates an answer using the Mistral model with PEFT fine-tuning

🤖 Models Used
Embeddings
BAAI/bge-small-en-v1.5

Base Language Model
TheBloke/Mistral-7B-Instruct-v0.2-GPTQ

Fine-Tuning (PEFT Adapter)
shawhin/shawgpt-ft

⚠️ Important Notes

Documents must be added manually to the articles/ directory

The LLM runs in evaluation mode

This project is intended for local, experimental use

System instructions encourage clear scientific reasoning in responses

✨ Learning Objectives

This project demonstrates:

✔ how to build a local RAG pipeline
✔ vector search using Llama-Index
✔ context injection into an LLM
✔ use of compressed & fine-tuned models

👩‍💻 Author

Marion Fresquet

Developed as part of a technical test for an apprenticeship application.
