# Sentiment Analysis on Twitter Tweets (Sentiment140 Dataset)

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Logistic%20Regression-green?style=flat-square&logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)
![Colab](https://img.shields.io/badge/Open%20In-Colab-orange?style=flat-square&logo=googlecolab)

## 🚀 Project Overview
This project focuses on **Sentiment Analysis of Tweets** using the popular **Sentiment140 dataset**.  
The model predicts whether a tweet expresses a **positive** or **negative** sentiment by leveraging **Natural Language Processing (NLP)** techniques and a **Logistic Regression classifier**.

The pipeline includes:
- **Text preprocessing** (cleaning, stopword removal, and stemming)
- **TF-IDF Vectorization** for numerical feature extraction
- **Model training** using Logistic Regression
- **Model evaluation** on unseen test data
- **Model persistence** with `pickle` for future use

---

## 📂 Dataset
- **Dataset:** [Sentiment140](https://www.kaggle.com/datasets/kazanova/sentiment140)
- **Size:** 1.6 million tweets
- **Target Variable:**  
  - `0` → Negative Sentiment  
  - `4` → Positive Sentiment (converted to `1` in this project)

---

## 🛠️ Tech Stack
- **Languages:** Python 3.10
- **Libraries:**  
  - `numpy`, `pandas` – Data handling  
  - `nltk` – Stopwords, stemming  
  - `scikit-learn` – TF-IDF, train-test split, Logistic Regression  
  - `pickle` – Model saving  
- **Environment:** Google Colab

---

## ⚙️ Project Pipeline
1. **Data Loading**: Load the dataset with correct encoding (`latin-1`).  
2. **Data Cleaning**:  
   - Remove unwanted characters, mentions, URLs, and punctuation.  
   - Apply **stemming** using `PorterStemmer`.  
3. **Feature Extraction**: Convert text to numerical vectors using **TF-IDF**.  
4. **Train-Test Split**: 80% training, 20% testing (stratified).  
5. **Model Training**: Logistic Regression with `max_iter=1000`.  
6. **Evaluation**:  
   - **Training Accuracy:** ~80%  
   - **Test Accuracy:** ~77%  
   - No significant overfitting detected.  
7. **Model Deployment**: Save model as `trained_model.sav` for re-use.

---

## 📊 Model Performance
| Dataset     | Accuracy |
|-------------|----------|
| **Training** | **80.4%** |
| **Testing**  | **77.7%** |

---

## 🔍 Example Predictions
```python
# Load the model
import pickle
loaded_model = pickle.load(open('trained_model.sav', 'rb'))

# Predict sentiment
tweet = "I love this product! Absolutely amazing."
vectorized_tweet = vector.transform([tweet])
prediction = loaded_model.predict(vectorized_tweet)

print("Positive Tweet" if prediction[0] == 1 else "Negative Tweet")
