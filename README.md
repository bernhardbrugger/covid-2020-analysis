# Covid-19 in Spring 2020: Curve Fitting & Time-Series Clustering

> Hand-written data science from March–May 2020, done while the first wave was still unfolding. No agents, no copilots: just pandas, scipy, scikit-learn and tslearn.

📓 **[Open the notebook](covid_spring_2020.ipynb)** (all outputs and plots are included, so you can read it without running anything)

## What it does

| Part | Method |
|---|---|
| Data cleaning | Fixing missing ISO codes and dtypes in the ECDC worldwide case data |
| Country curves | Daily and cumulative infections and deaths, country vs. country, country vs. China |
| First-wave forecast | Logistic curve fit (`scipy.optimize.curve_fit`) to estimate the size, speed and end of the first wave |
| Outbreak similarity | **Dynamic Time Warping** + `TimeSeriesKMeans` to cluster countries by the *shape* of their outbreak |
| Embedding | Multi-Dimensional Scaling (MDS) + K-Means, with and without scaling |
| Growth dynamics | Doubling rates and daily percentage growth per country |
| Context | Infections per 1,000 people vs. population density |

## Why it's here

It's an honest snapshot of how I worked before coding agents existed: messy real-world data, quick hypotheses, many plots. It's also where I first used DTW for time-series similarity, the same idea that drives my market pattern-matching work today.

The logistic-fit setup follows the approach that was widely shared in early 2020. The DTW clustering, the MDS embeddings, the country comparisons and the growth and density analysis are my own extensions.

## Data

- `data/COVID-19-geographic-distribution-worldwide-2020-04-09.xlsx`: ECDC snapshot of daily cases and deaths per country (published by the European Centre for Disease Prevention and Control)
- Section 6 additionally used a 2020 population and density table (`population_2020.csv`: rank, name, density, pop2020, area), which is not included here

## Run it

The code is published exactly as written in 2020, so the file paths in the loading cells still point to my old local folder. Change them to `data/...` before running.

```bash
pip install pandas numpy scipy scikit-learn tslearn matplotlib seaborn openpyxl
jupyter notebook covid_spring_2020.ipynb
```

*Snapshot from April 2020. The numbers and forecasts reflect what was known at that time, not the later course of the pandemic.*
