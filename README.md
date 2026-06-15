# Medical Transcript Classifier

An advanced, multi-channel Natural Language Processing (NLP) pipeline designed to automate the categorization of unstructured medical transcripts into distinct clinical specialties. 

By leveraging linguistic preprocessing, dependency parsing for negation detection, and robust machine learning classifiers, this system accurately routes clinical narratives to their respective specialties, streamlining workflows for Electronic Health Records (EHR) and medical auditing.

## 🚀 Features

- **Multi-Channel NLP Pipeline**: Custom text preprocessing using `NLTK` and `spaCy`.
- **Clinical Abbreviation Expansion**: Standardizes medical jargon and shorthand into full clinical terms to ensure semantic consistency.
- **Context-Aware Negation Detection**: Utilizes `spaCy` dependency parsing to identify negated clinical findings (e.g., "no history of chest pain") and adjust feature weights accordingly.
- **Robust Feature Extraction**: Implements TF-IDF vectorization tuned with custom n-grams to capture multi-word clinical phrases.
- **High-Accuracy Classification**: Evaluated using `scikit-learn` algorithms (including optimized Logistic Regression) to classify text into key medical specialties.

## 🩺 Supported Specialties

The classifier is trained to accurately differentiate between major clinical specialties, including but not limited to:
- 🫁 Cardiovascular / Pulmonary
- 🦴 Orthopedic
- 🧪 Gastroenterology
- 🧠 Neurology
- 🤰 Obstetrics / Gynecology

## 🛠️ Tech Stack

- **Language**: Python 3.x
- **NLP Libraries**: `spaCy`, `NLTK`
- **Machine Learning**: `scikit-learn`
- **Data Manipulation**: `pandas`, `numpy`

## 📦 Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/IBasicllyDoWrk/Medical-Transcript-Classifier.git](https://github.com/IBasicllyDoWrk/Medical-Transcript-Classifier.git)
   cd Medical-Transcript-Classifier

2. **Create a virtual environment & activate it:**
```bash
  python -m venv venv
  source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

3. **Install the required dependencies:**
```bash
  pip install -r requirements.txt

3. **Download the necessary NLP language models:**
```bash
  python -m spacy download en_core_web_sm
  python -m nltk.downloader punkt stopwords wordnet
```
## 🖥️ Usage
**Training the Model**
To preprocess the medical dataset, extract features, and train the classifier, run:

```bash
  python train.py
```
**Running Inference**
To classify a new evaluation transcript snippet, you can utilize the inference script:

```bash
  python predict.py --text "Patient presents with acute epigastric pain radiating to the back, aggravated after meals."
```
Output Example:

JSON
{
  "Prediction": "Gastroenterology",
  "Confidence": "0.912"
}

## 📊 Pipeline Architecture
Linguistic Preprocessing: Tokenization, lemmatization, and stop-word removal filtered for medical contexts.

Medical Dictionary Mapping: Dictionary-based lookup to expand common clinical shorthand.

Syntactic Negation Tagging: Dependency trees mark tokens within the scope of a negation modifier.

Vectorization: TF-IDF encoding on the processed clinical text.

Classification: Predictive modeling via optimized linear classifiers.

## 🔮 Future Roadmap
[ ] Transformer Integration: Transition from traditional ML to domain-specific large language models like BioBERT or ClinicalBERT to capture deeper contextual relationships.

[ ] EHR Integration: Develop RESTful API endpoints using Flask/FastAPI for seamless real-time integration into hospital Electronic Health Record systems.

[ ] UI Dashboard: Build a lightweight web interface for clinicians to paste text and instantly view parsed entities and specialty routing.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
