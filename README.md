# NHS GP Appointment DNA Analysis (SQL, Python, EDA, Statistics, Visualisation)

## Project Overview

This project investigates **Did Not Attend (DNA)** patterns in NHS GP appointments using SQL and Python analytics.  
The aim is to identify operational risk patterns, quantify financial impact, and provide practical recommendations to reduce missed appointments.

## Objectives

- Measure overall DNA rate and financial impact.
- Identify high-risk segments by appointment mode, season, and healthcare professional type.
- Engineer useful analytical features for trend and risk analysis.
- Validate patterns using statistical testing.
- Present clear visual evidence to support decisions.

## Dataset Summary

- **Period:** July 2023 to November 2025
- **Raw records:** 920+ million entries
- **Analysed appointments:** 866 million
- **DNA appointments:** 40.6 million
- **Overall DNA rate:** 4.42%
- **Estimated annual cost of DNA:** GBP 1.22 billion (using GBP 30 per missed appointment)

## Tools and Stack

- **SQL:** MySQL
- **Python:** pandas, numpy, matplotlib, seaborn, scipy
- **Notebook workflow:** Jupyter

## Analysis Workflow

## 1) SQL Phase

Main outputs:
- DNA rate by appointment mode
- DNA rate by healthcare professional type
- monthly and seasonal patterns
- highest-risk service combinations
- financial impact estimates

Key finding:
- **Video/online DNA rate: 0.46%** vs **Face-to-face DNA rate: 5.56%** (about **12x difference**).

## 2) Python Feature Engineering

Created and validated:
- `season` (Winter, Spring, Summer, Autumn)
- `dna_rate` (DNA count / total appointments)
- `months_since_start` (time index)
- `dna_rate_change` (month-over-month change)
- `Risk_level` (High_Risk / Low_Risk)

These features improved trend tracking and risk grouping.

## 3) Exploratory Data Analysis

Descriptive insights:
- Autumn is highest-risk season (~5.5%).
- Winter is lowest-risk season (~4.3%).
- October repeatedly shows the yearly peak.
- Other Practice Staff show higher DNA than GP-led appointments.

## 4) Statistical Testing

Tests used:
- **Chi-square test** for appointment mode vs DNA status
- **Cramer's V** for effect size
- **Independent t-test** for High_Risk vs Low_Risk periods
- **ANOVA** for seasonal DNA differences

Results summary:
- Chi-square p-value < 0.001 (statistically significant association).
- Cramer's V = 0.0732 (small but meaningful practical effect).
- T-test and ANOVA both support significant group differences.

## 5) Visualisation Outputs

Core charts produced:
- DNA rate by appointment mode (bar chart)
- Top 10 highest-risk combinations
- DNA rate over time (line chart)
- Seasonal decomposition plot
- Rolling averages trend
- Year-over-year DNA comparison
- DNA rate by HCP type
- HCP type vs appointment mode heatmap
- Financial loss by appointment mode

If these images are in the same folder, they can be displayed in GitHub:

![DNA by Appointment Mode](./dna_rate_by_appointment_mode_bar.png)
![DNA Over Time](./step4_line_dna_rate_over_time.png)
![DNA by HCP Type](./DNA%20Rate%20by%20Healthcare%20Provider%20Type.png)
![HCP vs Mode Heatmap](./DNA%20Rate%20(%25)%20by%20HCP%20Type%20and%20Appointment%20Mode.png)
![Financial Loss by Mode](./Financial%20Loss%20from%20DNA%20by%20Appointment%20Mode.png)

## Key Findings

1. **Appointment mode is the strongest operational lever** in this analysis.
2. **Face-to-face pathways drive most DNA risk and cost burden.**
3. **Risk is seasonal**, with repeated October spikes.
4. **HCP-mode combinations are not equally risky**, enabling targeted interventions.
5. DNA rates are improving gradually year-on-year, but not fast enough for a major cost reduction without additional action.

## Practical Recommendations (Operations)

- Expand appropriate video/online pathways for suitable appointment types.
- Run targeted reminder campaigns ahead of high-risk periods (especially October).
- Prioritise interventions for highest-risk HCP-mode combinations.
- Improve coding quality for Unknown/Unmapped categories.
- Use findings for local service redesign and capacity planning.

## Limitations

- Aggregated data (not individual patient-level records).
- Missing predictors (demographics, travel/access, reminder behavior, prior DNA history).
- National-level aggregation hides local practice variation.

## Repository Notes

- Main report: `NHS_DNA_Comprehensive_Report_v2.docx`
- Supporting notebook(s): `NHS_appointment ML.ipynb`, `NHS_Appointments.ipynb`
- Core dataset: `nhs_cleaned_with_features.csv`

---

If useful for your portfolio, you can pair this README with a separate model-focused README:
`README_ML.md`.
