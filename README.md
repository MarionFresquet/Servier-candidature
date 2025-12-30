# 🔍 Local RAG Pipeline with LLM Integration

Ce dépôt contient une implémentation d'un pipeline **RAG (Retrieval-Augmented Generation)** développé dans le cadre d'un test technique pour un poste en alternance.  
L'objectif est de permettre à un **Large Language Model (LLM)** de répondre à des questions en s'appuyant sur des documents externes, stockés et indexés localement.

---

### ⚙️ Technologies utilisées

- `llama-index` : pour l'ingestion des documents et la recherche vectorielle
- `HuggingFace` : pour les embeddings de texte
- `Mistral 7B` compressé avec `GPTQ` + fine-tuning `PEFT` pour la génération de texte

---

### 🧪 Fonctionnement du pipeline

1. Les documents sont placés dans le dossier `articles/`
2. Ils sont découpés en chunks et encodés en vecteurs (embeddings)
3. Un index vectoriel est créé
4. Lorsqu'une question est posée :
   - les chunks les plus pertinents sont récupérés
   - ils sont injectés comme contexte dans le LLM
   - le modèle génère une réponse basée sur ces documents

---

### 📁 Structure du projet

```bash
.
├── final_rag.py       # Script principal
├── articles/          # Dossier contenant les documents sources
└── README.md          # Fichier de documentation
```

### 📦 Prérequis
Python 3.9 ou supérieur recommandé

Installation des dépendances :

```bash

pip install llama-index llama-index-embeddings-huggingface peft auto-gptq optimum bitsandbytes transformers accelerate
```

### 💡 Le script utilise un modèle compressé (GPTQ), donc il peut fonctionner sur CPU.

### ▶️ Exécution du script
Ajoute tes documents dans le dossier articles/

Lance le script avec la commande suivante :

```bash
python final_rag.py
```

Ce que fait le script :

- Indexe les documents
- Récupère les passages les plus pertinents
- Construit un prompt contextuel
- Génère une réponse à l’aide du LLM
- Affiche à la fois le contexte utilisé et la réponse générée

### ❓ Exemple de requête par défaut
La question par défaut utilisée dans le script est :

```bash
What are the two main challenges that hinder the widespread application of the 'LLM-as-a-Judge' approach?

```
Le pipeline :

- Récupère les 3 chunks les plus pertinents (top_k = 3)
- Applique un seuil de similarité de 0.5
- Construit un prompt avec le contexte sélectionné
- Génère une réponse avec le modèle Mistral + PEFT

### 🧠 Modèles utilisés
Modèle d'embedding : BAAI/bge-small-en-v1.5

LLM (compressé GPTQ) : TheBloke/Mistral-7B-Instruct-v0.2-GPTQ

Adaptateur fine-tuning PEFT : shawhin/shawgpt-ft

### ⚠️ Notes importantes
Les documents doivent être ajoutés manuellement dans le dossier articles/

Le LLM est utilisé en mode évaluation uniquement. Ce projet est destiné à un usage local et expérimental. Le prompt guide le modèle vers des réponses scientifiquement exactes et claires.

### 🎯 Objectifs pédagogiques
Ce projet montre comment :

- Construire un pipeline RAG local
- Utiliser la recherche vectorielle avec Llama-Index
- Injecter du contexte dans un prompt LLM
- Exploiter un modèle compressé et fine-tuné pour des réponses efficaces

### 👤 Auteur
Marion Fresquet
