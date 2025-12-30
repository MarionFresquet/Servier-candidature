# 📚 Retrieval-Augmented Generation (RAG) — Technical Project

This repository contains a **Retrieval-Augmented Generation (RAG)** pipeline developed as part of a technical test for an apprenticeship position.  
The goal of the project is to enable a **Large Language Model (LLM) to answer questions using external documents** stored and indexed locally.

The pipeline is built using:

- **llama-index** for document ingestion and vector retrieval  
- **HuggingFace embeddings** for text encoding  
- **A GPTQ-compressed Mistral 7B model with PEFT fine-tuning** for text generation  

The main script is:

*final_rag.py*

---

## 🚀 How It Works

1. Documents are placed in the `articles/` folder  
2. They are split into chunks and converted to embeddings  
3. A vector index is created  
4. When a user asks a question:
   - the most relevant chunks are retrieved
   - they are injected as context into the LLM
5. The model generates an answer grounded in the retrieved content  

---

## 📂 Project Structure
.
├── final_rag.py # Main script
├── articles/ # Folder for source documents
└── README.md


> Add your PDF / TXT / article files inside the `articles/` folder.

---

## 🛠️ Requirements

Python **3.9+** recommended.

### Install dependencies

```bash
pip install llama-index llama-index-embeddings-huggingface peft auto-gptq optimum bitsandbytes transformers accelerate

##💡 The script uses a GPTQ-optimized model, so it can run on CPU.

##▶️ Running the Project

Add your documents to the articles/ directory
Run the script:

python final_rag.py
