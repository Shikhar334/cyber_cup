# AI-Powered Phishing URL Detection System

## 🌟 Project Goal

Our project aims to design and implement a robust, AI-powered system that can accurately detect whether a given mail is containing a phishing threat or a legitimate link. The system goes beyond traditional keyword filtering by analyzing a combination of lexical, host-based, and advanced textual features.

## ✨ Key Features

* *Hybrid AI Model:* Our system uses a powerful stacking ensemble of Machine Learning (LightGBM, XGBoost) and Deep Learning (Character-level CNN) models for enhanced accuracy and robustness.
* *Comprehensive Feature Engineering:* We analyze URLs using three distinct feature sets:
    * *Lexical Features:* URL length, number of dots, presence of suspicious words like 'login' and 'secure'.
    * *Host-Based Features:* Domain age, HTTPS status, and IP-based URLs.
    * *TF-IDF Features:* Character-level and token-level TF-IDF to detect obfuscation and common phishing patterns.
* *Advanced Cross-Validation:* We use *5-Fold Stratified Out-of-Fold (OOF) validation* to prevent overfitting and ensure our model's performance is reliable on unseen data.
* *Explainable Alerts:* The system is designed to not only classify a URL but also provide insights into why it was flagged, fostering user trust.
* *Self-Learning Mechanism:* An integrated feedback loop allows the model to continuously learn and improve from user corrections, reducing false positives and adapting to new threats.

## 🚀 Main Steps in the Pipeline

1.  *Data Preparation:* Clean, label, and tokenize URLs. Our dataset includes labeled phishing URLs from *PhishTank* and legitimate emails from *Enron* and *SpamAssassin*.
2.  *Feature Engineering:* Extract and generate lexical, host-based, and TF-IDF features from the processed URLs.
3.  *Modeling:* Train our stacking ensemble model, which combines the strengths of various base learners.
4.  *Cross-Validation:* Evaluate the model using the robust 5-Fold Stratified OOF method to ensure generalization.
5.  *Evaluation:* Compute and visualize key metrics like Accuracy, Precision, Recall, F1-score, and ROC-AUC.

## 🔧 Technologies and Libraries Used

* *Machine Learning:*
    * LightGBM / XGBoost: High-performance Gradient Boosting frameworks.
    * Scikit-learn: For data preprocessing, model selection, and evaluation.
* *Deep Learning:*
    * Keras (with TensorFlow backend): To build the Character-level CNN for raw URL analysis.
* *Data & Utilities:*
    * Pandas / NumPy: For data manipulation and numerical operations.
    * TF-IDF Vectorizer: For transforming text into numerical features.
* *Deployment (Future Scope):*
    * Browser Extension API for real-time alerts.

## 📈 Model Performance (Expected)

Our model is expected to achieve high performance across all key metrics. The stacking ensemble and robust cross-validation are designed to achieve high precision in detecting phishing threats while maintaining a low false positive rate.

## ➡ Future Enhancements

* *Dynamic URL Handling:* Integrate with live URL scanning APIs to handle shortened or redirected URLs.
* *Real-time Alerts:* Develop a browser extension or email client plugin for real-time phishing alerts.
* *Multilingual Support:* Expand the model to detect phishing in Indian languages.
* *Explainability:* Implement SHAP or LIME for detailed feature importance visualization.

