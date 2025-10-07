# cyber_cup

AI-Powered Phishing Email Detection System

This project is an end-to-end Artificial Intelligence (AI) and Machine Learning-based system that automatically detects phishing emails using Natural Language Processing (NLP) and metadata analysis. It is designed to identify and classify emails as phishing or legitimate (ham) by analyzing both their textual content and technical attributes.

The system also integrates explainability mechanisms (LIME and SHAP) so users can understand why an email was flagged, ensuring transparency and trust in the model’s decision-making.

1. Project Overview

Phishing attacks are one of the most widespread and damaging forms of cyber threats, often tricking users into revealing confidential information such as passwords or credit card details.

The objective of this project is to create an AI-powered detection system that can identify such malicious emails automatically.

The system performs:

Text Analysis: Using fine-tuned transformer models (DistilBERT or RoBERTa) to read and interpret email content.

Metadata Analysis: Using LightGBM to analyze technical email headers, links, SPF/DKIM results, and attachments.

Explainability: Using LIME and SHAP to visualize and explain predictions.

Deployment: FastAPI backend providing a /predict endpoint for real-time phishing classification.

2. System Architecture

Email Input – The user or IMAP client provides raw email data.

Email Parser & Feature Extractor – Extracts useful information from the email body, subject, and metadata.

Model Layer – Consists of three models:

Text Model (DistilBERT or RoBERTa)

Metadata Model (LightGBM)

Fusion Model (Combines outputs of both)

Explainability Layer – Uses LIME (for text) and SHAP (for metadata).

API Backend – FastAPI endpoint /predict returns label, score, and explanation.

Dashboard or Demo Interface – Displays predictions and explanations to users.

3. Folder Structure

phishing-detection/
│ data/ — Raw and cleaned datasets (Enron, SpamAssassin, PhishTank)
│ features/ — Extracted metadata feature CSVs
│ models/ — Trained models (text, metadata, fusion)
│ serve/ — FastAPI backend (app.py)
│ docker/ — Dockerfile and container configuration
│ tests/ — Test cases and validation scripts
│ demo_emails/ — Example phishing and legitimate emails
│ README.md — Documentation file
│ runbook.txt — Quick setup and run guide
│ demo_script.txt — Demo narration file
│ slides.pptx — Final presentation slides

4. Setup Instructions
Requirements

Python 3.8 or higher

pip (Python package manager)

GPU (optional, for faster model training)

Docker (optional, for containerized deployment)

Step 1 – Install Dependencies

Run the following command in your project directory:
pip install -r requirements.txt

Step 2 – Start the FastAPI Server

Navigate to the “serve” folder and start the API:
cd serve
uvicorn app:app --reload

Step 3 – Test the API

Use Postman, curl, or a Python script to send a POST request:
POST http://127.0.0.1:8000/predict

Body (JSON):
{
"subject": "Your account has been suspended",
"body": "Click here to verify your account http://fake-bank-login.com
"
}

Expected Response:
{
"label": "phishing",
"score": 0.97,
"explanation": "Suspicious URL and urgent tone detected"
}

5. Model Details
Model Type	Description	Output
Text Model (DistilBERT / RoBERTa)	Transformer-based text classifier fine-tuned on email data	Embeddings + phishing probability
Metadata Model (LightGBM)	Tree-based model trained on extracted metadata features	Metadata phishing score
Fusion Model	Combines both models’ outputs	Final phishing probability
Explainability	LIME (for text), SHAP (for metadata)	Highlights key words, links, and features influencing the result
6. QA and Testing
Purpose

As the QA/Demo/Documentation Lead, your role ensures that the system runs smoothly, accurately classifies emails, and presents clear explanations for every prediction.

Testing Steps

Test various sample emails (both phishing and legitimate).

Check that the API correctly returns label, score, and explanation.

Verify that invalid or incomplete inputs produce clear error messages.

Maintain test logs and expected vs actual outcomes.

Example Test Cases
Test ID	Input	Expected Output	Result
TC01	Legitimate business email	ham	Pass
TC02	Bank phishing email	phishing	Pass
TC03	Empty email body	validation error	Pass

All test logs are saved in the tests/test_cases.xlsx file.

7. Demo Instructions
Steps to Run the Demo

Start the API server using “uvicorn serve.app:app --reload”.

Open Postman or run “demo_email.py”.

Use emails from the “demo_emails” folder as examples.

Observe the prediction (phishing or ham) and explanation output.

(Optional) Launch the dashboard prototype or visualization tool.

Demo Script Outline

Introduction to the project and the problem of phishing.

Show system workflow and architecture diagram.

Send a phishing email sample to the API.

Display response and highlight explainability.

Conclude with accuracy results and practical use cases.

8. Runbook (for Judges or Reviewers)

Quick Steps to Execute Project:

Clone the repository from GitHub or extract the ZIP folder.

Open terminal → install dependencies using: pip install -r requirements.txt

Start the FastAPI server: uvicorn serve.app:app --reload

Test with sample emails via Postman or “demo_email.py”.

(Optional) Build Docker image and run container:
docker build -t phishing-detector .
docker run -p 8000:8000 phishing-detector

9. Team Roles
Member	Role	Key Tasks
A	Data & Feature Lead	Gather datasets (Enron, SpamAssassin, PhishTank), clean and label data, extract metadata features.
B	ML / Model Lead	Train and fine-tune models (DistilBERT, LightGBM), create fusion model, handle explainability (LIME/SHAP).
C	Backend & Integration	Build FastAPI backend, integrate IMAP plugin, create Docker deployment.
D (You)	QA / Demo / Documentation Lead	Perform end-to-end testing, prepare demo video and test cases, write README and runbook, ensure smooth project presentation.
10. Deliverables Summary

Cleaned and merged datasets

Extracted metadata feature CSVs

Trained models (text, metadata, fusion)

FastAPI backend with /predict endpoint

Docker deployment setup

Demo video and presentation slides

Documentation (README, Runbook, Test Cases)

11. Future Enhancements

Add multilingual phishing detection capability

Develop full-fledged dashboard for monitoring and visualization

Integrate directly with Gmail/Outlook APIs

Incorporate domain and IP-based threat intelligence

Improve model accuracy through continuous retraining

12. Conclusion

This project demonstrates how AI and explainable machine learning can significantly enhance cybersecurity by detecting phishing emails in real time. By combining NLP, metadata features, and interpretability techniques, the system ensures both accuracy and trustworthiness for users.

It offers a scalable and explainable approach suitable for organizations, email providers, and end-users looking to improve their email security.

© 2025 — Phishing Detection Team

✅ This README contains everything you need for documentation, submission, or presentation.

Would you like me to now prepare your Runbook.txt — a short 1-page “how to run this project” guide for judges or reviewers?
