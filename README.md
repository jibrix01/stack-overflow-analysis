# Developer Pay and Job Satisfaction: A 2024 Stack Overflow Survey Analysis

This repository contains a regression analysis of developer compensation and job satisfaction.

## Data
The raw data comes from the 2024 Stack Overflow Developer Survey. It covers 65,437 respondents across 185 countries. The dataset is released under the Open Database License.

**Note:** The dataset itself is not included in this repository. 

## Tools
* Python
* pandas
* scikit-learn (Ridge, Random Forest)
* seaborn/matplotlib

## Methodology and Cleaning
Srict cleaning steps were applied before running any analysis. The final dataset dropped to 19,990 professional developers with valid pay and experience data.

* Only respondents who selected "I am a developer by profession."
* Annual compensation was restricted to between $5,000 and $500,000 to remove data-entry errors and outliers.
* Experience text buckets were converted into numeric years.
* Rows missing usable experience values were dropped entirely.

Compensation received a log10 transform before entering any linear model because raw pay is heavily right-skewed.

## Summary of Findings

* Country and years of experience account for almost all of what a regression model can explain about pay (R² ≈ 0.54).
* Education and remote status barely move the needle once country and experience are known.
* Languages like Go and Rust look like they pay more, but developers who use them also tend to be more senior.
* Job satisfaction correlates more with day-to-day friction than with pay.
* Remote workers report higher pay, but part of that gap exists because remote workers in this sample are more senior.
* A five-fold cross-validated Random Forest edges out a plain Ridge regression by about two points of R² (0.56 vs. 0.54).

Even the better model is off by about 50% on a typical prediction.