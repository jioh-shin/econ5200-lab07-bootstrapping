# Diagnosing Broken Confidence Intervals

## Objective
My goal was to understand why confidence intervals can fail and test how different bootstrap methods affect interval coverage.

## Methodology
- I examined a degenerate bootstrap using the median of 32,561 integer ages and checked why the bootstrap standard error was zero.
- I tested the coverage of nominal 95% confidence intervals using skewed simulated data with a sample size of 50 across 400 experiments.
- I compared parametric and bootstrap confidence intervals for both the mean and median.
- I analyzed wage data from 25 firms to see how treating workers as independent observations affected confidence intervals.
- I compared resampling individual workers with resampling entire firms to account for clustering.
- I used `bootstrap_utils.py`, which contained percentile, i.i.d., and cluster bootstrap functions.
- I asked AI to write a coverage function, revised my prompt once, and compared its output with my own results.

## Key Findings
- **Degenerate bootstrap:** The bootstrap standard error for the median was 0, and the BCa method returned `nan` with a warning instead of a confidence interval.
- **Mean coverage:** The parametric interval achieved 92.5% coverage, while the bootstrap interval achieved 92.0%, both below the nominal 95%.
- **Median coverage:** The parametric interval covered the true median only 66.8% of the time, compared with 92.8% for the bootstrap interval.
- **Clustered data:** Treating workers as independent produced an interval 5.7 times too narrow, with only 19.5% coverage. Resampling entire firms increased coverage to 91.0%.
- **AI verification:** After revising my prompt once, I checked the AI-generated coverage function against my own calculations. Both results matched exactly.

## Conclusion
I learned that confidence intervals can give misleading results when the data are discrete, skewed, or clustered. I also found that choosing a resampling method that matches the structure of the data matters for getting accurate coverage. By checking the AI-generated function against my own results, I confirmed that it reproduced my calculations.
