# 📋 Changelog — Crowd Decoder

All notable changes to this project are documented here.  
Format: [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)

---

## [1.0.0] — 2026-11-21 — *Initial Release*

### ✅ Added

**Task 1 — Data Loading & EDA**
- Load `Mall_Customers.csv` (200 customers × 5 columns) straight from this repository's raw link — no upload needed in Colab
- `.head()`, `.info()`, `.describe()`, missing-value and duplicate checks (0 and 0)
- Dropped `CustomerID`; renamed columns to `Annual_Income` and `Spending_Score`; `LabelEncoder` on `Gender` (Female = 0, Male = 1)
- Histograms with KDE, pairplot, correlation heatmap and a raw Income vs Spending scatter
- EDA summary: 5 observations + the feature-pair rationale

**Task 2 — Feature Scaling & Selection**
- `StandardScaler` on `Age`, `Annual_Income`, `Spending_Score` → `df_scaled`
- Manual z-score check against the library output
- `df_2f` (Annual_Income + Spending_Score) for the primary clustering
- Markdown on why distance-based clustering needs scaling

**Task 3 — K-Means Clustering**
- Elbow Method (k = 1–10) and Silhouette Score (k = 2–10) → k = 5 (Silhouette 0.5547)
- `KMeans(n_clusters=5, random_state=42, n_init=10)` → `KMeans_Cluster`
- Centroids shown in original units (verified against `cluster_centers_`) and marked as black X
- Cluster profile table with segment names and business interpretation

**Task 4 — Agglomerative Hierarchical Clustering**
- Ward linkage dendrogram with a cut line at height 7 → 5 clusters
- `AgglomerativeClustering(n_clusters=5, metric='euclidean', linkage='ward')` → `Hier_Cluster`
- Side-by-side comparison with K-Means: 196 of 200 customers agree (98%)
- Segment-wise profile comparison with K-Means

**Task 5 — DBSCAN**
- 4-NN k-distance plot → eps ≈ 0.4
- Grid search over eps 0.2–0.6 × min_samples 3–6 (clusters, noise, Silhouette)
- `DBSCAN(eps=0.4, min_samples=4)` → 3 clusters + 14 noise points (`DBSCAN_Cluster`)
- Conceptual comparison of all three algorithms (8 points)

**Task 6 — Algorithm Comparison & Business Insights**
- Three-panel comparison figure on the same axes
- Metrics table: Silhouette, Davies–Bouldin and Calinski–Harabasz for all three algorithms
- Business report: 5 segments, one marketing action each, K-Means recommended
- `kmeans.predict()` demo for a new customer + an extension with all 4 features

**Task 7 — Notebook Quality**
- Clean Restart & Run All (0 errors), HTML export and pinned `requirements.txt`

**Supporting Files**
- `README.md` — full cinematic project documentation
- `images/` — banner, story and insights graphics + the social-preview cover
- `screenshots/` — 14 key plots exported straight from the notebook
- `LICENSE`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `CITATION.cff`, `setup.cfg`, `.gitignore`, `.gitattributes`

### 🔧 Pre-release Fixes
- Three-panel figure: noise points are now filtered after the segment column exists (fixed a seaborn `hue` error)
- Overlapping legends moved to one shared figure legend (K-Means vs Hierarchical, 2 vs 4 features)
- Two rounded numbers corrected in the markdown (Calinski–Harabasz 248.6, 4-feature Silhouette 0.356)
- Dollar signs removed from the markdown so the HTML export doesn't render them as math
- Tested on an older Colab-like stack (pandas 2.2, scikit-learn 1.6) — same results

---

## [0.1.0] — 2026-11-20 — *Development Build*

- Notebook structure created with all 7 tasks
- Clustering results and plots drafted

---

*Crafted by **THE PARTH SHAH** — Red & White Skill Education, Surat · November 2026*
