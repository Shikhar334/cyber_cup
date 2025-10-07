# cyber_cup

AI-Powered Phishing Email Detection System
An end-to-end machine learning project that detects phishing emails using Natural Language Processing (NLP) and metadata analysis. The system combines text-based deep learning with handcrafted features from email metadata to accurately classify phishing vs. legitimate (ham) emails. It also provides explainable outputs using LIME and SHAP to help users understand model decisions.
PROJECT OVERVIEW
Phishing is one of the most common cyberattacks used to steal sensitive information. This project builds an AI-powered system capable of detecting phishing emails automatically by analyzing:
Email text content (subject, body)
Metadata (headers, links, attachments, SPF/DKIM results)
Explainability (why an email is flagged)
The final system exposes a /predict API endpoint and a demo dashboard to visualize predictions and explanations.
ARCHITECTURE
Email Input → Email Parser & Feature Extractor → ML Models
ML Models include:
Text Model (DistilBERT / RoBERTa)
Metadata Model (LightGBM)
Fusion Model (Text Embeddings + Metadata)
Then comes Explainability Layer:
LIME (text)
SHAP (metadata)
Finally, FastAPI Backend → /predict Endpoint → JSON Output {label, score, explanation}
FOLDER STRUCTURE
phishing-detection/
│ data/ – raw + cleaned datasets (Enron, SpamAssassin, PhishTank)
│ features/ – extracted metadata feature CSVs
│ models/ – trained models (text, metadata, fusion)
│ serve/ – FastAPI server files (app.py)
│ docker/ – Docker artifacts
│ tests/ – test cases and validation scripts
│ demo_emails/ – sample phishing and legitimate emails
│ README.md – documentation
│ runbook.txt – quick setup and run guide
│ demo_script.txt – demo video narration
│ slides.pptx – final presentation slides
SETUP INSTRUCTIONS
Requirements:
Python 3.8 or higher
pip
GPU (optional)
Docker (optional)
Install dependencies:
pip install -r requirements.txt
Run the API Server:
cd serve
uvicorn app:app --reload
Test the API:
Send a POST request to /predict with email content using Postman or curl. Example:
subject: "Your account has been suspended"
body: "Click here to verify your account http://fake-bank-login.com
Expected Output:
label: phishing
score: 0.97
explanation: Suspicious URL and urgent tone detected
MODEL DETAILS
Text Model (DistilBERT / RoBERTa): Fine-tuned transformer on email subject & body producing phishing probability.
Metadata Model (LightGBM): Trained on extracted features like links, SPF/DKIM results, and headers.
Fusion Model: Combines outputs from text and metadata models to produce a final phishing score.
Explainability: LIME for text and SHAP for metadata to make model decisions interpretable.
QA & TESTING
Example test cases:
TC01 - Legitimate business email → Expected Output: ham → Result: Pass
TC02 - Bank phishing email → Expected Output: phishing → Result: Pass
TC03 - Empty body → Expected Output: validation error → Result: Pass
Full test logs are available in tests/test_cases.xlsx.
DEMO INSTRUCTIONS
Start the FastAPI server: uvicorn serve.app:app --reload
Open Postman or run demo_email.py to send requests.
Use samples from the demo_emails folder.
Observe prediction results and explanations.
Optionally, launch the dashboard prototype for visualization.
Demo Video Script (in demo_script.txt) includes narration for:
Project introduction
Workflow overview
Live phishing detection example
Explainability visualization
RUNBOOK (for Judges or Reviewers)
Quick Steps to Run:
Clone the repository.
Install dependencies using pip install -r requirements.txt.
Start the FastAPI server using uvicorn serve.app:app --reload.
Send sample email JSON to /predict using Postman.
Optionally, use Docker:
docker build -t phishing-detector .
docker run -p 8000:8000 phishing-detector
TEAM ROLES
A – Data & Feature Lead: Dataset gathering, cleaning, feature extraction.
B – ML / Model Lead: Model training, explainability, and evaluation.
C – Backend & Integration: API development, IMAP integration, containerization.
D – QA / Demo / Docs Lead (You): End-to-end testing, demo preparation, documentation, presentation.
DELIVERABLES SUMMARY
Cleaned datasets and extracted features
Trained models (text, metadata, fusion)
FastAPI backend service
Docker deployment files
Demo video and presentation slides
README, Runbook, Test Cases
FUTURE IMPROVEMENTS
Add multilingual phishing detection support
Full dashboard for monitoring and visualization
Integrate with Gmail/Outlook API
Add domain/IP threat intelligence modules
CONCLUSION
This project demonstrates how AI and explainable ML can enhance email security by detecting phishing attempts in real time. By combining NLP, metadata, and interpretability, it ensures both accuracy and trustworthiness for enterprise and personal users.
