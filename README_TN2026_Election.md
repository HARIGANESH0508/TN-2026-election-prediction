# 🗳️ Tamil Nadu 2026 Election Prediction

![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> A machine learning pipeline that predicts Tamil Nadu 2026 State Assembly Election outcomes using historical data (1971–2021), anti-incumbency patterns, TVK vote-split modelling, and social/news sentiment analysis.

---

## 📌 Project Highlights

- ✅ Predicts seat distribution for DMK, AIADMK, TVK, BJP, PMK, INC, VCK
- ✅ Fixes the "same as last election" problem using 3 real-world correction factors
- ✅ Blends ML predictions with anti-incumbency rules and sentiment scores
- ✅ Generates a 4-panel visualization chart

---

## 🧠 The Key Fix — Why 2026 ≠ 2021

A pure ML model trained on historical data tends to predict incumbents win again. Tamil Nadu has a unique pattern — the ruling party has lost **9 out of 10** state elections. Three correction layers are applied:

| Factor | Description |
|--------|-------------|
| **Anti-incumbency** | DMK constituencies with margin < 15,000 flagged as HIGH swing risk |
| **TVK vote-split** | New party draws ~31.7% survey support, redistributing votes in 100+ urban seats |
| **Sentiment weight** | Social media + news sentiment scores blended as a seat-count multiplier |

---

## 📁 Project Structure

```
TN-2026-election-prediction/
├── TN_2026_FIXED_NOTEBOOK.ipynb       # Main notebook
├── TN_Assembly_1971_2021_Combined.csv # Historical election data
├── requirements.txt
├── README.md
└── outputs/
    └── 2026_prediction_chart.png
```

---

## 🚀 Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/TN-2026-election-prediction.git
cd TN-2026-election-prediction

# 2. Install dependencies
pip install -r requirements.txt

# 3. Open and run the notebook
jupyter notebook TN_2026_FIXED_NOTEBOOK.ipynb
```

> Run all cells top to bottom. The 4-panel chart will be saved to `outputs/`.

---

## 📊 Model Pipeline

```
Step 1  → Import libraries
Step 2  → Load historical CSV (1971–2021)
Step 3  → Clean numeric columns
Step 4  → Extract constituency-level winners
Step 5  → Feature engineering (lag features, incumbency flag)
Step 6  → Label-encode party names
Step 7  → Assemble model matrix
Step 8  → Train Random Forest + Gradient Boosting on pre-2021 data
Step 9  → Validate on 2021 actuals → select best model
Step 10 → Apply anti-incumbency correction
Step 11 → Blend social + news sentiment scores
Step 12 → Generate 4-panel output chart
Step 13 → Print methodology explanation
```

---

## 📈 Features Used

| Feature | Description |
|---------|-------------|
| `Prev_Margin` | Vote margin of previous winner in this constituency |
| `Prev_WinPct` | Win percentage of previous winner |
| `Prev_Party_Code` | Integer-encoded previous winning party |
| `Incumbent` | 1 if same party retained seat, else 0 |
| `Prev_Seats` | Total seats won by party in previous election |
| `Prev_Win_Streak` | Consecutive wins by same party in this constituency |
| `Is_Ruling_Party` | 1 if party was in state government (anti-incumbency signal) |

---

## 🎯 Model Results (2021 Validation)

| Model | Constituency Accuracy |
|-------|-----------------------|
| Random Forest | ~65% |
| Gradient Boosting | ~63% |

> Note: State-level seat totals are more meaningful than per-constituency accuracy for election prediction.

---

## 📉 Sentiment Scores Used

| Party | Social Score | Tweets |
|-------|-------------|--------|
| TVK | +0.4672 | 2,254 |
| BJP | +0.3913 | 23 |
| AIADMK | +0.0476 | 105 |
| DMK | −0.1500 | est. |

---

## 🛠️ Requirements

```
pandas
numpy
scikit-learn
matplotlib
```

Install with:
```bash
pip install -r requirements.txt
```

---

## 📂 Data Source

Historical Tamil Nadu Assembly Election data (1971–2021) compiled from Election Commission of India records.

---

## 👤 Author

**Hari Ganesh**
- Course: Machine Learning
- 📧 [your email here]
- 🔗 [LinkedIn profile here]

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

---

## ⚠️ Disclaimer

This project is for educational and research purposes only. Predictions are based on historical patterns and may not reflect actual election outcomes.
