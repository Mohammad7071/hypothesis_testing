# Hypothesis Testing for Oil Production Analysis

## Overview

This project demonstrates the application of statistical hypothesis testing to an operational problem in the oil and gas industry.

The analysis investigates whether a flowline restriction event was followed by a statistically significant decrease in oil production.

Using Python and daily production data, the project compares production performance before and after the operational event and applies Welch's Independent Two-Sample t-test to evaluate the observed difference.

The main objective is to demonstrate how statistical methods can help petroleum engineers evaluate operational changes and make more informed, data-driven decisions.

## Project Objective

In oilfield operations, production rates naturally fluctuate due to reservoir behavior, operating conditions, and equipment performance.

When an operational event occurs, engineers need to determine whether the observed production change represents a meaningful difference or normal production variation.

This project addresses the following question:

**Did the flowline restriction event lead to a statistically significant decrease in oil production?**

## Dataset

The analysis uses two datasets:

**1. Daily Production Dataset**

Contains daily production records for multiple wells, including:

- Date
- Well ID
- Actual oil production rate
- Pressure
- Water cut
- Well status
- Other production-related variables

The cleaned dataset is already available as `production_valid_df`.

**2. Operational Events Dataset**

Contains recorded operational events, including event identifiers, affected wells, event dates, and event types.

The selected event is:

| Parameter | Value |
|---|---|
| Event ID | E0066 |
| Well ID | A19 |
| Event Type | Flowline Restriction |
| Event Date | 2024-05-05 |

*Note: The datasets are synthetic and are used for educational purposes.*

## Methodology

The analysis follows these steps:

### 1. Event Selection

The operational event with ID `E0066` is selected from the events dataset.

The affected well and event date are then identified.

### 2. Production Data Selection

Daily oil production data for Well A19 are extracted from the cleaned production dataset.

Two time periods are selected:

- Before the event: 14 days before the event date.
- After the event: 14 days after the event date.

The event date itself is excluded.

### 3. Descriptive Statistics

The mean and standard deviation of oil production are calculated for both periods.

These statistics provide an initial understanding of production performance before and after the event.

### 4. Hypothesis Formulation

The null and alternative hypotheses are defined as follows:

**Null Hypothesis (H₀):**

\[
\mu_{before} \leq \mu_{after}
\]

The mean production before the event is less than or equal to the mean production after the event.

**Alternative Hypothesis (H₁):**

\[
\mu_{before} > \mu_{after}
\]

The mean production before the event is greater than the mean production after the event.

### 5. Statistical Testing

Welch's Independent Two-Sample t-test is applied to compare the mean production rates.

Welch's t-test is selected because it does not require the two groups to have equal variances.

The significance level is set to 0.05.

### 6. Decision and Interpretation

The p-value is compared with the significance level.

- If p-value < 0.05: Reject the null hypothesis.
- If p-value >= 0.05: Fail to reject the null hypothesis.

The final decision is interpreted in the context of oilfield production performance.

### 7. Data Visualization

A boxplot is used to compare the distribution of oil production before and after the event.

This visualization helps identify differences in the central values and spread of production rates.

## Tools and Libraries

The project uses the following Python libraries:

| Library | Purpose |
|---|---|
| Pandas | Data manipulation and filtering |
| SciPy | Statistical hypothesis testing |
| Matplotlib | Data visualization |
| Seaborn | Statistical plotting |

## How to Run the Project

### Requirements

Install the required libraries:

```bash
pip install pandas scipy matplotlib seaborn
```

### Data Preparation

Load the production and events datasets into your Python environment.

The production dataset should already be cleaned and available as:

```python
production_valid_df
```

The operational events dataset should be available as:

```python
events_df
```

Make sure the date columns are in datetime format before running the analysis.

### Run the Analysis

Run the Python script or notebook provided in this repository.

The code will:

1. Select the operational event.
2. Extract production data before and after the event.
3. Calculate descriptive statistics.
4. Perform Welch's t-test.
5. Calculate the percentage change in mean production.
6. Display the statistical decision.
7. Generate a boxplot.

## Key Concepts

**Hypothesis Testing**

A statistical method used to evaluate assumptions about a population based on sample data.

**Null Hypothesis (H₀)**

The initial statistical assumption tested using the available data.

**Alternative Hypothesis (H₁)**

The competing hypothesis that represents the effect or difference being investigated.

**P-value**

The probability, assuming the null hypothesis is true, of obtaining a test statistic at least as extreme as the one observed.

**Significance Level (α)**

The threshold used to determine whether the statistical evidence is sufficient to reject the null hypothesis.

**Welch's t-test**

A statistical test used to compare the means of two independent groups without assuming equal variances.

## Limitations

This project is intended as an educational example rather than a definitive operational investigation.

Several limitations should be considered:

- The analysis focuses on only one well and one operational event.
- The selected periods contain a limited number of daily observations.
- Daily production measurements may exhibit autocorrelation, meaning consecutive observations may not be independent.
- Other operational or reservoir-related factors may influence production during the selected periods.
- A statistically significant difference does not necessarily establish a causal relationship between the event and the production change.

For a more robust investigation, time-series analysis, additional operational variables, and comparisons with unaffected wells could be considered.

## Conclusion

Hypothesis testing provides a structured approach to evaluating operational assumptions using production data.

In this example, Welch's t-test is used to investigate whether oil production decreased after a flowline restriction event.

The project demonstrates how statistical analysis can help engineers move beyond simple before-and-after comparisons and evaluate operational changes using statistical evidence.

The broader objective is to connect petroleum engineering knowledge with data analysis techniques to support better operational decisions.

## Author

**Mohammad Ghasem**

Petroleum Engineering | Reservoir Engineering | Data Analysis | Python | Statistical Analysis
