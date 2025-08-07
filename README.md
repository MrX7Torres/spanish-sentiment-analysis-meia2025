# 🧠 MeIA 2025 - Sentiment Analysis on Mexican Tourism Reviews 🇲🇽

This project was developed for the MeIA 2025 macrotraining challenge on sentiment analysis, focused on tourist reviews from Mexico's *Pueblos Mágicos*.  
The goal is to classify reviews into 5 sentiment classes: from **very negative (0)** to **very positive (4)**.

## 📁 Dataset

| File                          | Description                                         |
|-------------------------------|-----------------------------------------------------|
| `MeIA_2025_train.xlsx`        | Labeled dataset (5,000 reviews with polarity scores)|
| `MeIA_2025_test_wo_labels.xlsx` | Unlabeled dataset (2,500 reviews)                  |

Each review contains:
- `Review`: Text of the tourist comment
- `Polarity`: Sentiment label (1 to 5)
- `Town`, `Region`, `Type`: Metadata for context

## 🧪 Methodology

- Data cleaning and filtering of useful columns
- Stratified `train_test_split`
- Custom label mapping: `1 → 0`, `2 → 1`, ..., `5 → 4`
- Tried multiple pre-trained Spanish models:
  - ❌ `dccuchile/bert-base-spanish-wwm-cased`
  - ❌ `beto-sentiment-analysis`
  - ✅ `UMUTeam/roberta-spanish-sentiment-analysis` (best results)
- Used HuggingFace Transformers with:
  - Batch size: 32
  - Learning rate: 3e-5
  - Epochs: 12
  - Evaluation every 200 steps
  - EarlyStoppingCallback (patience = 2)
  - F1-score as the main metric
- Final predictions saved to `.txt` for submission

## 📊 Metrics

Evaluation metrics used:
- Accuracy
- F1 Score
- Precision
- Recall
- `classification_report` by class

## 🚀 Tools & Libraries

- `transformers`
- `datasets`
- `sklearn`
- `pandas`
- `matplotlib`
- `openpyxl`

## 🧠 Team

Developed by:
- Jesús Antonio Torres Contreras

## 📄 License

MIT License – see [`LICENSE`](./LICENSE)
