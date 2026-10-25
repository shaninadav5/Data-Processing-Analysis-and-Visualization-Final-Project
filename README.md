# Data-Processing-Analysis-and-Visualization-Final-Project
Data cleaning, exploratory analysis and visualization of 750K podcast episodes to find what drives listening time (pandas, seaborn, SciPy).

# Podcast Listening Time – Data Processing, Analysis & Visualization

An end-to-end data processing and visualization project on 750,000 podcast episodes, exploring which factors drive listening time: episode length, popularity, sentiment, timing and sponsors.

**Notebook:** [`Data_Processing_Analysis_and_Visualization_Final_Project.ipynb`](Data_Processing_Analysis_and_Visualization_Final_Project.ipynb)

---

## The Data

750,000 podcast episodes. Each row describes one episode:

| Feature | Description |
|---|---|
| `Name`, `Event_Number` | Podcast name and episode number |
| `Genre` | e.g. Comedy, True Crime, Education, Technology, Health |
| `Event_Length_minutes` | Episode duration |
| `Host_Popularity_percentage`, `Guest_Popularity_percentage` | Popularity scores |
| `Event_Day`, `Publication_Time` | Day of week and time of day (Morning / Afternoon / Evening / Night) |
| `Number_of_Sponsers` | Number of sponsors / ads |
| `Event_Sentiment` | Positive / Neutral / Negative |
| **`Watch_Time_minutes`** | **Target:** how long listeners actually listened |

## Workflow

1. **Initial statistics:** summary statistics, data types, and missing values. Guest popularity was missing in about 19% of rows and episode length in about 11%.
2. **Data cleaning:**
   - Filled missing values with median and mean imputation.
   - Removed text from numeric fields (e.g. the "Episode" prefix in episode numbers).
   - Capped outliers with the IQR method.
   - Fixed data integrity issues.
3. **Normalization:** Z-score standardization of all numeric variables, so they can be compared on the same scale.
4. **Statistical analysis:** distributions and normality checks (Shapiro–Wilk), and Pearson correlations with watch time.
5. **Visualization:** distributions, correlation heatmaps, and comparisons of watch time across genres, sentiment, publication time and number of sponsors.

## Key Findings

- **Episode length is the decisive factor.** It has a very strong positive correlation (about 0.87) with watch time, so listeners are not put off by long episodes.
- **Popularity matters little.** Host and guest popularity have very little effect on listening time; content outweighs "big names".
- **Sentiment and timing matter.** Positive episodes hold listeners better than negative ones, and evening and night releases perform better than morning releases.
- **Too many ads hurt.** The number of sponsors is negatively correlated with watch time, which suggests heavy advertising causes listeners to drop off.

---

## Tools & Libraries

Python, pandas, NumPy, Matplotlib, seaborn, SciPy, scikit-learn

## How to Run

The notebook was written for **Google Colab** and is saved with its outputs, so you can read the full analysis directly on GitHub.

To run it yourself:
1. Open the notebook in [Google Colab](https://colab.research.google.com/).
2. Run the first cell. It opens a file picker; upload the dataset CSV (`train-2.csv`).
3. Click **Runtime → Run all**.
