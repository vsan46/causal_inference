# Causal Inference: Returns to Schooling using IV
**Project Status:** Completed

## 1. Project Overview
In this project, I replicate the analysis from David Card's famous 1995 paper, *"Using Geographic Variation in College Proximity to Estimate the Return to Schooling"*. 

My goal was to determine the causal effect of an extra year of education on wages. Since education is likely endogenous (correlated with unobserved "ability"), standard OLS regression often yields biased results. To solve this, I employed an **Instrumental Variable (IV)** strategy.

## 2. The Identification Strategy
To isolate the causal link, I used **geographic proximity to a college** (`nearc4`) as an instrument for education.

* **The Problem:** High-ability individuals are likely to get more education *and* earn higher wages regardless of schooling. This causes OLS to overestimate the return (or underestimate it, if high-opportunity cost dominates).
* **The Instrument:** Did the individual grow up near a 4-year college?
* **Relevance:** Living near a college lowers the cost of attending, increasing the likelihood of obtaining more education.
* **Exclusion Restriction:** Living near a college in childhood should not directly affect future wages, except through the channel of increased education.

## 3. Methodology
I performed the analysis in Python using `statsmodels` and `linearmodels`.
1.  **Naive OLS:** I established a baseline estimate of the return to education.
2.  **2SLS (Two-Stage Least Squares):** I used `nearc4` to predict education levels, then used those predicted levels to estimate wages.

## 4. Key Findings
* **OLS Result:** My baseline OLS model suggested a return to schooling of approximately **7.5%** per year.
* **IV Result:** The IV estimate jumped to approximately **13.2%** per year.
* **Interpretation:** The fact that the IV estimate is *higher* than the OLS estimate is a classic result in this literature. It suggests that the "local average treatment effect" (LATE) applies to a specific sub-population: those who would not have gone to college if they hadn't lived near one (compliers). For this group, the marginal return to education is very high.

## 5. Tools Used
* **Python:** Main analysis
* **Pandas:** Data manipulation
* **Linearmodels:** For robust IV/2SLS estimation
* **Wooldridge:** Source of the dataset