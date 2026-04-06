# 🧠 Palestinian Dialect-Aware Mental Health Detection using MARBERT

An advanced NLP framework designed to classify mental health indicators in Arabic social media posts, with a specific focus on the **Palestinian Dialect** and **Conflict-Zone contexts** (e.g., Gaza). By leveraging **MARBERT** and a custom-built dialect conversion pipeline, this project achieves a **~91% Macro F1-score**.

---

## 🚀 Key Highlights
* **Dialect-Aware**: Custom pipeline to convert Modern Standard Arabic (MSA) to Palestinian Dialect, handling complex grammar, negation, and verb roots.
* **Contextualized Data**: Integration of 6,100+ samples specifically reflecting mental health in conflict zones (generated via GPT-4 and Data Augmentation).
* **State-of-the-Art Model**: Fine-tuned **MARBERT** (Multi-dialectal Arabic BERT) optimized for social media text.
* **High Performance**: Outperformed baseline models and raw MSA models with an overall accuracy of **90.97%**.

---

## 🛠️ Methodology & Pipeline

### 1. Data Acquisition & Enrichment
- **Source**: Comprehensive dataset from Kaggle (51,000 samples) covering Stress, Anxiety, Suicidal thoughts, and Depression.
- **Translation**: High-fidelity translation from English to MSA using Google Translate API (outperforming MarianMT and MBart).
- **Augmentation**: Added 4,100 conflict-context samples and 2,000 augmented samples (Random Swap/Deletion/Insertion) to ensure model robustness in crisis scenarios.

### 2. The Palestinian Dialect Converter 🇵🇸
A sophisticated rule-based engine developed to handle:
- **Negation**: Converting standard "لم" to dialectal forms while preserving verb conjugation.
- **Verb Roots**: Specialized handling for "Wanting" verbs (أراد/بغى → بدو) and attached pronouns.
- **Contextual Replacement**: Male/Female name datasets to ensure correct gender-based verb conversion.
- **Lexical Mapping**: Two-tier dictionaries for standalone words and compound terms (e.g., أليس كذلك ← مش هيك).

### 3. Preprocessing & Normalization
- Removal of URLs, Mentions, Hashtags, and Tatweel.
- Letter Normalization (ة/ه → ه, أ/إ/آ → ا, etc.).
- Repeating Madd removal for noise reduction.

---

## 📂 Repository Structure

| File/Folder | Description |
| :--- | :--- |
| **`Dialect_Translation.ipynb`** | The core engine for MSA to Palestinian dialect conversion. |
| **`Copy_of_Model_Training.ipynb`** | Fine-tuning MARBERT with various hyperparameter runs. |
| **`Mental_Health_Dataset_Cleaning.ipynb`** | Preprocessing, normalization, and noise removal. |
| **`Base_line_model.ipynb`** | Logistic Regression implementation used for performance benchmarking. |
| **`Macro_metrics.ipynb`** | Detailed evaluation (Precision, Recall, F1) using Macro averaging. |
| **`Model_Usage.ipynb`** | Guide on how to load and use the trained model for inference. |
| **`Moroccan_Darija_Dialect/`** | Extension of the project to handle the Moroccan dialect extreme. |

---

## 📈 Results

| Metric | Baseline (LogReg) | **Fine-tuned MARBERT** |
| :--- | :---: | :---: |
| **Accuracy** | ~ | **90.97%** |
| **Precision (Macro)**| ~ | **91.63%** |
| **Recall (Macro)** | ~ | **91.19%** |
| **F1-Score (Macro)** | ~ | **91.34%** |

**Impact of Dialect Conversion:**
The inclusion of the Palestinian dialect converter and conflict-specific data improved the F1-score by **+1.36%** and accuracy by **+1.83%** compared to raw MSA models.

---


## 📝 References
1. **Abu Kwaik et al. (2018)**: Lexical distance study of Arabic dialects.
2. **Mental Health Dataset**: [Kaggle Source](https://www.kaggle.com/datasets/szegeelim/mental-health).
3. **MARBERT**: Multi-dialectal Arabic BERT for social media.
