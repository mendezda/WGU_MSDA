# Market Basket Analysis with Apriori Algorithm

## Summary

This project uses Market Basket Analysis to uncover frequently purchased item combinations from a telecom product dataset.

**Research Question**:  
Can Market Basket Analysis uncover which items are frequently purchased together by telecom customers?

The goal is to identify associations among products to inform bundling strategies, promotions, and recommendation systems.

## Tools Used

- Python
- pandas, numpy, matplotlib, seaborn
- mlxtend (`TransactionEncoder`, `apriori`, `association_rules`)

## Preprocessing

- Loaded telecom transaction data with up to 20 items per transaction
- Removed transactions with no recorded items
- Transformed dataset into a one-hot encoded boolean matrix using `TransactionEncoder`
- Removed columns with `NaN` (missing item names)
- Final dataset: 7,501 transactions and 119 distinct items

## Modeling

- Applied Apriori algorithm with a minimum support of 2% to generate frequent itemsets
- Generated association rules with:
  - Minimum `lift` threshold = 1
  - Key metrics: `support`, `confidence`, `lift`, `leverage`, `conviction`
- Top 3 rules were identified by:
  - Highest support
  - Highest confidence
  - Highest lift

## Results

### Top Association Rules:

- **By Support**:
  - `Dust-Off Compressed Gas 2 pack` → `HP 61 ink`  
  - Support: 5.3%, Confidence: 22.1%, Lift: 1.35

- **By Confidence**:
  - `10ft iPhone Charger Cable 2 Pack` → `Dust-Off Compressed Gas 2 pack`  
  - Confidence: 45.6%, Lift: 1.91

- **By Lift**:
  - `SanDisk Ultra 64GB card` → `VIVO Dual LCD Monitor Desk mount`  
  - Lift: 2.29, Confidence: 39.9%

### Key Findings:

- Dust-Off Compressed Gas 2 pack appeared frequently in strong rules, suggesting high cross-sell potential
- Lift values > 1 for all rules indicate strong positive associations between item pairs

## Notes

- Suggested actions include bundling popular item pairs and displaying highly associated items in "Frequently Bought Together" sections
- Confidence values above 40% highlight strong cross-sell opportunities
- Market Basket Analysis can be used to guide promotional design, shelf placement, and e-commerce recommendations
