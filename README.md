# 🧠 AI-Assisted Airline Customer Support System  
### Real-Time Complaint Detection & Auto-Response using Kafka, Spark, Flask, and Deep Learning  

---

## 🚀 Overview  

This project presents an **AI-driven real-time airline customer support system** that automatically detects, classifies, and responds to customer complaints on **Twitter**.  
It combines **Big Data streaming (Kafka + Spark)**, **Deep Learning (LSTM)**, and **NLP techniques** to build an end-to-end **intelligent auto-reply pipeline**.

The system listens to live tweets, processes them in real time, classifies sentiment and complaint type, and replies automatically via a REST API — simulating a **real-time AI support agent**.

<p align="center">
  <br><em>Figure 1: Web Interface of AI-Assisted Customer Support</em>
</p>
<img width="2047" height="651" alt="image" src="https://github.com/user-attachments/assets/c31781f3-cfbf-4a75-967a-d27e80f703c1" />


---

## 🧭 Table of Contents

- [Overview](#-overview)
- [Architecture](#-architecture)
- [Methodology](#-methodology)
- [Results](#-results)
- [Tech Stack](#-tech-stack)
- [Setup Instructions](#-setup-instructions)
- [Sample Outputs](#-sample-outputs)
- [Folder Structure](#-folder-structure)
- [Research Contribution](#-research-contribution)
- [Future Scope](#-future-scope)
- [Author](#-author)
- [Acknowledgments](#-acknowledgments)

---

## 🏗️ Architecture  

<p align="center">
  <br><em>Figure 2: Overall System Architecture – Kafka + Spark + LSTM + Flask</em>
</p>
<img width="1202" height="714" alt="image" src="https://github.com/user-attachments/assets/65ae5322-0647-4b4b-bdd4-035302105953" />



### 🔹 Architecture Description

1. **Data Source**  
   - Tweets are collected from **Kaggle Airline Sentiment Dataset** and **Twitter Live Stream** using Tweepy.  
   - Data is published to Kafka topics (`tweet-data`).  

2. **Streaming Pipeline**  
   - **Apache Spark Structured Streaming** consumes Kafka data for real-time analysis.  
   - Text preprocessing: contraction expansion, stopword removal, lemmatization.  

3. **Model Inference**  
   - **Sentiment Classifier (LSTM)** — detects sentiment polarity.  
   - **Complaint Classifier (LSTM + LDA)** — identifies the complaint category (e.g., seating, service, baggage).  
   - **Entity Recognition (NER)** — extracts airline and location references.  

4. **Response Engine (Flask API)**  
   - Flask handles REST requests and sends automatic replies via **Tweepy** API.  

5. **Storage & Traceability**  
   - Classified tweets and replies are stored in **Amazon S3 (Parquet)** for analytics and audits.  

---

## 🧠 Methodology  

<p align="center">
  <br><em>Figure 3: Methodology Flow – From Preprocessing to Auto-Response</em>
</p>
<img width="1490" height="1256" alt="image" src="https://github.com/user-attachments/assets/03caa9ab-3a21-4221-9f33-44f16e8ec1e5" />


### 🔹 Step-by-Step Flow

1. **Data Preprocessing**
   - Expanded contractions & abbreviations  
   - Removed URLs, hashtags, and digits  
   - Lemmatized text for uniform representation  

2. **Embedding Generation**
   - Dense word vector representations using **Keras Tokenizer**  

3. **Modeling**
   - **Sentiment Classifier:** Embedding → LSTM (128 units) → Dense(2)  
   - **Complaint Classifier:** Embedding → LSTM (100 units) → Dense(8)  

4. **Response Generation**
   - Flask API composes contextual replies  
   - Each response tagged with a **unique Ticket ID**  

5. **Storage & Traceability**
   - Stored in S3 for reporting & downstream analytics  

---

## ⚙️ AWS Streaming Lifecycle  

Apache Kafka → Spark Structured Streaming → LSTM Classification
↓ ↓
Flask API ↔ Tweepy → Auto Tweet Reply → Amazon S3 Storage

---

## 📊 Results  

### 🔸 Model Performance

| Metric | Sentiment Model | Complaint Classifier |
|:-------|:----------------:|:--------------------:|
| **Accuracy** | 85.2% | 80.5% |
| **Macro F1 Score** | 0.846 | 0.792 |
| **Latency** | 2.8 – 3.1 sec/tweet | ✅ Real-Time |
| **Throughput** | ~1000 tweets/min | ✅ Scalable |


## 🧩 Tech Stack  

| Layer | Tools / Frameworks |
|:------|:-------------------|
| **Programming** | Python (PySpark, Flask) |
| **Data Stream** | Apache Kafka, Spark Streaming |
| **ML / DL** | TensorFlow, Keras (LSTM) |
| **NLP** | NLTK, Text Embedding |
| **Storage** | Amazon S3 (Parquet) |
| **Deployment** | AWS EC2, Flask API |
| **Version Control** | Git, GitHub |

---
