# Customer Segmentation with K-Means Clustering

## Summary

This project applies K-means clustering to identify distinct customer segments using continuous attributes such as income, age, tenure, and bandwidth usage.

**Research Question**:  
Can K-means clustering uncover meaningful, distinct patterns from continuous customer attributes?

The goal is to inform stakeholder decision-making by segmenting customers into groups based on similar behaviors and characteristics.

## Tools Used

- Python
- pandas, matplotlib
- scikit-learn (`RobustScaler`, `KMeans`, `silhouette_score`)

## Preprocessing

- Dropped irrelevant and incomplete variables; retained six key continuous attributes
- Confirmed no duplicate rows and no missing values in selected variables
- Used `RobustScaler` to mitigate the effect of outliers and standardize variables
- Created subset of scaled numerical features:
  - `Income`, `Age`, `Outage_sec_perweek`, `Tenure`, `MonthlyCharge`, `Bandwidth_GB_Year`

## Modeling

- Optimal number of clusters (K) determined using the elbow method and silhouette scores
- K = 3 was selected as optimal (Silhouette Score ≈ 0.203)
- Cluster centroids were analyzed to understand each group’s characteristics
- Clustering was done on scaled features using `KMeans` with `n_clusters=3`

## Results

**Silhouette Score**: 0.203  
**Cluster Profiles**:

- **Cluster 0**: Average income, longest tenure, highest bandwidth usage  
- **Cluster 1**: Average income, short tenure, low bandwidth usage  
- **Cluster 2**: High income, average tenure and usage  

**Demographics**:
- Cluster 0: Avg income ≈ $29.6k, tenure ≈ 60 months, 51% female  
- Cluster 1: Avg income ≈ $29.5k, tenure ≈ 9 months, 49% female  
- Cluster 2: Avg income ≈ $87.7k, tenure ≈ 33 months, 53% female  

## Notes

- Clustering was sensitive to feature scaling and cluster shape assumptions
- The silhouette score suggests the clusters are only moderately well-separated
- Recommended next steps:
  - Explore other clustering methods (e.g., DBSCAN or GMM)
  - Use additional attributes (e.g., categorical features)
  - Develop tailored strategies for each segment:
    - Cluster 0: Loyalty rewards for high-usage, long-tenure customers
    - Cluster 1: Incentives for engagement and retention
    - Cluster 2: Premium offers for high-income customers
