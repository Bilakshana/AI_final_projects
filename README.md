# 🤖 AI Final Projects

A collection of three end-to-end AI/ML projects built, trained, evaluated, and deployed as interactive web applications on Streamlit Cloud.

- ♻️ **Track 1:** Waste image classification using a custom CNN and MobileNetV2
- 🎬 **Track 2:** Movie review sentiment analysis using TF-IDF and Logistic Regression
- 🧠 **Track 3:** Domain-specific RAG chatbot using FAISS vector search and LLaMA 3 via Groq

All three projects include full training pipelines, evaluation metrics, confusion matrices, and live Streamlit demos.

---

## 📁 Projects Overview

| Track | Project | Tech Stack | Live App | Repo | Demo |
|-------|---------|------------|----------|------|------|
| Track 1 | ♻️ Waste Image Classifier | CNN, MobileNetV2, TensorFlow | [Live App](https://aifinalprojecttrack1-bilakshana-neupane.streamlit.app) | [GitHub](https://github.com/Bilakshana/ai_final_project_track1) | [Recording](https://drive.google.com/file/d/1zmDULiE6z9uLao5g6BdNb5_r5aTkoVzO/view?usp=sharing) |
| Track 2 | 🎬 Sentiment Analysis | TF-IDF, Logistic Regression, NLP | [Live App](https://aifinalprojecttrack2-bilakshana-neu.streamlit.app) | [GitHub](https://github.com/Bilakshana/ai_final_project_track_2) | [Recording](https://drive.google.com/file/d/1HDKS4sQcoLHWHse33oR9YMQ7LEaA2Air/view?usp=sharing) |
| Track 3 | 🧠 RAG Chatbot | FAISS, LLaMA 3, Groq, Sentence Transformers | [Live App](https://aifinalprojecttrack3-bilakshana-neu.streamlit.app) | [GitHub](https://github.com/Bilakshana/ai_final_project_track_3) | [Recording](#) |

---

## 🗂️ Track 1 : Smart Waste Image Classifier

**Repo:** https://github.com/Bilakshana/ai_final_project_track1  

**Live App:** https://aifinalprojecttrack1-bilakshana-neupane.streamlit.app 

**Demo Recording:** https://drive.google.com/file/d/1zmDULiE6z9uLao5g6BdNb5_r5aTkoVzO/view?usp=sharing

### 🎯 Objective
Build an image classification system that classifies waste images into 6 categories: Cardboard, Glass, Metal, Paper, Plastic, and Trash.

### 📦 Dataset
**TrashNet** : 2,527 labeled images across 6 waste categories  
Download: [Kaggle — TrashNet](https://www.kaggle.com/datasets/feyzazkefe/trashnet)

| Class | Images |
|-------|--------|
| Cardboard | 403 |
| Glass | 501 |
| Metal | 410 |
| Paper | 594 |
| Plastic | 482 |
| Trash | 137 |

### 🏗️ Model Architecture

**Model 1 : Custom CNN (trained from scratch)**
- 3 blocks of Conv2D → BatchNorm → MaxPool → Dropout
- GlobalAveragePooling → Dense(256) → Softmax(6)
- L2 regularization on all layers

**Model 2 : MobileNetV2 (transfer learning)**
- Pretrained on ImageNet weights
- Phase 1: Base frozen, only head trained
- Phase 2: Top 54 layers unfrozen and fine-tuned (LR = 1e-5)

### ⚙️ Image Preprocessing & Augmentation
- Rescaling to [0, 1]
- Random rotation (±20°)
- Horizontal flip
- Random zoom (±20%)
- Width/height shift (±15%)
- Validation data: rescaling only (no augmentation)

### 📊 Evaluation Results

| Metric | Custom CNN | MobileNetV2 |
|--------|-----------|-------------|
| Accuracy | ~74% | ~88–92% |
| Precision | ~75% | ~87–90% |
| Recall | ~74% | ~88–92% |
| F1-Score | ~74% | ~87–91% |

Evaluation includes confusion matrices and per-class classification reports.

### 🔍 Error Analysis
Common confusion pairs:
- Glass ↔ Metal (reflective surfaces look similar)
- Paper ↔ Cardboard (similar texture and colour)
- Plastic ↔ Glass (transparent materials)

### 🚀 How to Run Locally
```bash
git clone https://github.com/Bilakshana/ai_final_project_track1
cd ai_final_project_track1
pip install -r requirements.txt
python train.py        # Train both models (~30–60 min GPU)
python evaluate.py     # Evaluate and generate plots
streamlit run app.py   # Launch the demo
```

### 📚 Learning Outcomes
- CNN architecture and convolutional layers
- Transfer learning with MobileNetV2
- Image augmentation strategies
- Interpreting classification metrics and confusion matrices

---

## 🗂️ Track 2 : Sentiment Analysis System

**Repo:** https://github.com/Bilakshana/ai_final_project_track_2

**Live App:** https://aifinalprojecttrack2-bilakshana-neu.streamlit.app 

**Demo Recording:** https://drive.google.com/file/d/1HDKS4sQcoLHWHse33oR9YMQ7LEaA2Air/view?usp=sharing

### 🎯 Objective
Build a sentiment analysis system that classifies IMDb movie reviews as Positive or Negative using NLP techniques.

### 📦 Dataset
**IMDb 50K Movie Reviews** — 50,000 reviews evenly split between positive and negative  
Download: [Kaggle — IMDb Dataset](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)

| Split | Samples |
|-------|---------|
| Train | 40,000 |
| Test  | 10,000 |
| Positive | 25,000 |
| Negative | 25,000 |

### 🏗️ Model Architecture

**Text Preprocessing Pipeline:**
- Lowercasing
- HTML tag removal
- Contraction expansion
- Punctuation and digit removal
- Stopword removal (negation words kept: not, no, never…)
- WordNet Lemmatization

**Model — TF-IDF + Logistic Regression:**
- TF-IDF Vectorizer: 50,000 features, unigrams + bigrams, sublinear TF
- Logistic Regression: C=1.0, lbfgs solver, max_iter=1000

### 📊 Evaluation Results

| Metric | Score |
|--------|-------|
| Accuracy | ~88% |
| Precision | ~88% |
| Recall | ~88% |
| F1-Score | ~88% |
| ROC-AUC | ~95% |

### 🚀 How to Run Locally
```bash
git clone https://github.com/Bilakshana/ai_final_project_track_2
cd ai_final_project_track_2
pip install -r requirements.txt
python train.py        # Train the model
python evaluate.py     # Evaluate and generate plots
streamlit run app.py   # Launch the demo
```

### 📚 Learning Outcomes
- NLP preprocessing pipelines
- TF-IDF vectorization and n-gram features
- Classical ML for text classification
- Evaluating text classification systems

---

## 🗂️ Track 3 : Domain-Specific RAG Chatbot

**Repo:** https://github.com/Bilakshana/ai_final_project_track_3 

**Live App:** https://aifinalprojecttrack3-bilakshana-neu.streamlit.app 

**Demo Recording:** 

### 🎯 Objective
Build a Retrieval-Augmented Generation chatbot that answers questions grounded in user-uploaded domain-specific documents (PDF or TXT), eliminating hallucination by injecting only real document content into the LLM prompt.

### 🏗️ RAG Architecture

```
User Query
    │
    ▼
Embedding Model (all-MiniLM-L6-v2)
    │
    ▼
FAISS Vector Search  ←── Document Chunks (indexed)
    │
    ▼
Top-K Relevant Chunks
    │
    ▼
Prompt Builder (Zero-shot with context injection)
    │
    ▼
LLaMA 3.1 8B via Groq API
    │
    ▼
Grounded Answer
```

### ⚙️ Technical Implementation
- **Document Parsing:** pypdf for PDFs, plain text for TXT files
- **Chunking:** LangChain text splitter (chunk size: 500, overlap: 50)
- **Embeddings:** sentence-transformers (all-MiniLM-L6-v2, 384 dimensions)
- **Vector Search:** FAISS IndexFlatIP (inner product similarity)
- **Prompt Engineering:** Zero-shot prompting with context injection
- **LLM:** LLaMA 3.1 8B Instant via Groq API (free tier)

### 📊 Evaluation Results

| Metric | Score |
|--------|-------|
| Avg Retrieval Score | 0.82 |
| Avg Answer Score | 0.79 |
| Queries Evaluated | 7 |
| Hallucination Risk | Low |

### 🔬 Model Comparison

| Approach | Avg Score | Hallucination Risk |
|----------|-----------|--------------------|
| Pure LLM (no RAG) | ~0.35 | High |
| Zero-shot RAG | ~0.79 | Low |
| Few-shot RAG | ~0.83 | Very Low |

### 🚀 How to Run Locally
```bash
git clone https://github.com/Bilakshana/ai_final_project_track_3
cd ai_final_project_track_3
pip install -r requirements.txt
streamlit run app.py
# 1. Enter your free Groq API key in the sidebar
# 2. Upload any PDF or TXT file
# 3. Click Build Index
# 4. Start asking questions
```

> Get a free Groq API key at [console.groq.com](https://console.groq.com)

### 📚 Learning Outcomes
- LLM foundations and prompt engineering
- Embedding-based vector search with FAISS
- RAG pipeline implementation
- Reducing hallucination in LLM outputs

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
| Language | Python 3.11 |

---



## 👤 Author

**Bilakshana Neupane**  
GitHub: [github.com/Bilakshana](https://github.com/Bilakshana)

---

## 📚 References

- He et al. (2016). Deep Residual Learning for Image Recognition.
- Howard et al. (2017). MobileNets: Efficient Convolutional Neural Networks.
- Lewis et al. (2020). Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks. [arXiv:2005.11401](https://arxiv.org/abs/2005.11401)
- Sentence-Transformers: https://www.sbert.net
- FAISS: https://github.com/facebookresearch/faiss
- Groq LLaMA 3 API: https://console.groq.com
- TrashNet Dataset: https://github.com/garythung/trashnet
- IMDb Dataset: https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews

