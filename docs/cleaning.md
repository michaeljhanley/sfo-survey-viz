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

I chose to execute the entire project in Excel for the following reasons:
- Excel is widely available, well-document, and relatively easy for stakeholders with a limited programming background to understand and use.
- Excel skills continue to be in high demand among employers looking for data workers.
- The program does have some built-in statistical analysis functionality, but some parts need to be done manually. This challenges the user to understand some of the more minute calculations than some other tools that abstract more of the statistical calculations.

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

### Decoding
- **Action Taken**: Decoded responses from integers to their corresponding string data
- **Rationale**: The datasets are small enough that Excel will be able to process these easily. Having human-readable categories makes pivoting and charting easier later.
- **Implementation Details**:
    - Made lookup tables for and Q3GETTO1 and Q21INCOME
    - Used XLOOKUP function to automatically replace those columns with the appropriate string data

### Feature Engineering
- **Action Taken**: Added 'is_business' column to 2017's data.
- **Rationale**: Decodes data into useful categories for analysis/pivoting without the need for an extensive lookup table, since we're only interested in two categories.
- **Implementation Details**:
    - Used IF function to convert Q22FLY data into 'Business' or 'Other'
    - Replaced the original column's values with these calculations.

## Final Dataset Characteristics

- Final Row Count: 3,087 (2016), 2,831 (2017)
- Final Column Count: 3 (2016), 5 (2017)
- Missing Data Summary: N/A
- Known Limitations:
    - Respondents were allowed to select more than one transportation mode and travel reason. The ones that did constituted a fraction of a percent of the overall data. For the purposes of this exercise, I chose to omit the extra data so as not to over- or undervalue responses. If I had more information about the survey's methodology, I would be open to making a different decision on that depending on how the data was collected.

## Challenges and Solutions

### Major Challenges
Duplicate Rows
Impact: Excel's built-in functionality for deleting duplicate rows is straightforward, but identifying duplicate rows is limited to workarounds, even in powerful tools like Power Query. This is important, because knowing what you're working with is important before you decide how to handle duplicate rows.
Solution implemented: No duplicates were found this time. If there were any, I'd add the dataset(s) to Power Query and use grouping to identify duplicates.
Effectiveness: N/A

## Future Improvements

### What I Would Do Differently
Document as I go along
Why this would be better: Python and R have notebook workflows available for iterative problem-solving and inline explanation step by step. Excel has no such feature, so documenting an in-progress project requires some extra initiative.
How it would improve the process: This would ensure the project is completed along with its documentation. Summarizing the work done in the moment could also inspire some critical thinking about alternative solutions to cleaning problems.
Resources needed: Note-taking software

## Notes and Observations

None at this time.