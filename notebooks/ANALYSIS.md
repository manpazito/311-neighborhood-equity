# Equity Analysis of 311 Service Requests in San Francisco

## Overview

This project analyzes equity in San Francisco’s 311 service request system by combining request-level administrative data with census tract–level socioeconomic and demographic data from the American Community Survey (ACS). The primary goal is to assess whether service access, responsiveness, and outcomes vary systematically across neighborhoods, and whether disparities persist after accounting for service type and workload.

The analysis proceeds in multiple stages, moving from descriptive spatial patterns to more rigorous, counterfactual equity diagnostics.

## Data Sources

- **311 Service Requests (San Francisco, 2023)**  
  Includes request location, service type, timestamps (opened/closed), responsible agency, and resolution status.
- **ACS Census Tract Data (5-year estimates, 2023)**  
  Includes median household income, poverty rate, renter share, educational attainment, and racial/ethnic composition.
- All service requests were spatially joined to census tracts to enable tract-level aggregation and comparison.

## 1. Spatial Distribution of 311 Requests

### What was done

- Counted total 311 requests per census tract.
- Mapped request density using choropleth maps.
- Created interactive maps allowing comparison between request volume and tract demographics.

### Key findings

- Request volume varies substantially across tracts.
- High request volume often aligns with dense, centrally located neighborhoods.
- Volume alone does not indicate equity: high-volume tracts may reflect greater need, greater awareness, or lower barriers to reporting.

## 2. Service Type Composition by Tract

### What was done

- Identified the most common service type in each census tract.
- Mapped dominant service categories spatially.
- Examined how service mix differs across neighborhoods.

### Key findings

- Certain services (e.g., street and sidewalk cleaning, graffiti, bulky items) dominate citywide.
- Some tracts show a narrow service mix, while others exhibit a broader range of requests.
- Differences in service composition motivate the need to control for service type when analyzing delays.

## 3. Request Resolution Time Analysis by Service Type

### What was done

- Computed resolution time (hours between opened and closed timestamps).
- Aggregated mean and median resolution times by service type.
- Restricted analysis to service types with sufficient sample sizes (≥20 resolved requests).

### Key findings

- Resolution times vary widely by service type.
- Some services exhibit long-tailed distributions, with a small number of extreme delays.
- This confirms that raw delay comparisons across neighborhoods must adjust for service mix.

## 4. Correlation Between Resolution Time and Socioeconomic Factors

### What was done

- Aggregated median resolution time at the census tract level.
- Examined Pearson correlations between delay and:
  - Median household income
  - Median home value
- Visualized relationships with scatterplots and regression lines.

### Key findings

- Modest correlations exist between neighborhood socioeconomic characteristics and resolution time.
- However, correlation alone cannot distinguish between service mix effects, workload effects, and systemic inequities.

## 5. Silent Neighborhood Analysis (Reporting Equity)

### What was done

- Compared request volume against indicators of socioeconomic vulnerability.
- Identified tracts with high vulnerability but relatively low 311 usage.

### Key findings

- Some neighborhoods with higher renter shares and poverty rates generate fewer 311 requests than expected.
- This suggests potential barriers to reporting, such as limited awareness, language access issues, or lower trust in city services.
- Equity concerns may arise not only from slow responses, but also from under-reporting.

## 6. Counterfactual (Residual) Equity Analysis

### Purpose

To identify neighborhoods that experience slower service **than expected**, after accounting for service type, workload, and socioeconomic characteristics.

### What was done

- Built a request-level regression model predicting delay using:
  - Service type fixed effects
  - Median household income
  - Renter share
  - Request volume per tract
- Computed residuals (actual delay − predicted delay).
- Aggregated residuals to the tract level.
- Identified tracts with consistently positive residuals (slower than expected).

### Key findings

- Some tracts exhibit systematically longer delays even after controlling for observable factors.
- These tracts represent potential areas of operational or administrative inequity not explained by demand or service composition.

## 7. Robustness Check: Mean/Pearson vs. Median/Spearman

### What was tested

- Compared two approaches:
  - **Mean residuals + Pearson correlation** (sensitive to outliers)
  - **Median residuals + Spearman correlation** (robust to skewed distributions)

### Key findings

- Very low overlap between tracts identified by the two methods.
- Mean-based results are driven by rare but extreme delays.
- Median-based results capture tracts with consistently slower day-to-day service.
- For equity analysis, median-based and rank-based methods provide a more robust and representative measure of resident experience.

## Overall Conclusions

- Equity in 311 services is multidimensional:
  - Who reports
  - What services are requested
  - How quickly requests are resolved
- Raw averages can mask important disparities.
- After controlling for service mix and workload, some neighborhoods still experience systematically slower service.
- Robust methods reveal that lower-income and renter-heavy neighborhoods are more likely to face consistent delays rather than isolated extreme failures.

## Policy and Planning Implications

- Improving equity may require:
  - Targeted outreach in under-reporting (“silent”) neighborhoods
  - Monitoring residual delays, not just average response times
  - Service-specific performance benchmarks adjusted for neighborhood context
- Residual-based monitoring can serve as an ongoing equity diagnostic tool for city agencies.

## Limitations

- Observational analysis cannot establish causality.
- Administrative data may contain unobserved operational constraints.
- ACS data reflects multi-year averages rather than point-in-time conditions.
