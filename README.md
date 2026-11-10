# E. coli Resistance to Third-Generation Cephalosporins: Confidence Interval Analysis of EARS-Net Data, 2013 to 2025


*Last updated: November 2026*



---

## Summary

This project asks what share of invasive *E. coli* isolates reported to EARS-Net were resistant to third-generation cephalosporins, and how that share differed before and after EARS-Net moved to EUCAST-only interpretation. In 2020 to 2025, 13.86% of 986,328 tested isolates were resistant (95% CI 13.79% to 13.92%), which is 1.83 percentage points higher than in 2013 to 2018. (95% CI for the difference 1.73 to 1.93). That is about 1 in 7 tested isolates, so these antibiotics cannot be assumed to work for every patient, but the data cover reported isolates from participating countries and cannot show that the change in interpretation caused the rise.
The data do not show a step change when EARS-Net moved to EUCAST-only interpretation in 2019, and they cannot show what caused the rise.

---

## Background

Antimicrobial resistance (AMR) is a growing public health problem because it reduces the effectiveness of antibiotics. EUCAST publishes standardised criteria for interpreting antibiotic susceptibility tests. It does not reduce resistance itself. It makes measurement and surveillance more consistent across laboratories.

The European Antimicrobial Resistance Surveillance Network (EARS-Net), run by the European Centre for Disease Prevention and Control (ECDC), collects resistance data on invasive isolates from participating countries. Invasive isolates are bacteria found in normally sterile sites such as blood.

---

## Research Questions

1. What proportion of invasive E. coli isolates reported through EARS-Net in 2020 to 2025 were resistant to third-generation cephalosporins?
2. How does that compare with 2013 to 2018, and how did the rate move year by year?

---

## Dataset

| Item | Detail |
|---|---|
| Source | ECDC, EARS-Net surveillance data |
| Organism | *Escherichia coli* |
| Antibiotic group | Third-generation cephalosporins |
| Population | Reported invasive isolates |
| Pre period | 2013 to 2018 |
| Post period | 2020 to 2025 |
| Excluded | 2019, the year of the changeover to EUCAST-only interpretation |

---

## Methodology

1. **Cleaning and preparation** in Python (pandas): filtered the raw ECDC file to the organism, antibiotic group and study periods above.
2. **Exploratory data analysis** of tested and resistant isolate counts by year.
3. **Resistance proportion and confidence interval** for each period, using the normal approximation to the binomial proportion:

```
p  = resistant / tested
SE = sqrt( p * (1 - p) / n )
95% CI = p ± 1.96 * SE
```

4. **Difference between periods.** The two periods are treated as independent samples, so their standard errors combine:

```
SE_diff = sqrt( SE_pre^2 + SE_post^2 )
95% CI  = (p_post - p_pre) ± 1.96 * SE_diff
```

5. **Visualisation** in Power BI: the pooled interval, the yearly resistance rate, and a region filter.

---

## Results

| Period | Resistant | Tested | Resistance | 95% CI |
|---|---:|---:|---:|---|
| Pre (2013 to 2018) | 81,262 | 675,790 | 12.02% | 11.95% to 12.10% |
| Post (2020 to 2025) | 136,656 | 986,328 | 13.86% | 13.79% to 13.92% |
| **Difference (post minus pre)** | | | **+1.83 points** | **1.73 to 1.93** |

### Year by year

| Year | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 |
|---|---:|---:|---:|---:|---:|---:|
| Resistance | 12.66% | 11.91% | 12.68% | 14.43% | 14.69% | 15.70% |

### What the results show

- The difference between periods is statistically distinguishable from zero. The interval does not include 0.
- The yearly pattern matters more than the pooled figure. 2020 to 2022 sit within about 0.7 points of the pre-period rate. The rise appears in 2023 to 2025.
- Because the increase is concentrated in the last three years, the data do not support a simple "before and after EUCAST-only adoption" story.
- Tested isolates rose from 675,790 to 986,328 between two periods of equal length (six years each). This suggests reporting coverage changed, which this analysis did not investigate.

---

## Conclusion

Resistance to third-generation cephalosporins in invasive E. coli was higher in 2020 to 2025 than in 2013 to 2018, and the rise accelerated in the final three years. The pooled estimate is precise, but it describes no single year, so the yearly series is the more useful result. The analysis shows that resistance rose. It does not show why.

## Recommendations

- **Researchers:** analyse the trend by country, using methods that account for clustering within countries and laboratories, and add confidence intervals to each year.
- **Surveillance programmes:** follow the 2023 to 2025 increase closely, and publish coverage information (countries and laboratories reporting) alongside resistance rates so changes in reporting can be separated from changes in resistance.

---

## Limitations

- The data are reported invasive isolates from participating EARS-Net countries. They do not represent all E. coli infections.
- Country participation and laboratory coverage vary across years, which can change the reported rate without any change in true resistance.
- The comparison is observational and not causal. The interpretation rules changed between the two periods, so the comparison reflects the measurement system as well as the bacteria.
- The confidence intervals assume every isolate is an independent random draw. Isolates cluster within countries and laboratories, so the true uncertainty is wider than the intervals shown.
- Pooling six years into one estimate hides the year-to-year pattern. Yearly rates are reported without confidence intervals so far.

---

## Tools

Python (pandas, NumPy, SciPy, Matplotlib, Seaborn), Power BI, Git and GitHub.

## Repository Structure

```
ecoli-cephalosporin-resistance-confidence-intervals/
├── data/
│   ├── raw/             ECDC source file (not committed if large)
│   └── processed/       Cleaned analysis file
├── notebooks/
│   └── amr_confidence_interval.ipynb
├── visuals/
│   └── Executive Summary.png
├── requirements.txt
└── README.md
```

## How to Run

1. Install the requirements: `pip install -r requirements.txt`
2. Download the EARS-Net data from the ECDC link below and place the CSV in `data/raw/`.
3. Open `notebooks/amr_confidence_interval.ipynb` and choose **Run All**.

## Data Source

European Centre for Disease Prevention and Control (ECDC), European Antimicrobial Resistance Surveillance Network (EARS-Net): https://www.ecdc.europa.eu/en/antimicrobial-resistance/surveillance-and-disease-data/data-ecdc

---

*Author: Emmanuel Bitrus*
