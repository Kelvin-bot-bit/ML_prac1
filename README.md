# ML_prac1
# Machine Learning Practicals

A collection of practical machine learning exercises implemented in Python using **Pandas, Scikit-learn, Joblib, and Jupyter Notebook**.

This repository focuses on developing practical machine learning skills through data preparation, model training, prediction, evaluation, model persistence, and data exploration.

---

## 📌 Project Overview

This project contains hands-on machine learning exercises covering:

* Data loading and exploration
* Feature and target selection
* Classification using Decision Trees
* Training and testing machine learning models
* Model accuracy evaluation
* Saving and loading trained models
* Decision-tree visualization
* Exploratory analysis of datasets

The main practical implements a **music genre recommendation/classification model** that predicts a user's likely music genre based on demographic features such as age and gender.

A second practical explores a **video game sales dataset** using Pandas for basic data analysis and statistical exploration.

---

## 🚀 Technologies Used

| Technology           | Purpose                                     |
| -------------------- | ------------------------------------------- |
| **Python**           | Core programming language                   |
| **Pandas**           | Data loading and manipulation               |
| **Scikit-learn**     | Machine learning model development          |
| **Joblib**           | Model serialization and persistence         |
| **Jupyter Notebook** | Interactive development and experimentation |
| **Graphviz**         | Decision-tree visualization                 |

---

## 🧠 Machine Learning Workflow

The music recommendation practical follows a basic supervised learning workflow:

```text
Dataset
   │
   ▼
Data Loading
   │
   ▼
Feature / Target Separation
   │
   ▼
Train/Test Split
   │
   ▼
Decision Tree Classifier
   │
   ▼
Model Training
   │
   ▼
Prediction
   │
   ▼
Accuracy Evaluation
   │
   ▼
Model Persistence
   │
   ▼
Decision Tree Visualization
```

---

## 🎵 Music Genre Classification

The main practical uses a dataset containing information about users and their preferred music genres.

### Features

The model uses:

* **Age**
* **Gender**

### Target

The target variable is:

* **Genre**

The Decision Tree Classifier learns patterns between the input features and music genre preferences.

### Example Prediction

The trained model can be used to make predictions for new users:

```python
predictions = model.predict([[21, 1]])
print(predictions)
```

The model returns the predicted music genre based on the learned patterns.

---

## 🌳 Decision Tree Classification

The project uses Scikit-learn's `DecisionTreeClassifier`.

```python
from sklearn.tree import DecisionTreeClassifier

model = DecisionTreeClassifier()
model.fit(X, Y)
```

The dataset is divided into training and testing sets before evaluating the model:

```python
from sklearn.model_selection import train_test_split

X_train, X_test, Y_train, Y_test = train_test_split(
    X,
    Y,
    test_size=0.2
)

model.fit(X_train, Y_train)
```

Model performance is then evaluated using the test data.

```python
score = model.score(X_test, Y_test)
print(score)
```

---

## 💾 Model Persistence

After training, the machine learning model is saved using **Joblib**.

```python
import joblib

joblib.dump(model, 'music-recommender.joblib')
```

The saved model can later be loaded without retraining:

```python
model = joblib.load('music-recommender.joblib')

predictions = model.predict([[21, 1]])
```

This demonstrates an important machine learning workflow: **training a model once and reusing it later for predictions**.

---

## 🌳 Model Visualization

The trained Decision Tree can be exported into Graphviz DOT format:

```python
from sklearn import tree

tree.export_graphviz(
    model,
    out_file="music-recommender.dot",
    feature_names=['age', 'gender'],
    class_names=sorted(Y.unique()),
    label='all',
    rounded=True,
    filled=True
)
```

The generated `music-recommender.dot` file provides a visual representation of the model's decision-making process.
<img width="950" height="636" alt="image" src="https://github.com/user-attachments/assets/52757b5a-f05a-4557-bbf0-3d82899ec36f" />


---

## 🎮 Video Game Sales Analysis

The repository also contains a separate practical based on the `vgsales.csv` dataset.

The exercise demonstrates basic data exploration using Pandas.

### Operations performed

```python
import pandas as pd

df = pd.read_csv('vgsales.csv')
```

Dataset dimensions can be inspected using:

```python
df.shape
```

Statistical information can be explored using:

```python
df.describe()
```

The underlying dataset values can also be inspected:

```python
df.values
```

This practical provides a foundation for more advanced exploratory data analysis and machine learning workflows.

---

## 📁 Project Structure

```text
ML/
│
├── music.ipynb
├── sale.ipynb
│
├── music.csv
├── vgsales.csv
│
├── music-recommender.joblib
├── music-recommender.dot
│
├── requirements.txt
├── README.md
│
└── .gitignore
```

### File Description

| File                       | Description                                  |
| -------------------------- | -------------------------------------------- |
| `music.ipynb`              | Music genre classification practical         |
| `sale.ipynb`               | Video game sales data analysis               |
| `music.csv`                | Dataset used for music classification        |
| `vgsales.csv`              | Video game sales dataset                     |
| `music-recommender.joblib` | Saved trained Decision Tree model            |
| `music-recommender.dot`    | Graphviz representation of the Decision Tree |
| `requirements.txt`         | Python project dependencies                  |
| `README.md`                | Project documentation                        |
| `.gitignore`               | Files and directories excluded from Git      |

---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Kelvin-bot-bit/ML_prac1.git
```

Navigate into the project:

```bash
cd ML_prac1
```

---

### 2. Create a Virtual Environment

It is recommended to use a virtual environment to isolate the project's dependencies.

```bash
python3 -m venv .venv
```

Activate it on Linux/macOS:

```bash
source .venv/bin/activate
```

On Windows:

```powershell
.venv\Scripts\activate
```

---

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

Open either:

```text
music.ipynb
```

or:

```text
sale.ipynb
```

and execute the notebooks sequentially.

---

## 📊 Model Development Process

The music classification practical demonstrates the following machine learning concepts:

### 1. Data Loading

The dataset is loaded using Pandas:

```python
music_data = pd.read_csv('music.csv')
```

### 2. Feature Selection

The target column is removed from the input dataset:

```python
X = music_data.drop(columns=['genre'])
```

### 3. Target Selection

The target variable is extracted:

```python
Y = music_data['genre']
```

### 4. Model Training

A Decision Tree Classifier is created and trained:

```python
model = DecisionTreeClassifier()
model.fit(X, Y)
```

### 5. Prediction

The trained model predicts the genre for previously unseen inputs:

```python
model.predict([[21, 1]])
```

### 6. Evaluation

The dataset is divided into training and testing subsets and model performance is evaluated.

### 7. Model Persistence

The trained model is serialized with Joblib so it can be reused later.

---

## 🔐 Reproducibility and Repository Hygiene

The repository should **not** commit local virtual environments or other machine-specific files.

Recommended `.gitignore`:

```gitignore
# Python
__pycache__/
*.py[cod]
*.pyo

# Virtual environments
.venv/
venv/
env/

# Jupyter
.ipynb_checkpoints/

# IDEs
.vscode/
.idea/

# OS files
.DS_Store
Thumbs.db
```

If `.venv` is already being tracked by Git, remove it from Git's index before pushing:

```bash
git rm -r --cached .venv
```

Then commit the change:

```bash
git add .gitignore
git commit -m "chore: exclude virtual environment from repository"
```

---

## 📚 Learning Objectives

This project was developed to strengthen practical understanding of:

* Machine learning fundamentals
* Supervised learning
* Classification algorithms
* Decision trees
* Feature engineering fundamentals
* Dataset exploration
* Train/test splitting
* Model evaluation
* Model serialization
* Data analysis with Pandas
* Jupyter Notebook workflows
* Basic machine learning visualization

---

## 🔮 Future Improvements

The project can be extended with:

* Additional machine learning algorithms
* Cross-validation
* Hyperparameter tuning
* Feature scaling where appropriate
* Confusion matrix and classification reports
* Precision, recall, and F1-score evaluation
* Larger and more diverse datasets
* Interactive prediction interface
* REST API for model predictions
* Web-based machine learning dashboard
* Automated model training pipeline
* Model performance comparison
* Data visualization using Matplotlib or Plotly

---

## ⚠️ Disclaimer

This repository is primarily intended for **learning, experimentation, and practical machine learning development**.

The music recommendation model is a demonstration of basic classification and should not be considered a production-grade recommendation system. Its predictions are limited by the size, features, and quality of the training dataset.

---

## 👨‍💻 Author

**Kelvin Kaiseyie**

Bachelor of Computer Science | Full-Stack Development | Cybersecurity | Machine Learning

GitHub: **[@Kelvin-bot-bit](https://github.com/Kelvin-bot-bit)**

---

## ⭐ Acknowledgements

This project was developed as part of practical machine learning studies and experimentation with Python-based data science and machine learning tools.

If you find this project useful, consider giving the repository a ⭐.

