# Milestone 2 Exploration

## Dataset Link
We use **The Movies Dataset** from Kaggle:  
https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset

This dataset contains metadata on over 45,000 films and 26 million ratings from TMDB. This includes information on cast, crew, budget, revenue, genres, release dates, and user ratings.

---

## Environment Setup

Python 3.10 and beyond.

### pip + venv example
```bash
python3 -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install pandas numpy matplotlib tqdm scikit-learn
```

You will also need a Kaggle account to download.


## Preprocessing Plan

- **Fix data types**: Ensure budget, revenue, runtime, popularity, and vote counts are numeric.  
- **Log transforms**: Apply to skewed variables like budget and revenue.  
- **Feature engineering**:  
  - Extract release year, month, quarter.  
  - Parse genres, cast, crew into usable categories.  
  - Compute ROI = revenue / budget.  
- **Handle missing values**: Fill runtime with median, replace missing categorical values with "Unknown".  
- **Target definition**:  
  - Regression target: revenue or ROI.  
  - Classification target: success = ROI ≥ 1 and vote_average ≥ 6.  
- **Outliers**: Cut extreme values out after log transform.


## Milestone 3

For this milestone we finished the main preprocessing steps:
- Converted numeric columns to numbers and filled missing values.
- ROI, log of budget/revenue, release year/month/quarter
- One-hot encoded top languages and genres
- Scaled numeric features with z-score

Our first model was an SVM RBF.  
- Smaller C values underfit 
- Larger C values overfit
- balance was at C = 1.  
- Overall accuracy on the test set was good