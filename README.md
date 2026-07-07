# Multiple Regression Analysis — Variable Selection for Sales Candidate Prediction

A statistical modeling project that identifies the best subset of predictor variables for forecasting first-month sales performance of job candidates, using correlation analysis, multicollinearity diagnostics, and all-possible-regressions selection.

## Problem Statement

An HR manager wants a data-driven model to predict a candidate's ability to become a qualified salesperson. Sales performance in the first month (`y`) is modeled against five candidate attributes:

- `x1` — sales aptitude test score
- `x2` — age
- `x3` — irritability tendency test score
- `x4` — years of work experience
- `x5` — average school GPA

The task: find the smallest set of predictors that best explains sales performance, without multicollinearity distorting the estimates.

## Methodology

1. **Correlation matrix** — computed pairwise correlations between `y` and all predictors to identify candidate variables and detect multicollinearity risk between predictors themselves.
2. **Full regression model** — fit `y` against all five predictors; inspected t-statistics, p-values, and Variance Inflation Factors (VIF) to flag insignificant and collinear variables.
3. **All-possible-regressions search** — evaluated all 2⁵−1 = 31 possible variable subsets, comparing R² across each.
4. **Best subset selection** — selected the model with the fewest variables that retained near-maximal explanatory power without multicollinearity.

## Key Results

| Model | # Variables | R² |
|---|---|---|
| Full model (x1–x5) | 5 | 0.9799 |
| **Selected model (x1, x2)** | **2** | **0.9777** |

Final model:

```
y = -75.00 + 0.2211·x1 + 5.307·x2
```

- VIF for both retained predictors ≈ 1.32 → multicollinearity effectively eliminated.
- The two-variable model explains **97.77%** of the variance in `y`, nearly matching the full 5-variable model while being far more parsimonious and interpretable.

## Tools

- Minitab (correlation, regression, all-possible-regressions procedures)

## Files

- `report.pdf` — full write-up with correlation matrix, regression outputs, and all-possible-regressions table
