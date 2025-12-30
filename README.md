# 🔍 Local RAG Pipeline with LLM Integration

This repository contains an implementation of a **RAG (Retrieval-Augmented Generation)** pipeline developed as part of a technical test for an apprenticeship position.  
The goal is to enable a **Large Language Model (LLM)** to answer questions based on external documents, stored and indexed locally.

---

### ⚙️ Technologies used

- `llama-index`: for document ingestion and vector search
- `HuggingFace`: for text embeddings
- `Mistral 7B` compressed with `GPTQ` + `PEFT` fine-tuning for text generation

---

### 🧪 How the pipeline works

1. Documents are placed in the `articles/` folder  
2. They are split into chunks and encoded into vectors (embeddings)  
3. A vector index is created  
4. When a question is asked:  
   - the most relevant chunks are retrieved  
   - they are injected as context into the LLM  
   - the model generates an answer based on these documents  

---

### 📁 Project structure

```bash
.
├── final_rag.py       # Principal Script 
├── articles/          # Folder containing the source documents  
└── README.md          # Documentation file
```

### 📦 Prerequisites  
Python 3.9 or higher recommended

Dependency installation:

```bash

pip install llama-index llama-index-embeddings-huggingface peft auto-gptq optimum bitsandbytes transformers accelerate
```

### 💡 The script uses a compressed model (GPTQ), so it can run on CPU.

### ▶️ Running the script  
Add your documents to the `articles/` folder

Run the script with the following command:

```bash
python final_rag.py
```

What the script does:

- Indexes the documents  
- Retrieves the most relevant passages  
- Builds a context-aware prompt  
- Generates a response using the LLM  
- Displays both the context used and the generated response

### ❓ Default query example  
The default question used in the script is:

```bash
What are the two main challenges that hinder the widespread application of the 'LLM-as-a-Judge' approach?

```
The pipeline:

- Retrieves the 3 most relevant chunks (`top_k = 3`)  
- Applies a similarity threshold of 0.5  
- Builds a prompt with the selected context  
- Generates a response using the Mistral model + PEFT

### 🧠 Models used  
Embedding model: `BAAI/bge-small-en-v1.5`  
LLM (GPTQ compressed): `TheBloke/Mistral-7B-Instruct-v0.2-GPTQ`  
PEFT fine-tuning adapter: `shawhin/shawgpt-ft`

### ⚠️ Important notes

Documents must be added manually to the `articles/` folder.

The LLM is used in evaluation mode only. This project is intended for local and experimental use. The prompt guides the model toward scientifically accurate and clear responses.

### 🎯 Learning objectives  
This project demonstrates how to:

- Build a local RAG pipeline  
- Use vector search with Llama-Index  
- Inject context into an LLM prompt  
- Use a compressed and fine-tuned model for efficient responses

### 👤 Author  
Marion Fresquet
