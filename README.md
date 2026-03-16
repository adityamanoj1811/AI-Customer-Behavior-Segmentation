# 🔍 AI-Based Customer Behavior Segmentation for Web Analytics

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)](https://python.org)
[![Platform](https://img.shields.io/badge/Platform-Google%20Colab-orange?logo=googlecolab)](https://colab.research.google.com)
[![Dataset](https://img.shields.io/badge/Dataset-GA4%20BigQuery-green?logo=googlebigquery)](https://console.cloud.google.com)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen)]()

> A complete end-to-end AI-based customer behavior segmentation system using real-world web analytics data from Google Analytics 4 (GA4) BigQuery public dataset.

---

## 📌 Project Overview

This project segments **269,542 web users** from the Google Merchandise Store into distinct behavioral groups using multiple unsupervised and supervised machine learning algorithms. The system can predict which segment any new web visitor belongs to in real time with **98.61% accuracy**.

### Key Results

| Metric | Value |
|--------|-------|
| Total Users Segmented | 269,542 |
| Final Segments | 3 |
| Silhouette Score | 0.4622 |
| Classifier Accuracy | 98.61% |
| PCA Variance Retained | 91.53% |
| Clustering Algorithms | 4 (K-Means, DBSCAN, Hierarchical, GMM) |

---

## 🗂️ Repository Structure

```
AI-Customer-Behavior-Segmentation/
│
├── 📓 AI_Customer_Behavior_Segmentation_GA4_COLAB.ipynb   ← Main notebook
├── 📊 requirements.txt                                     ← Dependencies
├── 📄 README.md                                            ← This file
├── 📄 LICENSE                                              ← MIT License
├── 📄 .gitignore                                           ← Git ignore rules
│
├── 📁 docs/
│   ├── project_report.pdf                                  ← Full project report
│   └── architecture.png                                    ← Pipeline diagram
│
└── 📁 sample_outputs/
    ├── eda_distributions.png
    ├── eda_funnel.png
    ├── eda_correlation.png
    ├── optimal_k.png
    ├── silhouette.png
    ├── umap.png
    ├── tsne.png
    ├── radar.png
    ├── segment_dashboard.png
    ├── feature_importance.png
    ├── model_evaluation.png
    └── gmm_clustering.png
```

---

## 📊 Dataset

| Property | Details |
|----------|---------|
| **Name** | GA4 Obfuscated Sample Ecommerce |
| **Source** | `bigquery-public-data.ga4_obfuscated_sample_ecommerce` |
| **Period** | November 1, 2020 – January 31, 2021 (92 days) |
| **Store** | Google Merchandise Store |
| **Events** | page_view, scroll, view_item, add_to_cart, begin_checkout, purchase |
| **Access** | Free via Google BigQuery Sandbox |

---

## 🤖 AI & ML Techniques

| # | Technique | Type | Purpose |
|---|-----------|------|---------|
| 1 | **PCA** | Dimensionality Reduction | 21 → 11 features, 91.53% variance retained |
| 2 | **K-Means** | Unsupervised Clustering | Primary segmentation algorithm |
| 3 | **DBSCAN** | Density-Based Clustering | Outlier detection + cluster confirmation |
| 4 | **Agglomerative** | Hierarchical Clustering | Dendrogram + cluster validation |
| 5 | **GMM** | Probabilistic Clustering | Soft assignments + uncertainty mapping |
| 6 | **UMAP** | Non-linear Reduction | 2D cluster visualization |
| 7 | **t-SNE** | Non-linear Reduction | Cluster separation validation |
| 8 | **Random Forest** | Supervised Classification | Real-time segment prediction |
| 9 | **RFM Analysis** | Statistical Scoring | Recency, Frequency, Monetary scoring |

---

## 👥 Customer Segments Discovered

### Cluster 0 — Engaged Non-Converters (37,218 users — 13.8%)
- Regular visitors who never complete a purchase
- High session count and page views
- Strong add-to-cart behavior but zero conversions
- **Strategy:** Cart abandonment emails, 10% discount triggers, trust signals

### Cluster 1 — High-Value Buyers (3,833 users — 1.4%)
- Premium segment driving 100% of revenue
- Average revenue $61.87 per user
- 55%+ conversion rate, 17+ pages per session
- **Strategy:** VIP loyalty program, personalized recommendations, early access

### Cluster 2 — Casual Shoppers (228,491 users — 84.8%)
- Passive majority with minimal engagement
- Balanced but low values across all behavioral features
- 95%+ are new users with single sessions
- **Strategy:** Welcome popup, best-seller showcase, brand awareness campaigns

---

## 🔄 Project Pipeline

```
GA4 BigQuery Data (270,154 users)
          ↓
Feature Engineering (21 behavioral features)
          ↓
Log Transform + StandardScaler
          ↓
PCA (21 → 11 dimensions, 91.53% variance)
          ↓
┌─────────────────────────────────────┐
│  4 Clustering Algorithms            │
│  ├── K-Means      (silhouette 0.462)│
│  ├── DBSCAN       (3 clusters found)│
│  ├── Hierarchical (silhouette 0.521)│
│  └── GMM          (probabilistic)   │
└─────────────────────────────────────┘
          ↓
3 Segments confirmed by all algorithms
          ↓
UMAP + t-SNE Visualization
          ↓
Random Forest Classifier (98.61% accuracy)
          ↓
┌─────────────────────────────────────┐
│  Prediction Engine                  │
│  ├── Single user prediction         │
│  ├── Batch prediction (CSV)         │
│  ├── Confidence scores              │
│  └── What-If simulator              │
└─────────────────────────────────────┘
```

---

## 🗒️ Notebook Sections

| Section | Description |
|---------|-------------|
| 1 | Install Libraries |
| 2 | Google Authentication |
| 3 | Project Configuration |
| 4 | Data Extraction from BigQuery |
| 5 | Data Overview & Schema |
| 6 | Exploratory Data Analysis (4 charts) |
| 7 | Data Cleaning & Preprocessing |
| 8 | Feature Engineering (21 features) |
| 9 | RFM Analysis |
| 10 | PCA Dimensionality Reduction |
| 11 | Finding Optimal K (Elbow + Silhouette + DB + CH) |
| 12 | K-Means Clustering |
| 13 | DBSCAN Clustering |
| 14 | Agglomerative Hierarchical Clustering |
| 15 | UMAP & t-SNE Visualization |
| 16 | Cluster Profiling & Segment Labeling |
| 17 | Segment Dashboard (6 charts) |
| 18 | Random Forest Classifier |
| 19 | Model Evaluation |
| 20 | Feature Importance |
| 21 | Final Report & Marketing Recommendations |
| + | GMM Clustering |
| + | K=3 vs K=4 vs K=5 Comparison |
| + | Prediction Engine (5 cells) |

---

## ⚙️ Setup & Usage

### Prerequisites
- Google Account
- Google Cloud Platform project (free)
- BigQuery API enabled

### Step 1 — Open in Google Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

Click the badge above or go to [colab.research.google.com](https://colab.research.google.com) and upload the notebook.

### Step 2 — Authenticate
When Section 2 runs, click the Google login link and sign in with your GCP account.

### Step 3 — Set Project ID
In Section 3, replace:
```python
PROJECT_ID = "YOUR_GCP_PROJECT_ID"
```
Find your project ID at [console.cloud.google.com](https://console.cloud.google.com).

### Step 4 — Run All
```
Runtime → Run All
```
The notebook handles everything automatically. BigQuery results are cached after the first run.

### Step 5 — Download Outputs
After completion, download from the Colab Files panel:
```
/content/rf_segment_classifier.pkl
/content/scaler.pkl
/content/pca.pkl
/content/ga4_segmentation_results.csv
/content/segment_report.csv
/content/batch_predictions.csv
```

---

## 📦 Dependencies

```txt
# Install in Colab (only these 3 needed — rest are pre-installed)
umap-learn==0.5.7
xgboost==2.1.3
plotly==5.24.1

# Pre-installed on Colab
pandas, numpy, scikit-learn, matplotlib, seaborn
scipy, joblib, pyarrow, google-cloud-bigquery
```

---

## 📈 Key Findings

### Conversion Funnel Drop-off
```
Sessions        → Page Views    :  0.1% drop
Page Views      → Product Views : 77.3% drop  ← Critical gap
Product Views   → Add to Cart   : 79.5% drop  ← Critical gap
Add to Cart     → Checkout      : 22.6% drop
Checkout        → Purchase      : 54.5% drop
```
Only **1.6% of users** (4,419 out of 270,154) completed a purchase.

### Top 5 Features for Segment Prediction
```
1. conversion_rate        (0.1375) — strongest behavioral signal
2. total_items_purchased  (0.1370) — purchase depth
3. total_pageviews        (0.1133) — browsing volume
4. purchase_count         (0.1053) — buying frequency
5. total_revenue          (0.0975) — monetary value
```

### Device & Channel Insights
- Device type has near-zero importance for segmentation
- Traffic channel has near-zero importance for segmentation
- **What users DO on the site matters far more than how they arrived**

---

## 🎯 Marketing Recommendations

| Segment | Priority | Key Actions |
|---------|----------|-------------|
| High-Value Buyers | 🟢 RETAIN | VIP loyalty program, personalized recommendations |
| Engaged Non-Converters | 🔵 CONVERT | Cart abandonment emails, trust signals, retargeting |
| Casual Shoppers | ⚪ NURTURE | Welcome popup, best-sellers, brand awareness |

---

## 👨‍💻 Authors

**Aditya Manoj** — Data Engineering, BigQuery SQL, ML Pipeline, EDA, Visualization, Business Analysis 
---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- **Google** for the GA4 BigQuery public dataset
- **Scikit-learn** for clustering and classification algorithms
- **UMAP-learn** for dimensionality reduction visualization
- **Plotly** for interactive visualizations

---

*Built with ❤️ using Google Colab + BigQuery + Python*
