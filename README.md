# ✈️ Twitter Airline Sentiment Analysis

Classifies airline tweets into Positive / Neutral / Negative using TF-IDF + Logistic Regression (76.9% accuracy) and BERT transformer. Features Aspect-Based Sentiment Analysis (ABSA), SQL Brand Analysis, WordCloud, Airline Brand Scorecard, and a live dual-model prediction system.

## 🔍 What Makes This Unique
- **Dual Model System** — TF-IDF + LR vs BERT with smart conflict resolution (BERT overrides TF-IDF on negation — "not great" → NEGATIVE)
- **ABSA** — Aspect-Based Sentiment Analysis using clause splitting + BERT. Routes complaints to correct department (food → Catering, staff → HR, baggage → Baggage team)
- **SQL Brand Analysis** — Airline scorecard, complaint routing, confidence analysis using CTEs and PARTITION BY window functions
- **WordCloud** — visual word drivers per sentiment class (Negative / Neutral / Positive)
- **Airline × Complaint Heatmap** — which airline gets which complaint type most
- **Airline Brand Scorecard** — ranks all 6 airlines by sentiment score with stacked chart
- **Live Prediction** — free text input with dual model comparison + final decision logic

## 📊 Dataset
Twitter US Airline Sentiment — 14,640 real tweets · 3 classes
Negative: 63% · Neutral: 21% · Positive: 16%

## 🛠️ Tech Stack
Python · Scikit-learn · XGBoost · TF-IDF · BERT · Transformers · WordCloud · SQLite · Matplotlib · Seaborn

## 📁 Project Structure
| File | Description |
|------|-------------|
| `sentimnet-analysis.ipynb` | Full notebook |
| `requirements.txt` | Dependencies |

## 🔍 Key Sections
| # | Section | What it does |
|---|---------|-------------|
| 1 | Libraries | All imports |
| 2 | Load Dataset | Tweets.csv from Kaggle |
| 3 | EDA | 6 charts — distribution, airline, confidence |
| 3b | SQL Brand Analysis | Scorecard · complaints · confidence bands |
| 4 | Complaint Heatmap | Airline × Negative Reason matrix |
| 5 | Text Cleaning | Remove @mentions, URLs, punctuation |
| 6 | WordCloud | Word drivers per sentiment class |
| 7 | TF-IDF | 10,000 features · unigrams + bigrams |
| 8 | Model Comparison | NB · LR · RF · XGBoost |
| 9 | Confusion Matrix | Counts + percentage heatmap |
| 10 | Hyperparameter Tuning | RandomizedSearchCV on TF-IDF + LR |
| 11 | BERT | distilbert zero-shot comparison |
| 12 | BERT vs TF-IDF | 300-tweet accuracy comparison |
| 13 | Brand Scorecard | Airline sentiment ranking + charts |
| 14 | Live Prediction | Dual model + conflict resolution |
| 15 | ABSA | Per-aspect sentiment + department routing |

## 📈 Model Results
| Model | Accuracy |
|-------|----------|
| Naive Bayes | ~72% |
| **Logistic Regression (Tuned)** | **76.9%** |
| Random Forest | ~74% |
| XGBoost | ~75% |
| BERT (zero-shot) | ~72-75% |

## 🗄️ SQL Highlights
```sql
-- Top 3 Complaints per Airline (PARTITION BY + RANK)
WITH complaint_ranked AS (
    SELECT airline, negativereason, COUNT(*) AS complaints,
        RANK() OVER (
            PARTITION BY airline
            ORDER BY COUNT(*) DESC
        ) AS complaint_rank
    FROM tweets
    WHERE airline_sentiment = 'negative'
    GROUP BY airline, negativereason
)
SELECT * FROM complaint_ranked WHERE complaint_rank <= 3
```

## 🤖 ABSA Aspects
| Aspect | Keywords | Routes To |
|--------|----------|-----------|
| ⏱️ Punctuality | delay, cancel, late | Operations |
| 🍽️ Food | meal, drink, snack | Catering |
| 👨‍✈️ Staff | crew, rude, helpful | HR/Training |
| 🧳 Baggage | lost, luggage, bag | Baggage team |
| 💺 Comfort | seat, legroom, cramped | Cabin crew |
| 📱 Booking | app, website, checkin | IT/Support |

## 🔑 Key Insights
- Negative tweets dominate — 63% of all airline tweets
- United Airlines has worst sentiment score
- Virgin America has best sentiment score
- Top complaints: Customer Service · Late Flights · Lost Baggage
- TF-IDF fails on negation ("not great") — BERT handles correctly
- Domain-matched TF-IDF beats large zero-shot BERT



## 👤 Author
**KAVIN VENKAT**
[LinkedIn](www.linkedin.com/in/kavin-venkat-1710s0202) 
