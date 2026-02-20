# Patient Segmentation Analysis Using K-Means Clustering

---

# Executive Summary

This whitepaper presents the findings of an unsupervised machine learning study conducted to identify structured patient segments within a hospital system. The analysis focuses on female patients and evaluates whether demographic and financial indicators reveal meaningful subgroup patterns.

Using K-Means clustering with standardized continuous variables, the study identified eight operationally distinct patient segments. While statistical separation between clusters was moderate, the segmentation reveals actionable demographic-cost profiles that can inform targeted care programs, financial planning, and strategic resource allocation.

The primary insight is that even moderate clustering quality can yield operational value when interpreted within real-world healthcare context.

---

# Methodology

## Data Scope

The original dataset contains 10,000 patient records and 50 variables. For this study:

* The dataset was filtered to female patients
* Six continuous variables were selected

Selected variables:

* Children (household size indicator)
* Age
* Income
* DocVisits
* TotalCharge
* AdditionalCharges

Categorical medical condition variables were excluded due to the distance-based assumptions of K-Means clustering.

## Data Preparation

Because K-Means relies on Euclidean distance, all variables were standardized using StandardScaler.

Standardization ensured:

* Equal weighting across features
* Prevention of high-magnitude financial variables dominating cluster formation
* Balanced geometric representation in feature space

A pipeline was constructed to integrate scaling and clustering for consistent preprocessing.

## Cluster Selection Process

Two complementary evaluation methods were applied:

### 1. Elbow Method (Inertia)

* Measured within-cluster sum of squared distances
* KneeLocator identified an elbow near k ≈ 8
* Diminishing marginal reduction in inertia beyond eight clusters

### 2. Silhouette Analysis

* Evaluated separation quality
* Scores ranged between 0.17 and 0.19
* Highest score at k = 2

Despite slightly stronger statistical separation at k = 2, eight clusters were selected to provide greater operational granularity for decision-makers.

## Dimensionality Reduction

Principal Component Analysis (PCA) reduced six variables into two dimensions for visualization.

Cluster centroids were calculated as the mean of standardized feature values within each segment.

---

# Operational Interpretation

Although silhouette scores indicate moderate overlap between clusters, segmentation reveals structured demographic-financial patterns.

### Example Segment: Elderly Moderate-Income, High Additional Charges

* Average Age: 77.97
* Average Income: ~$40,000
* Average DocVisits: 5.23
* Average AdditionalCharges: ~$25,830

This segment reflects older patients with disproportionate additional charges relative to income.

### Example Segment: Middle-Aged, High-Income Group

* Average Age: ~51
* Income: ~$104,000
* Moderate utilization patterns
* Lower AdditionalCharges relative to elderly segment

These profiles highlight meaningful differences in cost distribution and utilization behavior across demographic groups.

Importantly, healthcare populations rarely separate into perfectly distinct clusters. Moderate silhouette values reflect real-world complexity rather than model failure.

---

# Strategic Recommendations

Based on segmentation findings, the following actions are recommended:

1. Conduct targeted cost analysis for elderly high-charge segment to identify preventable expense drivers.
2. Develop chronic care management programs tailored to high-utilization elderly patients.
3. Offer preventive wellness or premium engagement programs for higher-income middle-aged segment.
4. Expand feature set in future analyses to include medical conditions and service types using mixed-type clustering methods (e.g., k-prototypes).
5. Conduct longitudinal follow-up studies to evaluate cost trajectory by cluster.

---

# Limitations

* Moderate silhouette scores indicate overlapping clusters
* Only six continuous variables were included
* Categorical health indicators were excluded
* PCA visualization compresses multidimensional nuance

These limitations suggest segmentation can be strengthened with broader feature inclusion.

---

# Conclusion

This study demonstrates that demographic and financial indicators can reveal operationally meaningful patient segments, even when statistical separation is moderate.

The findings support the use of segmentation analytics as a strategic tool for:

* Resource allocation
* Cost management
* Preventive care planning
* Targeted patient engagement

Future efforts should prioritize expanded feature inclusion and alternative clustering algorithms to enhance segmentation precision while preserving operational interpretability.
