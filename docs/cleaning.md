# Excel Data Preprocessing Documentation (WIP)

## Table of Contents
1. [Overview](#overview)
2. [Dataset Information](#dataset-information)
3. [Preprocessing Steps](#preprocessing-steps)
4. [Data Quality Checks](#data-quality-checks)
5. [Final Dataset Characteristics](#final-dataset-characteristics)
6. [Challenges and Solutions](#challenges-and-solutions)
7. [Future Improvements](#future-improvements)
8. [Notes and Observations](#notes-and-observations)

## Overview

This document outlines the data cleaning and preprocessing steps performed in Excel before analysis. It includes the rationale behind each decision, challenges encountered, and potential future improvements.

## Dataset Information

- Original Data Source: DataSF ([2016](https://data.sfgov.org/Transportation/2016-SFO-Customer-Survey/t3vr-buhp/about_data), [2017](https://data.sfgov.org/Transportation/2017-SFO-Customer-Survey/nnh5-5rwz/about_data))  
- Time Period Covered: 2016 and 2017  
- Initial File Format: .csv  
- Initial Row Count: 3,087 (2016), 2,831 (2017)  
- Initial Column Count: 97 (2016 and 2017)  

## Preprocessing Steps

### Determine Necessary Columns
- **Action Taken**: Narrowed the list of columns to only the ones necessary to analyze rideshare use (total over time, income in 2017, reason for travel in 2017)
- **Rationale**: This step focuses future cleaning and analysis efforts on only the data we need.
    - 'RESPNUM' (2016, 2017) allows us to count the number of unique responses belonging to each response category
        - Retrieving 2 years of data allows us to compare trends year-over-year
    - 'Q3GETTO1' (2016, 2017) helps us determine the primary transportation method respondents used to arrive at SFO
    - 'Q21INCOME' (2017) gives us the respondent's income bracket
    - 'Q22FLY' (2017) provides the respondent's reason for travel
    - 'WEIGHT' (2016, 2017) lets us know how much each individual response should count for. This allows us to make inferences about the survey's representation of the whole population of SFO travelers.
- **Implementation Details**:
    - .csv converted into .xlsx
    - Extraneous columns were deleted in Excel

### Check Uniqueness Constraints
- **Action Taken**: Searched datasets for duplicate rows for further investigation
- **Rationale**: If entered erroneously, extra copies of information could result in false analyses
- **Implementation Details**:
    - Used a single COUNTIFS formula to check for the number of duplicate rows
    - No duplicates found

### Missing Data
- **Action Taken**: Searched all columns for empty/NULL cells.
- **Rationale**: Data that is unintentionally omitted could skew results.
- **Implementation Details**:
    - Used a single COUNTBLANK formula on the datasets' ranges to count the number of blank cells
    - No blank cells found

### Data Range Constraint Checks
- **Action Taken**: Checked all relevant numeric columns to ensure values fall within expected ranges
- **Rationale**: Values outside of expected ranges indicate possible data entry errors. Since each response corresponds to a response code, this could result in responses that are unable to be counted or analyzed.
- **Implementation Details**:
    - The range of numbers found on the code list is narrow, so here, I chose to turn the datasets into tables and visually inspect the column filters to ensure all values were integers in the expected range.
        - I found no erroneous entries.
    - Note: 'RESPNUM' doesn't need to be checked in detail this case, because the expected range is directly related to the number of rows in the dataset. This is because we haven't had to delete any rows this far. This can be verified with a simple visual check.

### [Step Name]
- **Action Taken**:
- **Rationale**:
- **Implementation Details**:

## Data Quality Checks

### Consistency Checks Performed:
[List specific checks]
[Results and actions taken]

### Validation Methods:
[Describe validation approaches]
[Results and implications]

## Final Dataset Characteristics

Final Row Count: [Number]
Final Column Count: [Number]
Missing Data Summary: [Overview of any remaining missing data]
Known Limitations: [Document any known issues or limitations]

## Challenges and Solutions

### Major Challenges
[Challenge Description]
Impact:
Solution implemented:
Effectiveness:

[Challenge Description]
Impact:
Solution implemented:
Effectiveness:

## Future Improvements

### What I Would Do Differently
[Alternative Approach]
Why this would be better:
How it would improve the process:
Resources needed:

### Additional Steps for Next Time
[New Step or Process]
Purpose:
Expected benefit:
Implementation approach:

### Process Expansion Ideas
[Additional data quality checks to implement]
[New validation steps to consider]
[Automation opportunities]
[Additional documentation needs identified]

## Notes and Observations

[Any additional insights gained during preprocessing]
[Unexpected patterns or anomalies discovered]
[Decisions that might affect analysis]