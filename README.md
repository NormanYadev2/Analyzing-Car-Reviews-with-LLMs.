# 🚗 Analyzing Car Reviews with LLMs

Welcome to the repository for **Car-ing is Sharing**, a forward-thinking car sales and rental company enhancing customer support using **Large Language Models (LLMs)**. This repository contains a demonstration of LLM-powered NLP tasks on real customer reviews.

---

## 📌 Project Objective

As part of modernizing customer engagement, the team was tasked to:
- Build a **multi-functional chatbot prototype** using various Hugging Face LLM pipelines.
- Support tasks like sentiment classification, translation, summarization, and both extractive and generative question answering.
- Evaluate model outputs using standard NLP metrics like **Accuracy**, **F1**, **BLEU**, and **ROUGE**.

---

## 🧠 Implemented Tasks and Results

### 1. ✅ Sentiment Analysis

- **Model**: `distilbert-base-uncased-finetuned-sst-2-english`
- **Pipeline**: Hugging Face `pipeline("sentiment-analysis")`
- **Method**:
  - Reviews passed with `truncation=True` to handle token length (DistilBERT's limit = 512).
  - Classification done in batches.

---

### 2. 🌍 English to Spanish Translation

- **Model**: `Helsinki-NLP/opus-mt-en-es`
- **Pipeline**: `pipeline("translation_en_to_es")`
- **Method**:
  - First 10 reviews extracted.
  - Translations compared to `reference_translations.txt` using **BLEU**.

---

### 3. ❓ Generative Question Answering

- **Model**: `t5-base` or `facebook/bart-large`
- **Pipeline**: `pipeline("text2text-generation")`
- **Method**:
  - Used first review and asked a relevant question.
  - Compared generated answer to human reference using BLEU and ROUGE.

---

### 4. 📌 Extractive Question Answering

- **Model**: `deepset/minilm-uncased-squad2`
- **Pipeline**: `pipeline("question-answering")`
- **Method**:
  - Extracted question from 1st review.
  - Compared model’s exact span output with the reference.

---

### 5. 📝 Summarization

- **Model**: `facebook/bart-large-cnn`
- **Pipeline**: `pipeline("summarization")`
- **Method**:
  - Last review summarized (~50–55 tokens).
  - Compared to human-written summary using BLEU and ROUGE.
-

---

## 📁 Results


| Task                     | Metric(s)         | Result(s)                                      |
|--------------------------|-------------------|------------------------------------------------|
| **Sentiment Analysis**   | Accuracy           | **0.8711**                                     |
|                          | F1 Score           | **0.8573**                                     |
| **Translation (EN→ES)**  | BLEU Score         | **0.8647**                                     |
| **Generative QA**        | BLEU Score         | **0.6305**                                     |
|                          | ROUGE1             | **0.772**                                      |
|                          | ROUGE2             | **0.768**                                      |
|                          | ROUGE-L / Lsum     | **0.772**                                      |
| **Extractive QA**        | Exact Match        | **0.0**                                        |
|                          | F1 Score           | **0.0**                                        |
| **Summarization**        | BLEU Score         | **0.7413**                                     |
|                          | ROUGE1             | **0.861**                                      |
|                          | ROUGE2             | **0.857**                                      |
|                          | ROUGE-L / Lsum     | **0.861**                                      |

