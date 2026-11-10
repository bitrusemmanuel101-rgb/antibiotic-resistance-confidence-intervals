# EUCAST and Antimicrobial Resistance in *E. coli*

## Project Overview

This project is part of a three-project pharmaceutical statistics portfolio investigating antimicrobial resistance (AMR) in *Escherichia coli* (*E. coli*) in the context of EUCAST's standardisation of antibiotic susceptibility testing and interpretation.

The portfolio explores resistance estimation, historical resistance comparisons and antibiotic treatment comparisons using confidence intervals, hypothesis testing and A/B testing.

EUCAST provides standardised criteria for interpreting antibiotic susceptibility results. It does not directly reduce bacterial resistance; rather, it supports consistent measurement and surveillance of resistance.

---

## Project Objective

To estimate the proportion of invasive *E. coli* isolates resistant to third-generation cephalosporins during the period following EARS-Net's adoption of EUCAST-only susceptibility interpretation.

### Research Question

What proportion of invasive *E. coli* isolates reported through EARS-Net between 2020 and 2025 were resistant to third-generation cephalosporins?

### Dataset

- **Source:** European Centre for Disease Prevention and Control (ECDC), EARS-Net
- **Organism:** *Escherichia coli*
- **Antibiotic group:** Third-generation cephalosporins
- **Study period:** 2020–2025
- **Population:** Reported invasive isolates

### Methodology

- Data cleaning and preparation using Python.
- Exploratory data analysis.
- Calculation of the pooled resistance proportion.
- Estimation of a 95% confidence interval using the normal approximation to the binomial proportion.
- Visualisation of overall findings and annual resistance patterns using Power BI.

### Key Findings

| Metric | Result |
| --- | --- |
| Total tested isolates | 986,328 |
| Resistant isolates | 136,656 |
| Estimated resistance | 13.86% |
| 95% confidence interval | 13.79%–13.92% |


### Conclusion

The analysis estimated that 13.86% of invasive *E Coli* isolates reported through the EARS-Net between 2020 and 2025 were resisitant to third-generation cephalosporins. the 95% confidence interval ranged from 13.79% to 13.92%. These findings indicate that resistance remains an important concern requiring continued surveillance.


## Recommendations

1. Health Institutions: Continue monitoring third-generation cephalosporin resistance to support informed antibiotic selection.
2. Public Health Authorities: Strenghten antimicrobial resistance surveillance and maintain consistent laboratory reporting standards.
3. Future Researchers: Investigate resistance patterns across individual countries and examine change over time, accounting for difference in surveillance coverage.


### Limitations

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
