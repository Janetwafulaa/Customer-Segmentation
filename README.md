# Customer Segmentation using Machine Learning

This project explores **customer segmentation** on the datasets.  
The workflow covers data cleaning, aggregation, visualization, dimensionality reduction, clustering, and evaluation.

---

##  1. Data Cleaning
Steps taken:
- Checked for **missing values** and removed rows with missing key fields (e.g., Age, Income).
- Detected and flagged **unrealistic values** (e.g., negative or zero Age/Income).
- Dropped **duplicate rows** (none found in this dataset).
- Filtered out **records where Age < 18**.
- Standardized column names for consistency.

---

## 2. Feature Engineering & Aggregation
- Created **Age Bins** (`Young`, `Adult`, `Senior`) using `pd.cut`.
- Generated **Spending Level** categories using `pd.qcut` on the Spending Score.
- Added derived metrics:
  - **Income-to-Age Ratio**
  - **High-Value Customer Flag** (customers with above-average income and spending).
- Aggregated statistics:
  - Average Income by Gender.
  - Average Spending Score by Age Groups & Gender.
  - Cluster Profiles (mean Age, Income, Spending per cluster).

---

## 3. Data Visualization
Exploratory plots:
- **Histogram** of Age distribution.
- **Bar chart** of average Spending Score by Gender.
- **Scatter plot** of Annual Income vs Spending Score.
- **Boxplot** of Spending Score by Age Groups.
- **Pivot Table** & heatmaps for Gender × Age Group analysis.

---

## 4. Dimensionality Reduction (PCA & t-SNE)
- Standardized **Annual Income** and **Spending Score**.
- Ran **PCA**:
  - Plotted explained variance ratio to choose components.
  - Visualized 2D PCA projection colored by Gender.
- Ran **t-SNE**:
  - Visualized 2D embeddings to reveal finer clusters.
- **Comparison**:
  - PCA preserves global structure.
  - t-SNE shows clearer, compact local clusters.

---

## 5. Clustering
### K-Means
- Ran K-Means for **k = 2…10**.
- Plotted **Elbow Curve** to identify optimal k.
- Computed **Silhouette Score** for each k.
- Chose **k = 5** (optimal balance).
- Visualized clusters on Income vs Spending scatter plots.

### Hierarchical Clustering
- Performed **Agglomerative Clustering (Ward linkage)**.
- Visualized **dendrogram** to decide the number of clusters.
- Cut dendrogram at **k = 5**.
- Compared assignments to K-Means using **Adjusted Rand Index (ARI)**.

---

## 6. Cluster Profiling
For each cluster (both K-Means & Hierarchical):
- Calculated **average Age, Annual Income, and Spending Score**.
- Counted cluster sizes.
- Identified distinct segments:
  - **Young High Spenders**
  - **Older Low Spenders**
  - **Middle Income Balanced**
  - etc.

---

## 7. Evaluation
- Compared cluster stability using **different random states** in K-Means.
- Used **ARI** to compare runs → clusters stable due to `n_init=10`.
- Compared K-Means vs Hierarchical results numerically & visually.
- Exported final dataset with cluster labels to CSV.

---

## Key Learnings
- Feature scaling is crucial before PCA/Clustering.
- PCA helps reduce noise, but t-SNE gives more intuitive clusters.
- K-Means is sensitive to initialization but stable with multiple runs.
- Hierarchical clustering provides interpretability but is computationally heavier.
- Profiling clusters is critical for business insights.

---


