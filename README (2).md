# RISE26 AI Behavioral Analysis

A data science project that analyzes AI-related news headlines to uncover sentiment trends, behavioral influence patterns, and topic clusters across thousands of media sources.

---
## What This Project Does

This notebook ingests a large dataset of AI news headlines and runs a full analytical pipeline:

- **Sentiment Analysis** — Classifies each headline as Positive, Negative, or Neutral using VADER
- **Behavioral Influence Score (BIS)** — A custom composite metric that scores headlines based on sentiment intensity, punctuation density, word complexity, and agency framing (human vs AI subjects)
- **Topic Modeling** — Runs Latent Dirichlet Allocation (LDA) to discover 10 recurring themes across headlines
- **Class Analysis** — Breaks down coverage by AI topic category (e.g. robotics, ethics, regulation)
- **Statistical Testing** — Mann-Whitney U tests to compare weekend vs. weekday sentiment and BIS
- **Visualizations** — 7 charts covering volume trends, word clouds, top sources, BIS trends, and more

---

## Project Structure

```
RISE26_AI_Behavioral_Analysis/
│
├── RISE26_AI_Behavioral_Analysis.ipynb   # Main analysis notebook
├── dataset_A.csv                          # Dataset (auto-downloaded by notebook)
├── README.md                              # This file
├── .gitignore                             # Excludes checkpoints, cache, venv
│
└── outputs/                               # Generated after running the notebook
    ├── top_sources.png
    ├── bis_weekly_trend.png
    ├── bis_by_class.png
    ├── bis_by_source.png
    ├── agency_vs_emotion.png
    ├── class_distribution.png
    └── analysis_summary.json
```

---

## Requirements

- Python 3.8+
- Jupyter Notebook or Google Colab

All Python packages are installed automatically when you run the first cell:

```
pandas, numpy, matplotlib, seaborn, plotly,
nltk, wordcloud, scikit-learn, scipy, gdown
```

---

## How to Run

### Option A — Google Colab (easiest, no setup needed)

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Upload notebook** and select `RISE26_AI_Behavioral_Analysis.ipynb`
3. Click **Runtime → Run all**
4. The dataset downloads automatically — no manual steps needed

### Option B — Run Locally with Jupyter

1. Clone the repo:
   ```bash
   git clone https://github.com/YOUR_USERNAME/RISE26_AI_Behavioral_Analysis.git
   cd RISE26_AI_Behavioral_Analysis
   ```

2. (Optional but recommended) Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate        # Mac/Linux
   venv\Scripts\activate           # Windows
   ```

3. Launch Jupyter:
   ```bash
   jupyter notebook
   ```

4. Open `RISE26_AI_Behavioral_Analysis.ipynb` and click **Kernel → Restart & Run All**

---

## Key Outputs

| Output | Description |
|---|---|
| `analysis_summary.json` | Key metrics: total headlines, sentiment breakdown, top source, top class |
| `top_sources.png` | Bar chart of the 15 most active news sources |
| `bis_weekly_trend.png` | Weekly average Behavioral Influence Score over time |
| `bis_by_class.png` | BIS distribution across the top 10 AI topic categories |
| `bis_by_source.png` | Top 15 sources ranked by mean BIS |
| `agency_vs_emotion.png` | Scatter plot of human-vs-AI agency framing against emotional intensity |

---

## Dataset

The dataset (`dataset_A.csv`) is downloaded automatically from Google Drive when you run Cell 2. It contains AI-related news headlines with the following fields:

| Column | Description |
|---|---|
| `date` | Publication date |
| `title` | Headline text |
| `source` | News outlet |
| `classes_str` | AI topic categories |
| `number_of_words_title` | Word count of headline |
| `day_of_week`, `month`, `year`, `quarter` | Time features |
| `is_weekend` | Boolean flag |

---

## Methodology

### Behavioral Influence Score (BIS)

BIS is a custom composite metric computed from four z-scored components:

| Component | What it measures |
|---|---|
| Sentiment intensity | Absolute VADER compound score |
| Punctuation density | Ratio of punctuation characters to total characters |
| Avg word length | Proxy for cognitive complexity |
| Agency balance | Human mentions minus AI mentions in headline |

Components are standardized and combined into a weighted score.

### Topic Modeling

LDA is run on cleaned headline text with 10 topics, using a vocabulary of up to 1,000 terms (min doc frequency: 5, max doc frequency: 70%).

---

## Notes

- The notebook clears warnings for cleaner output — this is intentional
- Runtime is typically 3–8 minutes depending on dataset size and machine
- If the `gdown` download fails, manually place `dataset_A.csv` in the same folder as the notebook

---

## License

This project was created for the RISE26 competition. All analysis code is original.
