# CS599_Final_Project
## 👥 Team Members & Roles

| Member | Role                                | Responsibilities                                                                 |
|--------|-------------------------------------|----------------------------------------------------------------------------------|
| A      | Feature Engineering & Preprocessing | Clean the data, reduce features (≤50), remove multicollinearity, normalize features |
| B      | Clustering & Characterization       | Perform unsupervised clustering, assign cluster IDs, analyze subgroup characteristics |
| C      | Subgroup Modeling (Stacking 1)      | Build stacking model for assigned cluster with ≥3 non-parametric base models and meta model |
| D      | Subgroup Modeling (Stacking 2) + Test Integration | Build stacking model for another cluster; integrate all models for test prediction and generate `submission.csv` |

## 📦 Required Files for Submission

| File Name                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| `GroupXX_TrainingData.ipynb`     | Shared notebook containing Sections 3.1 and 3.2: feature preparation and clustering |
| `A_Subgroup0.ipynb`              | Member A’s stacking model for Subgroup 0                                    |
| `B_Subgroup1.ipynb`              | Member B’s stacking model for Subgroup 1                                    |
| `C_Subgroup2.ipynb`              | Member C’s stacking model for Subgroup 2                                    |
| `D_Subgroup3.ipynb`              | Member D’s stacking model for Subgroup 3                                    |
| `GroupXX_Generalization.ipynb`   | Final unified script for test set prediction (Section 4)                    |
| `submission.csv`                 | Final prediction results for the 1012 test companies                        |
| `GroupXX_CS559_Results.docx`     | Team report: subgroup stats, characteristics, accuracy table (Table 3), confusion matrices, and video link |
| `video.mp4` or video link        | Group video presentation (embed or provide a shareable link)                |
