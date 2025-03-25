# nyc_admin_llm
## Overview

The NYC-Law Language Model (NYCLLM) is a domain-specific retrieval-augmented generation (RAG) model designed to help users understand and interpret the New York City Administrative Code (Titles 8, 9, and 10 —more titles in future releases). The model is optimized to answer questions based on NYC legal regulations, providing legally accurate and context-specific responses for non-legal experts.

This project is aimed at creating a powerful tool to make legal information more accessible and understandable by leveraging large language models (LLMs) and legal text embeddings.

## Features
Dataset: Includes a .txt (Titles 1, 2, 8, 9, 10, 20), .csv (Titles 8, 9, 10), and .jsonl (Titles 8, 9, and 10) of the administrative code with metadata and QA-pairs.

Retrieval-Augmented Generation: Uses a retrieval process to fetch the most relevant legal text from the dataset and then generates context-aware answers based on that text.

Use of BART: The model uses BART for generating embeddings, providing a high-quality representation of the legal text.

Claude for Response Generation: Uses Claude, an advanced AI model, to generate clear, non-legal jargon responses based on the context from the retrieved documents.

**Disclaimer Important: This model is intended for informational purposes only and should not be used for official legal defense, professional legal advice, or any legal decision-making. The model’s responses are based on publicly available legal text and machine learning techniques, and although it strives to provide accurate information, it does not guarantee correctness or comprehensiveness. Users should consult a qualified legal professional for legal advice or official matters.**

## Installation

`git clone https://github.com/your-username/nyc-llm.git`
`cd nyc-llm`

## Configuration
You will need a **Hugging Face** or **Anthropic API Key** for using the tool (* *note: included are two generation options, one with facebook/bart-large and the other with claude-3-7-sonnet-20250219* *)

## How It Works
Legal Text Embedding: The NYC legal text (including the NYC Administrative Code) is split into smaller chunks, and BART is used to create embeddings for each chunk. These embeddings are stored in a database (ChromaDB).
**Document Retrieval:** When a user asks a question, the query is transformed into an embedding. The model then retrieves the most relevant documents from ChromaDB using cosine similarity.
**Answer Generation:** Once the relevant documents are retrieved, they are fed into Claude, which generates an accurate, legal-text-based response tailored to the user's question.


## Usage
```
#To query the system, call the `generate_answer` function:
query = "What are the restrictions on carrying guns in NYC?"
answer = generate_answer(query)
print("Answer:", answer)
```

```
nyc-llm/
│
├── data/                    # Contains the NYC legal text
│
├── notebooks/               # Jupyter notebooks with the RAG script
│
├── chromadb/                # ChromaDB storage for legal text embeddings
│
├── requirements.txt         # Required Python libraries
│
└── README.md                # Project documentation
```

License
This project is licensed under the MIT License.
