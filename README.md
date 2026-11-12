# Healthcare Equity: Hospital Readmissions and Insurance Coverage

**Team A02** | BA780 Introduction to Data Analytics | Boston University, Questrom School of Business

Does a state's insurance coverage explain how often hospital patients are readmitted? We combined CMS hospital readmission data with KFF insurance data for 52 states and territories and six conditions to find out.

## Key Findings

- **Coverage does not track readmissions.** The correlation between a state's uninsured rate and its readmission gap is r = −0.11, which is essentially zero.
- **Medicaid expansion lowers the uninsured rate, but not readmissions.** Expansion states average 6.7% uninsured versus 10.0% for non-expansion states, yet their readmission gaps are the same.
- **Medicaid share is a suggestive lead.** It shows a moderate link to readmission gaps (r = +0.45), but the link weakens without Puerto Rico (r = +0.25), so we treat it as suggestive.
- **Medical conditions move together.** A state above the national rate on one medical condition tends to be above on the others (average r = +0.61).
- **Recommendation:** Do not justify coverage expansion by its effect on readmissions. Judge it on access to care, and test discharge and follow-up programs in high-gap states before scaling them.

## Research Question

Many people assume uninsured patients get less follow-up care and are readmitted more often. If that were true, expanding coverage should reduce readmissions, which matters to state Medicaid agencies and hospital associations deciding where to spend. We tested that assumption.

## Method

- **Readmission gap:** each hospital's 30-day readmission rate minus the national median for the same condition, then the median across each state's hospitals. This keeps conditions with very different baseline rates comparable.
- **Data:** 14,701 usable hospital-condition records, after removing 14,039 suppressed rows, joined to state insurance data.
- **Tests:** Pearson and Spearman correlations, Welch t-tests, Cohen's d, bootstrap and Fisher-z confidence intervals, and OLS regression with robust errors.
- **Multiple testing:** Holm correction on the secondary tests.
- **Robustness:** key results checked with and without Puerto Rico, and without North Carolina and South Dakota.
- **Verification:** every number in the report was checked against the code (98 of 98 matched).

## Repository Contents

| File | Description |
|------|-------------|
| `A02-Healthcare-Equity-Hospital-Readmissions-and-Insurance-Coverage.ipynb` | Final notebook: cleaning, analysis, charts, conclusions |

## Data Sources

| Dataset | Publisher | Link |
|---------|-----------|------|
| Unplanned Hospital Visits – Hospital | CMS Provider Data Catalog | https://data.cms.gov/provider-data/dataset/632h-zaca |
| Unplanned Hospital Visits – State | CMS Provider Data Catalog | https://data.cms.gov/provider-data/dataset/4gkm-5ypv |
| Health Insurance Coverage of the Total Population, 2022–2024 | KFF State Health Facts | https://www.kff.org/state-health-policy-data/state-indicator/total-population/ |
| Status of State Medicaid Expansion Decisions (published October 2026) | KFF | https://www.kff.org/status-of-state-medicaid-expansion-decisions/ |
| Status of State Action on the Medicaid Expansion Decision (as of October 2026) | KFF State Health Facts | https://www.kff.org/affordable-care-act/state-indicator/state-activity-around-expanding-medicaid-under-the-affordable-care-act/ |

## How to Run

1. Open the notebook in Jupyter or Google Colab.
2. Install the libraries: `pandas`, `numpy`, `scipy`, `statsmodels`, `matplotlib`, `seaborn`.
3. Download the datasets from the links above and load them as described in the notebook's data section.
4. Run all cells from top to bottom.

## Limitations

- CMS readmission scores cover Medicare patients, who are almost all insured, while KFF coverage describes the whole population. State uninsured rates are therefore a stand-in, and our results mean "no evidence of a link," not "coverage doesn't matter."
- The analysis is at state level, so it cannot speak to individual patients.
- Only 10 states did not expand Medicaid, which limits the comparison.
- The care-transition recommendation rests on published studies, not on our data.

## Contributors

- Aqsa Siddique
- Samarth Karan
- Ting Hui Chu
- Dhruv Shah

## AI Disclosure

Generative AI tools were used for coding assistance, wording refinement, and brainstorming. See the AI Disclosure section of the notebook for details.
