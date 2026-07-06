# When Marketing Models Try Too Hard

**A Practical Guide to Underfitting, Overfitting, and Building Models That Generalize**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/joedom99/overfitting-for-marketers/blob/main/when_marketing_models_try_too_hard.ipynb)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9+-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Made with Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-MIT-yellowgreen)](LICENSE)
[![Blog](https://img.shields.io/badge/Blog-Marketing%20Data%20Science-2C7873)](https://blog.marketingdatascience.ai)


This repository contains the companion Python notebook for my article [*When Marketing Models Try Too Hard*](https://blog.marketingdatascience.ai) on the Marketing Data Science blog. <!-- TODO: replace with live article URL after publication -->

The article explains why marketing models fail to generalize. This notebook lets you watch it happen.

## What's inside

The notebook builds three models on a synthetic dataset of 1,000 sales-qualified leads: one that learns too little, one that learns too much, and one that gets it just right.

| Model | Training Accuracy | Validation Accuracy |
|---|---|---|
| Underfit (1 feature) | 69% | 66% |
| Good Fit (6 real features) | 85% | 84% |
| Overfit (deep tree, 46 features) | 100% | 61% |

The overfit model scores perfectly on data it has seen and *worst of all* on data it hasn't. That single table is the whole article in miniature.

From there, the notebook demonstrates:

1. **The Goldilocks principle** visualized with polynomial curve fitting
2. **Training vs. validation curves** showing exactly where overfitting begins as model complexity increases
3. **Cross-validation** and why a single train/test split can mislead you by 10 points
4. **Time-based validation** for chronological marketing data, where shuffled cross-validation claims R² = 0.49 but an honest forward-in-time split reveals R² near zero
5. **Regularization** (L1) automatically zeroing out 31 of 40 junk CRM columns and improving validation accuracy
6. **Feature selection** showing that removing 40 irrelevant variables *improves* prediction by about five points
7. **Data leakage** via a realistic `contract_sent` field that boosts validation accuracy from 84% to 95% while making the model useless in production
8. **Marketing's small-n problem**: a 156-week marketing mix modeling simulation where ordinary regression assigns a pure noise variable a larger coefficient than a channel that genuinely drives sales, and Ridge regularization reins it in

Every random process is seeded (`SEED = 430`), so your numbers will match the article exactly.

## Figures

Running the notebook exports all seven figures to a `figures/` folder in a clean, publication-style format (white backgrounds, minimal chrome). These are the same figures used in the article.

## How to run it

**Google Colab (recommended):** Click the "Open in Colab" badge at the top of this README, then Runtime > Run all. No setup required. Everything used in the notebook comes preinstalled in Colab.

**Locally:**

```bash
git clone https://github.com/joedom99/overfitting-for-marketers.git
cd overfitting-for-marketers
pip install -r requirements.txt
jupyter notebook when_marketing_models_try_too_hard.ipynb
```

## Requirements

- Python 3.10+
- numpy, pandas, matplotlib, scikit-learn (see `requirements.txt`)

## A note on the data

All data in this notebook is **synthetic**, and that's deliberate. Because we generate the data ourselves, we know exactly which variables truly drive conversion and which are pure noise. That ground truth is what makes it possible to *see* a model fooling itself. The notebook is a teaching tool, not a plug-in template for your own CRM export, though every technique in it applies directly to real marketing data.

## Repository structure

```
.
├── when_marketing_models_try_too_hard.ipynb   # the companion notebook
├── requirements.txt
├── LICENSE
└── README.md
```

## Related articles

This notebook is part of a broader series on the statistical foundations of marketing analytics at [Marketing Data Science](https://blog.marketingdatascience.ai):

- *Bayesian Statistics Explained for Marketers* explains the prior-belief perspective behind regularization ([companion repo](https://github.com/joedom99/bayesian-stats-for-marketers))
- *When the Numbers Look Wrong: A Marketer's Guide to Anomaly Detection* covers recognizing when something unusual has happened
- My four-part marketing mix modeling series covers Robyn and Meridian in depth, including why regularization is fundamental to both

## About the author

Joe Domaleski is the founder of [Country Fried Creative](https://countryfriedcreative.com), a digital marketing agency in Peachtree City, GA, and writes about the intersection of marketing and data science at [Marketing Data Science](https://blog.marketingdatascience.ai).

## License

MIT License. See [LICENSE](LICENSE) for details.

