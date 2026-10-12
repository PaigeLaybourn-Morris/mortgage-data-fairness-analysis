
# Mortgage Data Analysis: When Can Data Produce an Unfair Decision?

## Project Overview

This project explores the relationship between data, decision-making and fairness within the mortgage market. Using official mortgage product sales data published by the UK Financial Conduct Authority (FCA), the analysis investigates patterns in mortgage sales across demographic and financial categories and considers the potential implications for data-driven lending decisions.

The project aims to understand how the characteristics and limitations of a dataset can affect the conclusions drawn from it, particularly when data is used to inform automated decisions such as mortgage lending.

## Research Questions

- How have mortgage sales changed over time?
- How are recorded mortgage sales distributed across age groups, income bands and UK regions?
- What patterns can be identified across borrower characteristics, mortgage values and lending products?
- How could unrepresentative training data, proxy variables and unreliable eligibility labels contribute to unfair algorithmic decisions?
- Why is overall model accuracy insufficient to establish that a decision-making system is fair?

## Dataset and Source

The dataset used in this project is the **Mortgage Product Sales Data**, published by the Financial Conduct Authority (FCA).

**Official source:** https://www.fca.org.uk/data/product-sales-data

The analysis uses quarterly mortgage data covering 2021–2025 and examines recorded sales across several categories, including:

- Age group
- Income band
- Postcode region
- Borrower type
- Loan amount
- Property value
- Loan-to-value (LTV) ratio
- Mortgage term
- Interest rate type
- Sales channel and advice status

The dataset is aggregated rather than consisting of individual mortgage applications. It therefore provides insight into recorded mortgage sales and their characteristics, rather than the outcomes of individual lending decisions.

## Methodology

The analysis was conducted in Python using Google Colab.

The main stages were:

1. **Data preparation:** Loaded the FCA spreadsheet into a pandas DataFrame and examined its structure.
2. **Data quality checks:** Checked for missing values, duplicate rows and negative values in the cleaned dataset.
3. **Feature preparation:** Extracted year and quarter information from the date column to support time-based analysis.
4. **Descriptive analysis:** Calculated totals, proportions and percentage changes to identify patterns in mortgage sales.
5. **Visualisation:** Used charts and summary tables to communicate changes over time and differences between categories.
6. **Fairness evaluation:** Considered how data quality, representation and potentially sensitive or proxy variables could affect algorithmic decision-making.

## Key Findings

### 1. Changes in Mortgage Sales Over Time

The analysis identified the following annual totals from the age-group sales breakdown:

| Year | Recorded sales | Annual change |
|---|---:|---:|
| 2021 | 1,224,696 | — |
| 2022 | 1,150,889 | -6.03% |
| 2023 | 888,342 | -22.81% |
| 2024 | 941,360 | +5.97% |
| 2025 | 1,080,728 | +14.80% |

Recorded sales declined between 2021 and 2023 before increasing in 2024 and 2025. Despite this recovery, the 2025 total remained below the 2021 total.

These figures describe recorded mortgage sales and should not be interpreted as the number of applications received or the proportion of applicants approved.

### 2. Age Distribution

In 2025, the largest age category was 31–35, accounting for approximately 19.21% of recorded sales. The 36–40 and 26–30 groups accounted for approximately 16.89% and 16.58%, respectively.

These findings indicate that recorded mortgage sales were concentrated among borrowers aged 26–40. However, sales distributions alone cannot establish whether particular age groups were treated unfairly, as the dataset does not show how many people in each group applied for a mortgage or were rejected.

### 3. Income Distribution

The largest income category in 2025 was £50,001–£100,000, representing approximately 46.90% of recorded sales. The £0–£50,000 category accounted for 28.76%, while the £100,001+ category accounted for 20.08%.

Approximately 4.27% of the recorded sales were categorised as having unknown income.

These differences provide a useful description of the income distribution within recorded sales, but do not demonstrate that higher-income applicants were more likely to be approved. Application numbers, rejection outcomes and relevant eligibility information would be needed to investigate that question.

### 4. Regional Distribution

The South East accounted for the largest share of recorded mortgage sales in 2025, at approximately 15.48%. The North West accounted for 11.10%, while London represented 10.77%.

Regional differences may reflect variations in population, housing prices, demand and other economic conditions. Postcode or regional information could also act as a proxy for characteristics associated with protected groups, creating potential fairness concerns if such information is used in automated lending decisions.

The observed regional differences do not, by themselves, establish discrimination.

## Algorithmic Fairness

A central theme of this project is the distinction between predictive accuracy and fairness.

### Overall Accuracy

For a model with known outcomes, accuracy measures the proportion of predictions that are correct:

Accuracy = (True Positives + True Negatives) / Total Predictions

However, a model can achieve high overall accuracy while performing differently across demographic groups.

### Approval Rates

An approval rate measures the proportion of applicants in a group who receive approval:

Approval Rate = Number Approved / Total Applicants in the Group

Comparing approval rates can help identify differences in outcomes between groups. Nevertheless, equal approval rates do not necessarily establish fairness, because groups may differ in relevant eligibility characteristics.

### True Positive Rate

The true positive rate measures the proportion of genuinely eligible applicants correctly approved:

True Positive Rate = True Positives / (True Positives + False Negatives)

Comparing this metric across groups can help investigate whether eligible applicants are being incorrectly rejected at different rates.

Other metrics, including false positive rates, may also be relevant depending on the fairness objective.

**Important limitation:** The FCA sales dataset does not contain individual applications, rejected applications, model predictions or verified eligibility labels. Consequently, this project cannot directly calculate mortgage approval rates, model accuracy or group-specific error rates. These metrics are discussed conceptually rather than presented as empirical results from this dataset.

## Potential Sources of Unfairness

### 1. Unrepresentative Training Data

If a model is trained on historical data that underrepresents certain groups, its predictions may be less reliable for those groups. Historical lending patterns may also reflect existing inequalities.

### 2. Proxy Variables

Variables such as postcode can indirectly reflect socioeconomic circumstances or characteristics associated with protected groups. A model may therefore reproduce unequal outcomes even if sensitive characteristics are not explicitly included.

### 3. Unreliable Eligibility Labels

If historical approval decisions are treated as evidence of whether an applicant was genuinely eligible, the model may learn past decisions rather than objective creditworthiness. Inaccurate or biased labels can therefore reinforce existing problems.

### 4. Conflicting Fairness Objectives

Different fairness metrics can lead to different conclusions about a model. For example, equal overall approval rates do not guarantee equal error rates among eligible applicants.

Evaluating fairness therefore requires a clearly defined objective, appropriate data and consideration of the consequences of different types of errors.

## Limitations

This analysis has several important limitations:

- The data records mortgage product sales rather than individual application outcomes.
- Group-level sales totals do not provide the denominators needed to calculate application or approval rates.
- The dataset does not contain verified eligibility labels or model predictions.
- Observed demographic and regional differences cannot independently establish discrimination or causation.
- Aggregate data can conceal variation within individual groups.
- The findings describe patterns in the available data and should not be generalised beyond what the dataset supports.

## Conclusion

This project demonstrates how descriptive data analysis can identify patterns in mortgage sales while highlighting the limitations of using observed data to assess fairness.

The results show differences in recorded sales across age groups, income bands and regions, but these differences cannot be interpreted directly as evidence of unfair lending. Establishing whether a mortgage decision-making system is fair would require more detailed application-level data, reliable eligibility labels and an explicit choice of fairness metrics.

Ultimately, **data can contribute to unfair decisions when it is unrepresentative, reflects historical inequalities, relies on misleading proxy variables or uses unreliable labels**. High predictive accuracy alone is not sufficient to guarantee fair outcomes.

## Tools and Technologies

- Python
- Google Colab
- pandas
- NumPy
- Matplotlib
- Seaborn (if used in the notebook)

## Reproducibility

To reproduce the analysis:

1. Open the Jupyter notebook in this repository using Google Colab.
2. Download the relevant quarterly mortgage data from the official FCA source.
3. Update the file path in the notebook if necessary.
4. Run the notebook cells in order to reproduce the data preparation, calculations, visualisations and findings.

## Author

Mathematics and Statistics undergraduate project exploring data analysis, financial decision-making and algorithmic fairness.
