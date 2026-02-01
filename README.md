📩 Spam Classifier with AI Explanation

A production-ready Spam Classification system built using FastAPI, Machine Learning, and Large Language Models (LLMs), with a Streamlit web app for user-friendly interaction.

This project not only classifies messages as Spam / Not Spam, but also explains why a message is spam and provides one clear safety recommendation, making the system transparent and practical for real-world use.

🚀 Live Demo
🔗 FastAPI Backend (API)
https://spam-classifier-api-uiiy.onrender.com

🖥 Streamlit Web App (UI)
https://spam-classifier-with-explanation.streamlit.app/


The Streamlit app consumes the live FastAPI backend.

🧠 Project Overview

Most spam classifiers stop at returning a label.
This project goes further by answering:

Is this message spam?

What type of spam is it?

Why is it spam?

What should the user do next?

This makes the system suitable for real-world applications, not just demos.

🏗 System Architecture
User Input
   ↓
FastAPI (/spam/predict)
   ↓
ML Model (TF-IDF + Classifier)
   ↓
Prediction (Spam / Not Spam)
   ↓
FastAPI (/spam-explain/explain)
   ↓
LLM (LLaMA via ChatGroq)
   ↓
Human-readable Explanation + Advice
   ↓
Streamlit UI

🔧 Tech Stack
Backend

FastAPI – High-performance REST API

scikit-learn – Spam classification model

NLTK – Text preprocessing

Pickle – Model persistence

AI Explanation Layer

LangChain

ChatGroq (LLaMA-3.1) – Explanation & advice generation

Frontend

Streamlit – Interactive web application

Deployment

Render – FastAPI backend

Streamlit Cloud – UI hosting

📁 Project Structure
spam_classifier/
│
├── main.py
├── model.pkl
├── vectorizer.pkl
├── requirements.txt
│
├── routers/
│   ├── spam_router.py
│   └── spam_explain_router.py
│
├── models/
│   └── spam_model.py
│
└── streamlit_app/
    └── app.py

🔌 API Usage
1️⃣ Spam Prediction

Endpoint

POST /spam/predict


Request

{
  "text": "Win ₹10,00,000 now! Click here"
}


Response

{
  "text": "Win ₹10,00,000 now! Click here",
  "prediction": "Spam"
}

2️⃣ Spam Explanation (LLM-powered)

Endpoint

POST /spam-explain/explain


Request

{
  "text": "Win ₹10,00,000 now! Click here",
  "prediction": "Spam"
}


Response

{
  "prediction": "Spam",
  "explanation": "This is a lottery scam designed to create urgency and lure users into clicking unsafe links. Avoid interacting with such messages and block the sender immediately."
}

🖥 Streamlit App Features

The Streamlit web app provides:

📝 Text input for messages

🔍 Spam / Not Spam prediction

🧠 AI-generated explanation

📌 Clear, readable output

🔗 Live App:
https://spam-classifier-with-explanation.streamlit.app/

⚠️ Important Technical Notes
scikit-learn Version Compatibility

The ML model was trained using:

scikit-learn==1.6.1


For reliable inference, the same version must be used during deployment.

NLTK Resources

The backend automatically ensures the availability of:

punkt

punkt_tab

stopwords

🔐 Environment Variables

Create a .env file for local development:

GROQ_API_KEY=your_groq_api_key


This key is required for AI-based explanation generation.

📊 Model Details

Vectorization: TF-IDF

Classifier: Tree-based ensemble model

Output Labels:

Spam

Not Spam

The model is optimized for practical spam detection, not toy datasets.

✨ Key Highlights

✅ End-to-end ML + LLM pipeline

✅ Explainable AI output

✅ Production-ready API

✅ Clean UI for non-technical users

✅ Real deployment debugging handled

🚀 Future Improvements

Prediction confidence scores

Multilingual spam detection

Transformer-based spam classifier

User history & analytics

Dockerized deployment

👨‍💻 Author

Alekhya Chatterjee
Machine Learning & AI Developer
Focused on building practical, explainable AI systems.

⭐ Final Note

This project demonstrates:

Real-world ML deployment

API-first backend design

Explainable AI integration

Debugging production issues end-to-end

If you found this useful, feel free to ⭐ the repository or build upon it.
