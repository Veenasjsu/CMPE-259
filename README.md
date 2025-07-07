# CMPE-259

# 🧠 Virtual Assistant for Learning Python

This project is a **domain-specific Question Answering (QA) system** that helps users learn Python by providing accurate and context-aware answers to their questions. It uses a Retrieval-Augmented Generation (RAG) approach, combining document retrievers, transformer-based embeddings, and powerful answer generation models like T5 and BERT.

---

## 📌 Features

- ✅ Retrieves relevant content from Python documentation and tutorials
- ✅ Embeds documents using HuggingFace’s `all-MiniLM-L6-v2`
- ✅ Retrieves context using FAISS index
- ✅ Answers questions using models like:
  - `T5-large`
  - `bert-large-uncased`
  - `roberta-base-squad2-distilled`
- ✅ Evaluates answer quality using cosine similarity
- ✅ Tracks response time and completeness

---

## 🧱 System Architecture

### 1. Data Preparation
- Source: Python official documentation/tutorials
- Preprocessing: Text extracted from PDFs → structured text
- Input: QA pairs (questions + ground truth answers)

### 2. Embedding
- Model: `all-MiniLM-L6-v2`
- Converts documents into vectors for indexing

### 3. Retriever
- Indexing: FAISS vector store
- Retrieval: Top 5 matching documents for each question
- Context limit: 200 tokens

### 4. Answer Generation
- Models: `T5-large`, `bert-large-uncased`, `roberta-base-squad2-distilled`
- Inference techniques: Beam search + length penalties

### 5. Evaluation
- Metric: Cosine similarity between generated and ground truth answers
- Threshold for correctness: Similarity > 0.4
- Additional metrics: Response time, completeness

---

## 📊 Evaluation Results

| Metric              | T5-large | BERT-large | RoBERTa-distilled |
|---------------------|----------|------------|-------------------|
| Accuracy (%)        | 86.67    | 33.33      | 20.00             |
| Avg. Response Time  | 44 sec   | 0.32 sec   | 1.29 sec          |
| Response Completeness | High  | Low        | Low               |

---

## 🖼️ Sample Output

**Q:** What is a dictionary in Python and how is it defined?  
**A (T5-large):**  
```python
a dictionary in Python is an unordered collection of key-value pairs...
