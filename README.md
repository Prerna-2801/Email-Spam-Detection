### Email Spam Detection

A production-style Machine Learning pipeline that classifies email into spam or ham (legitimate).

### Project Architecture

The system processes raw text inputs through a modular, isolated pipeline designed to eliminate data leakage: 

1. **Exploratory Data Analysis (EDA):** Dropped 415 duplicate rows, analyzed class distribution (4,516 Ham vs. 641 Spam), and encoded categorical text labels to numeric values (Ham: 0, Spam: 1).
2. **Data Splitting:** Divided the corpus into an 80/20 train/test split using stratified sampling to maintain identical class ratios across subsets.
3. **Text Preprocessing (NLTK):** Cleaned text features independently by applying lowercasing, alphanumeric regex filtering, tokenization, English stop-word removal, and WordNet lemmatization.
4. **Vectorization:** Vectorized clean text arrays using Scikit-Learn's TfidfVectorizer (fitting vocabulary strictly on the training partition).
5. **Model Training:** Trained a Multinomial Naive Bayes classifier on the resulting text-math matrices.

### Model Performance Evaluation

The model was tested against a completely hidden test partition of 1,032 emails, yielding the following performance metrics: 

* **Overall Accuracy:** 96.22%
* **Spam Precision:** 1.00 (100%) — Zero False Positives recorded. Legitimate communication is structurally protected from being incorrectly classified as junk.
* **Spam Recall:** 0.70 (70%) — The model successfully caught 89 out of 128 spam messages.

### Confusion Matrix

text

[[904   0]  <- [True Ham,  False Spam]
 [ 39  89]] <- [False Ham, True Spam]

Use code with caution.

### How To Run

1. Clone this repository:

bash

git clone https://github.com/your-username/email-spam-detector.git
cd email-spam-detector

Use code with caution.

1. Install the necessary library dependencies:

bash

pip install -r requirements.txt

Use code with caution.

1. Open and run the Jupyter Notebook to train the model and test live custom email inference:

bash

jupyter notebook notebooks/spam_detection.ipynb
