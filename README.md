# 🤖 AI Final Projects

A collection of three end-to-end AI/ML projects built, trained, evaluated,
and deployed as interactive web applications on Streamlit Cloud.

- ♻️ **Track 1:** Waste image classification using a custom CNN and MobileNetV2
- 🎬 **Track 2:** Movie review sentiment analysis using TF-IDF and Logistic Regression
- 🧠 **Track 3:** Domain-specific RAG chatbot using FAISS vector search and LLaMA 3 via Groq

All three projects include full training pipelines, evaluation metrics,
confusion matrices, and live Streamlit demos.

---

## 📁 Projects Overview

| Track | Project | Tech Stack | Live App | Repo | Demo |
|-------|---------|------------|----------|------|------|
| Track 1 | ♻️ Waste Image Classifier | CNN, MobileNetV2, TensorFlow | [Live App](https://aifinalprojecttrack1-bilakshana-neupane.streamlit.app) | [GitHub](https://github.com/Bilakshana/ai_final_project_track1) | [Recording](#) |
| Track 2 | 🎬 Sentiment Analysis | TF-IDF, Logistic Regression, NLP | [Live App](https://aifinalprojecttrack2-bilakshana-neu.streamlit.app/) | [GitHub](https://github.com/Bilakshana/ai_final_project_track_2) | [Recording](#) |
| Track 3 | 🧠 RAG Chatbot | FAISS, LLaMA 3, Groq, Sentence Transformers | [Live App](https://aifinalprojecttrack3-bilakshana-neu.streamlit.app/) | [GitHub](https://github.com/Bilakshana/ai_final_project_track_3) | [Recording](#) |

---

## 🗂️ Track 1: Waste Image Classifier

**Repo:** https://github.com/Bilakshana/ai_final_project_track1  

**Live App:** https://aifinalprojecttrack1-bilakshana-neupane.streamlit.app

**Demo Recording:** `[paste your YouTube/Drive recording link here]`

### What it does
Classifies waste images into 6 categories: Cardboard, Glass, Metal, Paper, Plastic, Trash.
Upload any waste photo and instantly get a prediction with confidence scores and a recycling tip.

### Models
- Custom CNN trained from scratch — ~74% accuracy
- MobileNetV2 with transfer learning — ~88–92% accuracy

### Dataset
TrashNet : 2,527 images across 6 classes  
[Kaggle Dataset](https://www.kaggle.com/datasets/feyzazkefe/trashnet)

### How to run locally
```bash
git clone https://github.com/Bilakshana/ai_final_project_track1
cd ai_final_project_track1
pip install -r requirements.txt
python train.py        # Train both models
python evaluate.py     # Evaluate and generate plots
streamlit run app.py   # Launch the demo
```

---

## 🗂️ Track 2 : IMDb Sentiment Analysis

**Repo:** https://github.com/Bilakshana/ai_final_project_track_2  

**Live App:** https://aifinalprojecttrack2-bilakshana-neu.streamlit.app

**Demo Recording:** `[paste your YouTube/Drive recording link here]`

### What it does
Classifies IMDb movie reviews as Positive or Negative using NLP techniques.
Supports single review prediction and batch CSV prediction.

### Model
- TF-IDF Vectorization + Logistic Regression
- Accuracy: ~88% | F1-Score: ~88% | ROC-AUC: ~95%

### Dataset
IMDb 50K Movie Reviews  
[Kaggle Dataset](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)

### How to run locally
```bash
git clone https://github.com/Bilakshana/ai_final_project_track_2
cd ai_final_project_track_2
pip install -r requirements.txt
python train.py        # Train the model
python evaluate.py     # Evaluate and generate plots
streamlit run app.py   # Launch the demo
```

---

## 🗂️ Track 3 : Domain-Specific RAG Chatbot

**Repo:** https://github.com/Bilakshana/ai_final_project_track_3 

**Live App:** https://aifinalprojecttrack3-bilakshana-neu.streamlit.app 

**Demo Recording:** `[paste your YouTube/Drive recording link here]`

### What it does
A Retrieval-Augmented Generation chatbot that answers questions grounded in
your own uploaded documents (PDF or TXT) using LLaMA 3 via Groq API.
Eliminates hallucination by injecting only real document content into the prompt.

### How it works
1. Upload your PDF or TXT documents in the sidebar
2. Documents are chunked and embedded using MiniLM-L6-v2
3. FAISS vector search finds the most relevant chunks for your question
4. LLaMA 3.1 8B generates a grounded answer from those chunks only

### Evaluation Results
| Metric | Score |
|--------|-------|
| Avg Retrieval Score | 0.82 |
| Avg Answer Score | 0.79 |
| Hallucination Risk | Low |

### Tech Stack
- Embeddings: `sentence-transformers` (all-MiniLM-L6-v2)
- Vector Search: FAISS
- LLM: LLaMA 3.1 8B via Groq API
- Interface: Streamlit

### How to run locally
```bash
git clone https://github.com/Bilakshana/ai_final_project_track_3
cd ai_final_project_track_3
pip install -r requirements.txt
streamlit run app.py
# Enter your free Groq API key in the sidebar
# Upload any PDF or TXT file and start chatting
```

> Get a free Groq API key at [console.groq.com](https://console.groq.com)

---

## 🛠️ Technologies Used

| Category | Tools |
|----------|-------|
| Deep Learning | TensorFlow, Keras, MobileNetV2 |
| Machine Learning | Scikit-learn, Logistic Regression, TF-IDF |
| NLP | NLTK, Sentence Transformers, LangChain |
| Vector Search | FAISS |
| LLM | LLaMA 3.1 8B via Groq API |
| Web App | Streamlit |
| Deployment | Streamlit Cloud |
| Version Control | Git, GitHub |

---

## 👤 Author

**Bilakshana Neupane**  
GitHub: [github.com/Bilakshana](https://github.com/Bilakshana)

LinkedIn: https://www.linkedin.com/in/bilakshana-neupane

---

## 📌 Notes

- All three apps are deployed and publicly accessible via Streamlit Cloud
- Track 3 requires a free Groq API key — get one at [console.groq.com](https://console.groq.com)
- Datasets are not included in repos due to size, download links provided above
- Model files for Track 1 are included directly in the GitHub repo
