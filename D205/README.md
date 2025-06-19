# Data Acquisition

This course develops SQL skills and introduces relational databases. Students perform data transference and manipulation tasks as part of the early stages in the data analytics lifecycle.

## Competencies
- Examine data for quality, dimensions, and relationships
- Implement physical data models
- Perform table operations and queries

# Joining SQL Tables to Analyze Churn and Online Backup Usage

## Summary

This project uses PostgreSQL to join customer data and service data, creating a contingency table to determine the relationship between customer churn and online backup service enrollment.

**Research Question**:  
Were there more clients that churned who were enrolled in the online backup service than clients that churned and were not enrolled in the online backup service?

The goal is to use SQL joins and filtering to generate actionable summaries that can help stakeholders evaluate whether online backup usage is associated with reduced churn.

## Tools Used

- PostgreSQL
- SQL (psql environment)
- Services and customer data in CSV format

## Preprocessing

- Created a new `services` table with `customer_id` as the primary key
- Loaded external `Services.csv` file into the `services` table using `COPY` command
- Enforced referential integrity via one-to-one join between `customer` and `services` tables on `customer_id`

## Modeling

- Wrote SQL query to:
  - Join `customer` and `services` tables
  - Count churned and non-churned clients grouped by `online_backup` status
  - Return counts using conditional aggregation (`CASE WHEN`) and `GROUP BY`
