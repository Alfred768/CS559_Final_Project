# 📊 CS559 Final Project - Team Workflow Overview (4 Members)

This project aims to improve bankruptcy prediction by dividing the dataset into subgroups and training specialized models for each. The workflow follows the official project specification and recent instructor clarifications to ensure compliance and clarity.

---

## 🗂️ Project Workflow

### Step 1: Data Cleaning and Preparation

- Load the training data.
- Handle missing values and remove duplicate rows.
- Drop irrelevant columns (e.g., "Index").
- Output basic data statistics (shape, missing counts, etc.).

---

### Step 2: Initial Feature Selection and Preprocessing

- Use `ExtraTreesClassifier` to identify important features.
- Select features with importance > 0.017.
- Apply standardization (e.g., `StandardScaler`) if necessary before clustering.

---

### Step 3: KMeans Clustering

- Apply `KMeans(n_clusters=5, random_state=42)` to the preprocessed data.
- Assign each sample a cluster label.
- Print the number of samples and number of bankrupt cases in each cluster.
- Save `cluster_labels.csv` containing:
---

### Step 4: Cluster Label Classifier (Supervised Model)

> 🔍 Objective: Build a classifier to predict cluster labels using the **original (unprocessed) training data**, and analyze which features are most important.

- Use the original training data (not the transformed data used in clustering).
- Train a supervised classifier (e.g., `RandomForestClassifier`) with cluster labels as the target.
- Extract and visualize `feature_importances_`.
- Document the top features and their role in distinguishing cluster memberships.

---

### Step 5: Subgroup Data Generation

- Merge `cluster_labels.csv` back with the original training data using `Index`.
- Split the data into separate CSV files, one for each cluster (e.g., `subgroup_0.csv`, `subgroup_1.csv`, ...).
- Print statistics for each subgroup (total samples, # of bankrupt companies).
- Mark any subgroup with **no bankrupt samples** for constant prediction (`ĥ = 0`).

---

### Step 6: Subgroup Modeling (One per Team Member)

Each team member is assigned one subgroup (excluding clusters with no bankrupt cases).

For each subgroup:
- Start from the original data (not preprocessed).
- Apply your own preprocessing (feature selection, scaling).
- Train base models + a stacking ensemble.
- Evaluate and record:
- Accuracy
- True Positive / True Negative counts
- Number of features used
- Confusion matrix

All subgroup results are aggregated into **Table 3** in the final report.

---

### Step 7: Generalization Notebook

- Load `test_data.csv`.
- Load the trained cluster classifier model (e.g., using `joblib.load()`).
- Predict the cluster label for each test sample.
- Send the samples to the corresponding subgroup model.
- Each subgroup model makes predictions (or `ĥ = 0` if constant).
- Merge predictions into final output: `GroupXX_Generalization.csv`.

---

### Step 8: Final Reporting

- Fill out Table 3 (one row per subgroup).
- Summarize subgroup assignments and model performance.
- Include charts or visualizations if needed.
- Optionally record a short team presentation or demo video.

---

## 📦 Required Files for Submission

| File Name                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| `GroupXX_TrainingData.ipynb`     | Shared notebook containing Sections 3.1 and 3.2: feature preparation and clustering |
| `A_Subgroup1.ipynb`              | Member A’s stacking model for Subgroup 1                                    |
| `B_Subgroup2.ipynb`              | Member B’s stacking model for Subgroup 2                                    |
| `C_Subgroup3.ipynb`              | Member C’s stacking model for Subgroup 3                                    |
| `D_Subgroup4.ipynb`              | Member D’s stacking model for Subgroup 4                                    |
| `GroupXX_Generalization.ipynb`   | Final unified script for test set prediction (Section 4)                    |
| `submission.csv`                 | Final prediction results for the 1012 test companies                        |
| `GroupXX_CS559_Results.docx`     | Team report: subgroup stats, characteristics, accuracy table (Table 3), confusion matrices, and video link |
| `video.mp4` or video link        | Group video presentation (embed or provide a shareable link)                |

---

## 💡 Additional Tips

- Use `joblib.dump()` and `joblib.load()` to save and load trained models and transformers.
- Fix `random_state` for all models and processes to ensure reproducibility.
- Keep subgroup pipelines independent — each member starts from raw data and defines their own process.
- For subgroups with no bankrupt samples, generate a constant prediction file (all labels = 0).
