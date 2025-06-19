# Advanced Data Acquisition

Expands on foundational SQL skills by introducing advanced operations, data aggregation, and integration from multiple sources to support organizational analytics needs.

## Competencies
- Apply advanced SQL to integrate data sources
- Explore and acquire data from various sources

# Telecom Churn Dashboard Using SQL and Tableau

## Summary

This project combines two telecom churn datasets—one from WGU and one from Maven Analytics—to create an interactive Tableau dashboard comparing churn trends across companies.

The dashboard provides stakeholders with insights into churn patterns by gender, tenure, and contract type. It is designed to help monitor and compare churn metrics against competitors over time.

## Tools Used

- Tableau
- Tableau Prep
- pgAdmin (PostgreSQL)
- SQL

## Preprocessing

- Cleaned and renamed fields in Tableau Prep for schema matching
- Removed non-matching or redundant fields from the competitor dataset
- Encoded churn responses into binary format ("Yes"/"No")
- Created a "Source" column to distinguish between datasets
- Joined WGU tables: `contract`, `customer`, `location`, and `payment`
- Unioned the WGU data with the competitor data
- Exported the unified dataset to `churn_union.csv` and imported it into PostgreSQL via pgAdmin
- Defined `customer_id` as the primary key

## Modeling

- Built SQL table `churn_union` with fields for customer demographics, churn status, and billing details
- Loaded data into Tableau via a PostgreSQL connection
- Created eight visualizations in Tableau:
  - Churn Map
  - Churn Rate by Company
  - Percent of Churn (Pie Chart)
  - Contract Duration by Gender
  - Average Tenure Table
  - Average Monthly Charge Table
  - Average Tenure vs. Duration (Bar Chart)
  - Churn Rate vs. Duration (Bar Chart)
- Organized worksheets into a Tableau Story with three interactive dashboards

## Results

- Month-to-month customers had the highest churn rate in both datasets
- Male customers at WGU had slightly higher churn rates than other demographics
- Churn trends between the WGU dataset and competitor data were largely comparable
- Contract duration and tenure emerged as key indicators of churn risk

## Notes

- Limitation: The LOD (LabsOnDemand) database had limited fields, reducing analytical depth
- The dashboard is filterable by churn status and source, and each visualization acts as a filter
- Future iterations could incorporate richer datasets for more granular insights into churn behavior
