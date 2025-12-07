# 🧪 Drug–Drug Interaction Side Effect Predictor (Flask App)

This project predicts the **top 10 possible side effects** when two drugs are taken together.  
It uses:

- RDF2Vec embeddings (128-dim each)  
- XGBoost MultiOutputClassifier  
- TwoSides multi-label dataset  
- DrugName → DrugBank ID mapping  
- Flask web interface  

The app loads drug embeddings, combines them, runs the trained model, and displays side-effect probabilities with risk levels.

---

## 🚀 Features

- Enter two drug names  
- Convert drug names → DrugBank IDs  
- Fetch RDF2Vec embeddings  
- Build 256-dim combined input vector  
- Predict side-effect probabilities  
- Display top 10 side effects  
- Auto-label risk as High / Medium / Low  
- Simple Flask UI  

---

## 📂 Project Structure

```
project/
│── app.py
│── requirements.txt
│── final_xgb_model.pkl
│── DrugNamee.csv
│── TWO_SIDES_50000_multilabel_with_names.csv
│── mock_rdf2vec_embeddings.csv
│
├── templates/
│     └── index.html
│
└── static/   (optional)
      ├── style.css
      └── script.js
```

---

## 📦 Requirements

Minimal requirements:

```
Flask==3.0.3
pandas==2.2.3
numpy==2.2.4
joblib==1.4.2
scikit-learn==1.6.1
xgboost==3.0.0
```

Save these in **requirements.txt**.

---

## 🛠️ Installation & Setup

### 1️⃣ Clone the repository
```
git clone https://github.com/Logicrithm/Drug-Drug-Interaction.git
cd yourrepo
```

### 2️⃣ Create a virtual environment

#### Windows:
```
python -m venv venv
venv\Scripts\activate
```

#### macOS / Linux:
```
python3 -m venv venv
source venv/bin/activate
```

### 3️⃣ Install dependencies
```
pip install -r requirements.txt
```

### 4️⃣ Run the Flask app
```
python app.py
```

The app will run at:

👉 **http://127.0.0.1:8000/**

---

## 🧠 How The App Works

### ✔ Step 1 — User enters two drug names  
Example: `"aspirin"` and `"warfarin"`

### ✔ Step 2 — Convert names → DrugBank ID  
Using the mapping file `DrugNamee.csv`.

### ✔ Step 3 — Fetch embeddings  
From `mock_rdf2vec_embeddings.csv`.

### ✔ Step 4 — Combine vectors  
```
combined = concat(drug1_vector, drug2_vector)
```

### ✔ Step 5 — Predict using trained model  
The model outputs probabilities for all side effects.

### ✔ Step 6 — Display top 10  
Sorted by probability along with risk levels.

---

## 🖼️ UI Screenshot (Add your screenshot)
```
![App Screenshot](screenshots/main_ui.png)
```

---

## 📁 Required Data Files

| File | Description |
|------|-------------|
| `final_xgb_model.pkl` | Trained XGBoost classifier |
| `DrugNamee.csv` | Drug name to DrugBank ID mapping |
| `TWO_SIDES_50000_multilabel_with_names.csv` | Needed to rebuild the list of side-effect labels |
| `mock_rdf2vec_embeddings.csv` | 128-dim embeddings for each drug |

---

## 🧪 Example Prediction Output

| Side Effect | Probability | Risk |
|------------|-------------|------|
| GI Bleeding | 0.92 | High |
| Bruising | 0.76 | Medium |
| Headache | 0.41 | Low |

---

## 🐞 Troubleshooting

### ❌ Drug not found  
The drug name does not exist in `DrugNamee.csv`.  
Try:  
- lowercase  
- removing spaces  
- checking spelling  

### ❌ KeyError (embedding not found)  
The DrugBank ID for your drug is not in `mock_rdf2vec_embeddings.csv`.

---

## 🤝 Contributing
Pull requests and suggestions are welcome.

---

## 📜 License
MIT License (you can replace this with any license you prefer)

---

## 🙌 Acknowledgements
- TwoSides dataset  
- RDF2Vec embedding methodology  
- DrugBank mapping  
- XGBoost MultiOutputClassifier  

