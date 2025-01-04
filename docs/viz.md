# SFO Transportation Analysis: Rideshare Usage Patterns (2016-2017)

## Project Overview
This document details the methodology of visualizing San Francisco International Airport (SFO) survey data, focusing on rideshare usage patterns across different demographic groups and time periods.

### Research Foci
1. Rideshare usage by income bracket
2. Rideshare usage by trip purpose (business vs. non-business)
3. Rideshare usage comparison between 2016 and 2017

## Visualizations

### Year-over-Year Rideshare Usage (Slopegraph)
<img src="https://raw.githubusercontent.com/michaeljhanley/sfo-survey-viz/refs/heads/main/visualizations/slopegraph_v2.png" width="450" />

**Design Choices:**
- I chose a slopegraph for the following reasons:
    - It allows me to compare changes over two periods of time.
    - It displays both the proportions (points) and the rate change between them (lines) in a way that's immediately easy to understand.
- Key design decisions:
    - I chose to bundle more transportation options into the "Other" category. Now that we've determined statistical significance, I thought that fewer lines on the graph would allow me to make the main point clear.
    - The rideshare label, points, and line are dark teal, while the rest of the categories are shades of gray. This allows the viewer to tell the difference between the other categories while drawing the eye right to the rideshare data I want them to zero in on.
    - I chose to graph proportions instead of absolute counts of weighted responses because of the different samples sizes from year to year.

**Key Findings:**
- Rideshare usage has increased between 2016 and 2017, becoming the number one transportation method for reaching SFO.

### Income Level Analysis (Stacked 100% Bar Chart)
<img src="https://raw.githubusercontent.com/michaeljhanley/sfo-survey-viz/refs/heads/main/visualizations/horiz_stacked_v2.png" width="450" />

**Design Choices:**
- I chose to use a stacked bar chart for the following reasons:
    - It quickly conveys the differences between the first and last categories
    - 100% normalization makes for an intuitive comparison of normalized proportions as opposed to absolute value counts.
    - Proportion sizes are easier to compare than other "part-of-whole" visualizations, like pie or donut charts
- Key design decisions:
    - The legend goes on the top-right in order to line up with the legend on the clustered bar chart
    - The same dark teal color is used to direct the eye to the rideshare data right away

**Key Findings:**
- Higher annual traveler income is associated with higher rates of rideshare app use

### Travel Purpose Analysis (Clustered Bar Chart)
<img src="https://raw.githubusercontent.com/michaeljhanley/sfo-survey-viz/refs/heads/main/visualizations/vert_clustered_v2.png" width="450" />

**Design Choices:**
- I chose a clustered bar chart because:
    - My intent was to highlight the difference between the the proportions of business and non-business travelers using rideshare apps.
        - I only needed to highlight the difference between one instance of the pair of travel reasons - clustered bars excel at this.
        - More travel reasons to compare would have required a different, less-crowded chart type.
- Key design decisions:
    - I chose to introduce the "steel green" and "dark pink" colors to differentiate business vs. non-business
        - Continuing to use the dark teal on the bars as before could have been confusing.
    - I chose to use the dark teal on the "Rideshare" axis label, as well as a faint gray rectangle, to highlight the data points of interest.
    - One limitation of the clustered bar is that it's difficult to represent proportions while accounting for scale
        - In other words, this visualization doesn't make it clear that non-business travelers significantly outnumber business travelers.
        - I chose the bar chart because the difference in proportion was the main point I wanted viewers to walk away with.
        - I experimented with stacked vertical bar charts of absolute counts, intending to give a sense of both scalem and proportion.
            - When I tested it on friends and family, they found it confusing, even with annotations and data labels.
            - In contrast, folks understood the message right away when I switched to a clustered bar.

**Key Findings:**
- A higher proportion of business travelers use rideshare apps compared to non-business travelers.

## Key Insights
<img src="https://raw.githubusercontent.com/michaeljhanley/sfo-survey-viz/refs/heads/main/visualizations/viz_combined_v2.png" />
- Rideshare usage has increased between 2016 and 2017, becoming the number one transportation method for reaching SFO.
- Business travelers and high-income travelers are more likely to use rideshare apps to reach SFO than their counterparts.
- These findings are statistically significant, but note that the effect size is relatively weak (V = 0.11-0.13)

## Limitations & Considerations [WIP]

## Future Improvements [WIP]

## Tools & Resources
- Excel