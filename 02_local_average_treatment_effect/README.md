# Practice: Local Average Treatment Effect (LATE) on Returns to Schooling

This is a practice project where I replicate the famous **Card (1995)** analysis to understand Instrumental Variables (IV) and LATE.

## The Goal
I want to measure the causal effect of an extra year of **Education** on **Wages**.

## The Problem (Endogeneity)
If we simply compare wages of educated vs. uneducated people (OLS), the results are biased.
* **Ability Bias:** High-ability people are likely to get more education *and* earn more money regardless of school.
* **Result:** OLS likely overestimates the effect of education for the general population.

## The Solution: Instrumental Variables
To fix this, I used an instrument: **Distance to College (`nearc4`)**.
* **Logic:** Growing up near a college makes it cheaper/easier to attend.
* **Relevance:** It correlates with education (proven in the First Stage).
* **Exclusion:** Living near a college shouldn't raise your wages *except* by helping you get an education.

## Who are the "Compliers"? (Understanding LATE)
Since this is an IV setup, the result is not the Average Treatment Effect (ATE) for everyone. It is the **Local Average Treatment Effect (LATE)**.

My estimate only applies to the **Compliers**:
> **Compliers** in this dataset are individuals who went to college *because* they lived near one, but would *not* have gone if they lived far away.

These are likely students from lower-income backgrounds for whom the cost of room & board was a dealbreaker.

## Results Summary

| Model | Coefficient | Interpretation |
| :--- | :--- | :--- |
| **OLS (Naive)** | A wage increase per year of school. (Likely Biased) |
| **IV (LATE)** | A wage increase per year of school. |

**Observation:** The LATE estimate is actually *higher* than the OLS estimate.
* **Why?** The "Compliers" (people on the margin who are sensitive to distance) actually get massive benefits from education. They likely have high potential but were held back by costs.