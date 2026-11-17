[**English**](README.md) | [Русский](README.ru.md)

# Customer Churn: Bank Customer Churn Analysis

**Objective:** Identify the customer characteristics associated with leaving the bank, determine the highest-risk segments, and assess which customer-retention areas warrant further investigation.

**Data:** 10,000 customers from France, Germany, and Spain. The target variable is `Exited`: `1` means the customer left, and `0` means the customer stayed. The churn rate in the sample is **20.4%**.

**Tech stack:** Python, pandas, NumPy, Matplotlib, Seaborn, SciPy, scikit-learn, statsmodels.

## Project structure

```text
.
├── Customer churn analysis.ipynb
├── Churn_Modelling.csv
└── README.md
```

## Data and methodology

The dataset contains 14 columns: credit score, country, gender, age, tenure, balance, number of bank products, credit card ownership, customer activity, estimated salary, and the target variable `Exited`, as well as identifier fields.

Before the analysis, data-quality checks were performed for missing values, exact duplicate rows, duplicate `CustomerId` values, and logical anomalies. Identifiers were excluded from the analysis because they do not provide independent behavioral information.

Next, churn rates were compared across age, country, gender, number of products, activity, and financial characteristics. Sample sizes and 95% Wilson confidence intervals were calculated for the groups.

Associations between features and churn were also assessed using effect sizes and mutual information. For mutual information, a noise threshold was estimated by permuting the target variable. Intersections between features and the contribution of high-risk segments to total churn and aggregate balance were examined separately.

## Key findings

### Churn across key segments

| Segment | Result |
|---|---:|
| Overall churn | **20.4%** |
| Customers aged 41–60 | 31% of the customer base and 61% of all customers who left |
| Germany | **32.4%** churn |
| France and Spain | 16–17% churn |
| Inactive customers | **26.9%** churn |
| Active customers | 14.3% churn |

### Highest-risk segment

The most prominent risk group is **inactive customers aged 41–60**:

- 16% of the entire customer base;
- 39% of all customers who left;
- churn rate within the segment: **51%**.

This segment appears to be a priority for further investigation of retention hypotheses.

### Impact on the customer base and balance

Customers who left accounted for **24.3% of the total balance**. Customers from Germany accounted for 12.8% of the total balance across the entire customer base.

Credit score, estimated salary, tenure, and credit card ownership did not show a meaningful association with churn in this analysis.

### Interpretation limitations

Customers with three and four products had very high churn rates — 83% and 100%, respectively. However, these figures are based on small groups. They should not be translated directly into product decisions without further data validation.

## Conclusion

Churn is not distributed evenly across the customer base. The most pronounced differences are associated with age, country, and customer activity. The first priorities should be to investigate retention among inactive customers aged 41–60 and to examine the high churn rate in Germany separately.

The results describe associations in observational data and **do not establish causality**. Choosing specific retention measures will require additional validation and experimental evaluation of their effectiveness.

## Data and setup

`Churn_Modelling.csv` is the original dataset from Kaggle: [Bank Customer Churn Prediction Dataset](https://www.kaggle.com/datasets/saurabhbadole/bank-customer-churn-prediction-dataset/data).

Python 3.10+ is required.

```bash
python -m pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels jupyter
jupyter notebook
```

Open `Customer churn analysis.ipynb`, make sure `Churn_Modelling.csv` is in the notebook's working directory (or specify its path in the first cell), and then run the cells in order.

---

*Educational portfolio project. The conclusions apply to the dataset provided and do not establish cause-and-effect relationships.*
