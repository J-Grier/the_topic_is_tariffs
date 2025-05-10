# Tariff Topic Modeling & Market Sensitivity Analysis

This project applies Bayesian topic modeling and hierarchical regression to identify how financial markets respond to trade policy uncertainty.

## Overview
- **Goal**: Determine whether unstructured financial headlines about tariffs contain actionable market signals.
- **Methods**: Hierarchical Dirichlet Process (HDP), Hierarchical Bayesian Regression, Gaussian Mixture Modeling (GMM)
- **Data**: ~2,000 tariff-related news headlines from Polygon.io (Dec 2024 – May 2025), S&P 500 stock prices, sector ETF returns

## Key Components
### ▶ Topic Modeling with HDP
- Automatically infers the number and content of latent topics from unstructured headlines
- Outperformed standard and seeded LDA in coherence and adaptability

### ▶ Event Study + Sector Analysis
- Identified event windows around first appearances of high-impact HDP topics
- Calculated Cumulative Abnormal Returns (CARs) for 6 ETFs (SPY, XLI, CARZ, FXI, XRT, SMH)
- Demonstrated divergent, sector-specific reactions to individual topics

### ▶ Stock-Level Sensitivity via Bayesian Regression
- Modeled each S&P 500 stock's response to topic emergence
- Classified stocks as **Resilient** or **Sensitive** based on posterior intervals
- 93 Resilient | 37 Sensitive | 0 Unaffected (by construction)

### ▶ Comparison to Gaussian Mixture Model (GMM)
- GMM identified clusters in raw abnormal returns without using topics
- HDP-guided classifications proved more diversified and stable under noise

## Portfolio Results
| Portfolio        | # of Stocks | Total Return | Annualized | Volatility | Sharpe Ratio |
|------------------|-------------|--------------|------------|------------|---------------|
| HDP Resilient    | 93          | +12.15%      | +34.72%    | 19.97%     | 1.74          |
| HDP Sensitive    | 37          | –23.35%      | –49.89%    | 38.16%     | –1.31         |
| GMM Cluster 0    | 8           | +43.95%      | +157.65%   | 31.47%     | 5.01          |
| GMM Cluster 1    | 6           | –37.89%      | –70.99%    | 44.63%     | –1.59         |
| SPY              | 1           | –6.88%       | –16.90%    | 28.13%     | –0.60         |

## Why It Matters
- Topic modeling can serve as more than sentiment tagging—it structures market narratives
- Bayesian inference offers confidence-aware classifications under noisy returns
- Demonstrates that news-driven signals can translate to portfolio-level performance

## Files
- `tariff_topic_pipeline.ipynb`: Model pipeline and output summary *(available upon request)*
- `bayesian_stock_tariff_classification.csv`: Stock-level posterior summaries

## References
- Huang et al. (2018), *Management Science*: Topic modeling earnings calls
- Yun (2024), *UChicago Thesis*: HDP in financial Q&A data
- Wang et al. (2025), *arXiv*: GMM-based stock return modeling

> _Model code available upon request. Full replication requires Polygon.io API access._
