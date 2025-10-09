# 📧 AI-Powered Phishing Email Detection System

### Team WARLOCKS — [Yash | Shivansh | Prithvi | Shikhar]  
**Institution:** Amity School of Engineering and Technology (ASET)

---

## 🌐 Overview

The **AI-Powered Phishing Email Detection System** is an advanced cybersecurity project designed to **detect and classify phishing emails** with high accuracy using **machine learning (ML)** and **deep learning (DL)** techniques.  
Unlike traditional filters that rely on keyword matching or static rules, our model intelligently analyzes the **email’s content, metadata, embedded URLs, and attachments** using **Natural Language Processing (NLP)** and **AI-driven ensemble models**.

This system represents the next generation of **phishing detection**, capable of adapting to evolving threats such as **image-based phishing**, **URL obfuscation**, and **AI-generated emails**.

---

## 🎯 Project Objectives

- Detect whether an email is **phishing or legitimate** using AI.
- Analyze **text, metadata, and URLs** within emails to identify hidden threats.
- Ensure **explainability** and **trust** through interpretable model outputs.
- Support **continuous learning** from user feedback to reduce false positives.

---

## ⚙️ System Architecture

### 🧩 1. Data Preparation
- **Datasets Used:**  
  - **PhishTank:** Verified phishing email URLs and domains.  
  - **Enron** & **SpamAssassin:** Legitimate email datasets for ham class.  
- **Processing Steps:**  
  - Cleaning and deduplication of email data.  
  - Extraction of email body, subject line, sender domain, and embedded URLs.  
  - Labeling as *phishing* or *legitimate (ham)*.

### 🧩 2. Feature Engineering
Our system leverages a **three-layer feature extraction pipeline**:
- **Lexical Features:**  
  URL length, number of dots, presence of suspicious keywords (`login`, `secure`, `verify`).
- **Host-Based Features:**  
  Domain age, HTTPS presence, DNS response time, and IP-based URLs.
- **Content-Based (TF-IDF) Features:**  
  Character-level and token-level TF-IDF representations of email text for semantic pattern detection.

### 🧩 3. Modeling
A **hybrid ensemble architecture** combining classical ML and deep learning:

| Layer | Model | Role |
|-------|--------|------|
| Base | **LightGBM / XGBoost** | Extracts structured phishing indicators |
| Base | **Character-level CNN** | Learns obfuscated text & URL patterns |
| Meta | **Logistic Regression** | Stacking ensemble for final prediction |

### 🧩 4. Cross-Validation
Implements **5-Fold Stratified Out-of-Fold (OOF) validation** to:
- Maintain balanced class distribution  
- Prevent overfitting  
- Improve generalization on unseen data

### 🧩 5. Evaluation Metrics
| Metric | Purpose |
|---------|----------|
| **Accuracy** | Overall correctness |
| **Precision** | Ratio of true phishing among detected ones |
| **Recall** | Detection rate for phishing emails |
| **F1-Score** | Balance of precision and recall |
| **ROC-AUC** | Measures classifier quality |

---

## 💡 Key Highlights

✅ **Hybrid AI Model** — Combines traditional ML and Deep Learning for superior detection.  
✅ **Explainable AI (XAI)** — Provides interpretable alerts and reasoning for flagged emails.  
✅ **Continuous Learning Loop** — Feedback-based retraining improves accuracy over time.  
✅ **Cross-Validated Pipeline** — Robust against overfitting using OOF validation.  
✅ **Real-World Adaptability** — Handles both textual and image-based phishing attacks.

---

## 🧠 Techniques & Libraries Used

| Category | Tools / Libraries |
|-----------|-------------------|
| **Data Processing** | `Pandas`, `NumPy`, `Regex`, `BeautifulSoup` |
| **Feature Engineering** | `TF-IDF Vectorizer`, `Fuzzy Matching`, `whois` |
| **Machine Learning** | `LightGBM`, `XGBoost`, `Scikit-learn` |
| **Deep Learning** | `Keras` (TensorFlow backend) for Char-level CNN |
| **Explainability** | `SHAP`, `LIME` (for interpretability) |
| **Visualization** | `Matplotlib`, `Seaborn` |
| **Deployment (Future Scope)** | `Flask`, `FastAPI`, Browser Extension API |

---

## 📈 Expected Model Performance

| Metric | Target |
|---------|---------|
| Accuracy | ≥ 95% |
| Precision | ≥ 94% |
| Recall | ≥ 93% |
| F1-Score | ≥ 94% |
| ROC-AUC | ≥ 0.97 |

The stacking ensemble and advanced cross-validation ensure both **high accuracy** and **low false-positive rate**.

---

## 🔄 Feedback & Self-Learning Mechanism

Our system integrates a **feedback loop** for continual improvement:
- **User Feedback:** Users can manually mark flagged emails as *Not Phishing* or *Phishing*.
- **Retraining Process:** The system incorporates this feedback during periodic retraining.
- **Dashboard Integration:** Real-time visualization of false positives, precision trends, and retraining cycles.

This **human-in-the-loop** approach ensures the system adapts dynamically to emerging threats.

---

## 🧭 Future Enhancements

🚀 **Dynamic URL Analysis:** Integration with live APIs (Google Safe Browsing, VirusTotal).  
🌍 **Multilingual Support:** Extend detection to phishing content in Indian regional languages.  
🧩 **Browser & Email Client Plugins:** For real-time detection in Gmail or Outlook.  
📊 **Explainability Dashboard:** Visualize SHAP values and feature importances for transparency.  
🔐 **Cloud Deployment:** Scalable backend with REST API for enterprise integration.

---
## 🛡️ Summary

This project presents a **comprehensive AI-powered phishing email detection framework** combining **lexical**, **host-based**, and **semantic (NLP)** analysis.  
By merging **LightGBM**, **XGBoost**, and **Character-level CNN** in a **stacked ensemble**, it achieves **state-of-the-art performance** in phishing detection while maintaining transparency through **explainable AI**.  

The model is adaptive, interpretable, and scalable — paving the way for **real-time, self-learning cybersecurity systems**.

---
