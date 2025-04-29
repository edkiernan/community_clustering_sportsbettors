# community_clustering_sportsbettors

## Overview

This project explores user behavior in Daily Fantasy Sports (DFS) through clustering and community detection. By combining **K-means clustering** and **BigCLAM (Big Cluster Affiliation Model)**, we uncover archetypes of DFS users and latent social structures in the sports betting ecosystem.

The analysis is grounded in a real-world dataset of over 10,000 DraftKings users and aims to provide actionable insights for applications like:

- Targeted marketing and user engagement
- Fraud detection and regulatory oversight
- Understanding behavioral patterns in online sports betting

---

## Data Source

The dataset comes from the **Transparency Project**, part of the Division on Addiction at the Cambridge Health Alliance (a Harvard Medical School affiliate). It focuses on user behavior in **NFL-based DFS contests** between August 1, 2014 and September 30, 2015.

### Key Files

- `TacklingData5All.csv`: Aggregated user stats (e.g., entry fees, winnings, contest counts)
- `TacklingData6Play.csv`: Contest-type and sport-level breakdowns for each user

---

## Methods

### Clustering

- **Technique**: K-means clustering
- **Input features**: Scaled values from `TacklingData5All.csv`, including `TotFees`, `TotWinnings`, `nCont`, `nDays`, etc.
- **Dimensionality Reduction**: Principal Component Analysis (PCA)
- **Number of Clusters**: 6 (determined via elbow method)

#### Betting Archetypes Identified:

1. **Casual Players** – Low spenders, moderate activity, balanced outcomes
2. **Low Rollers** – High activity, low stakes, experienced grinders
3. **Problematic High-Stakes Bettors** – Infrequent, volatile, high-stakes betting
4. **One-Time Bettors** – Minimal engagement, likely event-driven
5. **Serious Regulars** – Active, balanced volume and skill
6. **High Rollers** – Elite, high-stakes users with massive returns

### Community Detection

- **Technique**: BigCLAM using user-user graph based on contest similarity
- **Edge Construction**: Based on similarity in contest types and league participation from `TacklingData6Play.csv`
- **Hyperparameters**:
  - Communities: 5
  - Learning rate: 5e-4
  - Iterations: 500
  - Community threshold: 0.01

#### Community Profiles:

- **Community 0**: Contest-exclusive users, low league overlap
- **Community 1**: High NBA participation, contest type skewed to "other"
- **Community 2**: All-league players, heavily favor "other" contests
- **Community 3**: Balanced contest-type participation
- **Community 4**: Most diverse contest participation, strong in 50/50 contests

### Integration

A **cross-analysis** between clusters and communities revealed overlap patterns:

- Cluster 1 (Low Rollers) strongly overlaps with Community 4
- Cluster 2 (Problematic Bettors) lacks clear community alignment
- Cluster 5 (High Rollers) overlaps with multiple communities

---

## Results

- Identified **distinct behavioral clusters** that map to real-world archetypes
- Discovered **overlapping communities** of users with shared contest preferences
- Combined clustering and network analysis reveals deeper insights than either method alone

---

## Real-World Impact

- **DFS Companies**: Can target promotions to user archetypes
- **Regulators**: Can detect coordinated fraudulent activity (e.g., 2024 Jontay Porter prop-bet case)
- **Industry**: Reinforces behavioral analysis as a key driver for growth, personalization, and compliance

---

## Visualization

- **PCA cluster plots** visualize betting archetypes in reduced dimensions
- **Network graphs** show user similarity and overlapping community membership via BigCLAM

---

## Tools & Technologies

- **Python**: Data processing, clustering (scikit-learn), graph analysis (networkx, BigCLAM)
- **Pandas / NumPy**: Data wrangling
- **Matplotlib / Seaborn**: Visualization
- **Jupyter Notebook**: Exploratory data analysis

---

## Future Work

- Incorporate time-series modeling of betting behavior
- Add demographic data for sociological profiling
- Refine edge construction using more granular similarity metrics

---

## Citation

If using the dataset or methodology, please cite the Transparency Project and the original DFS dataset from Cambridge Health Alliance.

---

## License

This project is for academic and research purposes only. 