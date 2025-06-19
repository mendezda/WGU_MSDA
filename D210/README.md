# Representation and Reporting

Focuses on storytelling, visualization, and communication of data-driven insights through dashboards, audio representations, and executive tools.

## Competencies
- Communicate data insights to all audiences
- Create data visualizations
- Design interactive executive decision tools

# Telecom Churn Dashboard

## Summary

This project uses an internal churn dataset and an external competitor dataset to create an interactive Tableau dashboard. The dashboard helps stakeholders monitor churn patterns and contract trends across two telecom providers.

**Research Question**:  
How can a Tableau dashboard help visualize customer churn and support contract-related insights?

## Tools Used

- Python (pandas)
- Tableau Public

## Preprocessing

- Combined two datasets (WGU and competitor) using `pandas.concat()`
- Standardized column names and formats
- Added a `Company` field to distinguish sources
- Filled missing values (e.g., `InternetService = "None"`)

## Dashboard

[View Dashboard on Tableau Public](https://public.tableau.com/app/profile/drew.mendez/viz/D210_PA_MendezD_Task1/D210RepresentationandReporting)

## Results

- WGU Telecom shows lower churn than the competitor
- Male customers churn at higher rates in WGU’s data
- Dashboard supports contract-targeted retention strategies

## Notes

- Data storytelling follows Microsoft and Tableau best practices
- Designed for executive stakeholders
