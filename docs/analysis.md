# SFO Airport Survey Data Analysis [WIP]

## Overview
This document details the methodology and findings from analyzing San Francisco International Airport (SFO) survey data, focusing on rideshare usage patterns across different demographic groups and time periods.

## Data Processing Methodology

### Pivot Table Creation
Three pivot tables were created from the original survey dataset to examine specific relationships:
1. Rideshare usage by income bracket
2. Rideshare usage by trip purpose (business vs. non-business)
3. Rideshare usage comparison between 2016 and 2017
Note that the statistical tests were conducted on data after weights were applied. This is why response counts pivoted into decimals as opposed to integers. I accomplished this by making pivot tables with values that summed the WEIGHT values per category instead of counting the number of RESPNUMs per category.
   - WEIGHT values were provided by the original dataset

### Removing "connecting flight" and "Carshare" response data
On the original survey, respondents were able to choose "Connecting from another flight" as their method of arriving at SFO. I chose to not consider these responses because this type of arrival doesn't have any direct bearing on the other arrival methods. In addition, travelers arriving at SFO using this option generally don't get to choose other methods, as air travel implies that a majority of travelers arriving by connecting flight live too far to use other modes.\

Additionally, "Carshare (Zipcar, etc.)" data was omitted from analysis because it was not provided as a response option on the 2017 survey. Due diligence was made to ensure all other response numbers lined up, with slight limitations (see "Limitations and Considerations")

Finally, "Blank" and "not used" were omitted from analysis for self-evident reasons.

### Category Consolidation
To ensure statistical validity for chi-square testing, categories with low response counts were consolidated into an "other" category. This process followed these guidelines:
- Minimum threshold: 5 or more responses required in both expected and observed frequency tables
- Categories below this threshold were combined into an "other" category
- This consolidation ensures the chi-square test assumptions are met and results are statistically valid
**Categories included in the analysis-level "Other" variable**:
   - Company rented bus/cruise ship bus/other group arrangements
   - SamTrans bus/or 'bus' (carrier unspecified)
   - Limo/town car
   - Door-to-door van service
   - Other (response available in the original survey)

## Statistical Analysis

### Research Questions and Hypotheses

1. Income Bracket Analysis
   - Research Question: Is rideshare use significantly different among travelers of different income brackets?
   - Null Hypothesis (H₀): There is no significant relationship between income bracket and rideshare usage
   - Alternative Hypothesis (H₁): There is a significant relationship between income bracket and rideshare usage

2. Trip Purpose Analysis
   - Research Question: Is rideshare use significantly different among business vs. non-business travelers?
   - Null Hypothesis (H₀): There is no significant relationship between trip purpose and rideshare usage
   - Alternative Hypothesis (H₁): There is a significant relationship between trip purpose and rideshare usage

3. Year-over-Year Comparison
   - Research Question: Was the increase in rideshare usage from 2016 to 2017 statistically significant?
   - Null Hypothesis (H₀): There is no significant difference in rideshare usage between 2016 and 2017
   - Alternative Hypothesis (H₁): There is a significant difference in rideshare usage between 2016 and 2017

### Methodology
Chi-square tests of independence were performed on each pivot table to test the hypotheses. This test was chosen because:
- It's appropriate for categorical data
- It can determine if there are significant relationships between categorical variables
- It works well with the frequency data in our pivot tables
While Excel does provide tools for chi-square tests (see "Results" section), the input requires manual calculation of expected counts. I did so by filling a new table using simple multiplication and division formulas with cell references.

## Results
As noted above, tests were conducted using Excel's CHISQ.TEST function. This takes a range of observed counts and a range of expected counts as its arguments. It abstracts caclulations of chi-square statistic and degrees of freedom
Year-Over-Year Comparison (2016-2017)
- Chi-square statistic: χ²(8) = 76.01 
- P-value: p < 0.001
- Effect size: V = 0.13
- Sample size (weighted): n = 4,563
- **Interpretation of findings**: The chi-square test revealed a significant change in rideshare usage between 2016 and 2017, with a small effect size (V = 0.13). This indicates that while the increase in rideshare usage was statistically significant, the magnitude of the change was relatively modest.

Income Bracket Analysis
- Chi-square statistic: χ²(24) = 93.8
- P-value: p < 0.001
- Effect size: V = 0.13
- Sample size (weighted): n = 1,752
- **Interpretation of findings**: Analysis showed a significant relationship between income brackets and rideshare usage, with a small effect size (V = 0.13). This suggests that while income level does influence rideshare usage, the strength of this relationship is relatively modest.

Business vs. Non-Business Travel Analysis
- Chi-square statistic: χ²(8) = 23.94
- P-value: p = 0.002
- Effect size: V = 0.11
- Sample size (weighted): n = 2,121
- **Interpretation of findings**: The relationship between trip purpose and rideshare usage was significant, with a small effect size (V = 0.11). This indicates that while business travel status does influence rideshare usage, the magnitude of this effect is relatively small.

## Conclusions
[Insert conclusions drawn from the statistical analysis]

## Limitations and Considerations
- The analysis assumes random sampling in the survey data
- Category consolidation may impact the granularity of insights
- Chi-square tests show relationship existence but not direction or strength
- Differing survey wording

## Future Analysis Recommendations
[Insert recommendations for future analysis or data collection]