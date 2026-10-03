# Minimum Wage and Youth Unemployment in the EU

**Abdulhamit Ayaz · Applied Economics course project**

An exploratory analysis of the relationship between the minimum-wage-to-median-wage ratio and youth unemployment, using 177 country-year observations for 20 EU countries over 2014–2022.

## Research question

How does the estimated relationship change across econometric and machine-learning approaches and alternative control specifications?

## Methods

- Two-way fixed-effects OLS with country-clustered standard errors.
- LASSO with standardized predictors and cross-validated regularization.
- An exploratory DoubleML partially linear regression comparison using random forests.
- Sensitivity checks: pre-COVID sample, exclusion of overall unemployment, and lagged minimum wage ratio.

## Main finding

The baseline fixed-effects estimate is close to zero and statistically insignificant. Excluding overall unemployment yields a larger negative, statistically significant association. The principal finding is **sensitivity to the control specification**, rather than conclusive evidence of a causal policy effect.

LASSO is a regularization exercise, not a significance test. DoubleML uses ordinary sample splitting and inference in this notebook, so its uncertainty estimates do not account for dependence within countries. Including country and year dummies in a random forest is not equivalent to the OLS fixed-effects transformation.

## Files

| File | Contents |
|---|---|
| `minimum_wage_analysis.ipynb` | Executed analysis, figures, interpretation and limitations |
| `data_final.csv` | Processed country-year input data |
| `requirements.txt` | Versions used to execute the notebook |

## Run locally

Use Python 3.12. Keep the notebook and CSV in the same directory.

```bash
python -m pip install -r requirements.txt
python -m jupyter notebook
```

Open `minimum_wage_analysis.ipynb` and select **Run All**. Alternatively, upload both the notebook and CSV to Google Colab, install the dependencies and run the cells. The notebook does not require a Google account or Colab-specific upload code to run locally.

## Data provenance

Source: Eurostat. The original course notebook reports datasets `une_rt_a` (unemployment), `earn_mw_avgr2` (minimum wage ratio) and `tec00115` (GDP growth).

The processed CSV is included. Original Eurostat extracts, download dates and the merge script were not supplied; the original source filters have not been independently audited. The observed panel has no duplicate country-year rows or missing values. Germany 2014 and Ireland 2021–2022 are absent.

See [Eurostat's data reuse policy](https://ec.europa.eu/eurostat/help/copyright-notice). Dataset attribution applies to the underlying data; this repository does not claim ownership of Eurostat data.

## Scope and limitations

This is a course project demonstrating panel-data analysis, model comparison and interpretation. A short observational panel cannot by itself establish causality. Overall unemployment may also respond to minimum wage policy, so adding it changes the conditional question rather than necessarily resolving confounding. A statistically insignificant coefficient does not demonstrate that the true effect is zero.

The exploratory DoubleML exercise does not implement cluster-aware cross-fitting or inference. See the [official DoubleML cluster-robust example](https://docs.doubleml.org/stable/examples/py_double_ml_multiway_cluster.html).

## Author contribution

The author developed the research question and analytical approach. AI assistance supported Python coding. This public version clarifies interpretation and reproducibility without expanding the original analysis design.
