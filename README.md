# SENTIMENT-ANALYSIS

Classifies airline tweets into Positive / Neutral / Negative
using TF-IDF + Logistic Regression (76.9% accuracy) and BERT
transformer. Features Aspect-Based Sentiment Analysis (ABSA)
for granular complaint routing.

## 🔍 What Makes This Unique
- **Dual Model System** — TF-IDF + LR vs BERT with smart
  conflict resolution (BERT overrides TF-IDF on negation)
- **WordCloud** — visual word drivers per sentiment class
- **Airline × Complaint Heatmap** — which airline gets
  which complaint type most
- **Airline Brand Scorecard** — ranks all 6 airlines by
  sentiment score
- **ABSA** — per-aspect sentiment (food, staff, punctuality,
  baggage, comfort, booking) with business routing
- **Live Prediction** — free text input with dual model
  comparison + final decision logic

## 📊 Dataset
Twitter US Airline Sentiment — 14,640 real tweets
3 classes: Negative (63%) · Neutral (21%) · Positive (16%)

## 🛠️ Tech Stack
Python · Scikit-learn · XGBoost · TF-IDF · BERT ·
Transformers · WordCloud · Matplotlib · Seaborn

## 📁 Project Structure
| File | Description |
|------|-------------|
| `Twitter_Sentiment_Analysis_v1.ipynb` | Full notebook |
| `requirements.txt` | Dependencies |

## 🔍 Key Sections
| # | Section | What it does |
|---|---------|-------------|
| 1 | Libraries | All imports |
| 2 | Load Dataset | Tweets.csv from Kaggle |
| 3 | EDA | 6 charts — distribution, airline, confidence |
| 4 | Complaint Heatmap | Airline × Reason matrix |
| 5 | Text Cleaning | Remove mentions, URLs, punctuation |
| 6 | WordCloud | Word drivers per sentiment class |
| 7 | TF-IDF | 10,000 features, unigrams + bigrams |
| 8 | Model Comparison | NB, LR, RF, XGBoost |
| 9 | Confusion Matrix | Counts + percentage heatmap |
| 10 | Hyperparameter Tuning | RandomizedSearchCV |
| 11 | BERT | distilbert — zero-shot comparison |
| 12 | Brand Scorecard | Airline sentiment ranking |
| 13 | Live Prediction | Dual model + conflict resolution |
| 14 | ABSA | Per-aspect sentiment + routing |

## 📈 Results
| Model | Accuracy |
|-------|----------|
| Naive Bayes | ~72% |
| Logistic Regression (tuned) | **76.9%** |
| Random Forest | ~74% |
| XGBoost | ~75% |
| BERT (zero-shot) | ~72-75% |

## 🔑 Key Insights
- Negative tweets dominate — 63% of all airline tweets
- United Airlines has worst sentiment score
- Virgin America has best sentiment score
- Top complaints: Customer Service · Late Flights · Lost Baggage
- TF-IDF fails on negation ("not great") — BERT handles correctly
- Simple TF-IDF beats large BERT when domain-matched

## 🤖 ABSA Aspects
| Aspect | Keywords | Routes To |
|--------|----------|-----------|
| ⏱️ Punctuality | delay, cancel, late | Operations |
| 🍽️ Food | meal, drink, snack | Catering |
| 👨‍✈️ Staff | crew, rude, helpful | HR/Training |
| 🧳 Baggage | lost, luggage, bag | Baggage team |
| 💺 Comfort | seat, legroom, cramped | Cabin crew |
| 📱 Booking | app, website, checkin | IT/Support |

## 👤 Author
**KAVIN VENKAT**
[LinkedIn](www.linkedin.com/in/kavin-venkat-1710s0202) 
