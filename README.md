### Machine Learning-Based Prediction of COX-2 Inhibitors Using ChEMBL Data
#### 1️⃣ Project Overview

This project developed a quantitative structure–activity relationship (QSAR) model to predict inhibitory activity against Cyclooxygenase-2 (COX-2), a validated anti-inflammatory drug target.

The workflow included:

Data extraction from ChEMBL

Data curation and preprocessing

Molecular descriptor calculation

Fingerprint generation

Machine learning regression modeling

Algorithm comparison and evaluation

####2️⃣ Biological Background

Target: Cyclooxygenase-2
Gene: PTGS2

COX-2 is an inducible enzyme involved in prostaglandin biosynthesis and inflammation.
Selective inhibition of COX-2 reduces inflammation while minimizing gastrointestinal side effects associated with COX-1 inhibition.

Well-known COX-2 inhibitors include:

Celecoxib

Etoricoxib

COX-2 is therefore a classical and clinically validated drug discovery target.

#### 3️⃣ Dataset

Source: ChEMBL

Target: CHEMBL230 (Human COX-2)

Bioactivity type: IC50

Units: nM

Compounds after cleaning: 5377 molecules

Activity transformed to: pIC50

Data curation steps:

Removed missing SMILES

Filtered IC50 values with “=” relation

Kept values in nM

Converted IC50 → molar → pIC50

Removed duplicates

Final dataset size: 5377 compounds

#### 4️⃣ Feature Engineering
Molecular Representation

Morgan fingerprints (ECFP-like)

Radius = 2

2048 bits

Physicochemical descriptors:

Molecular weight

LogP

H-bond donors

H-bond acceptors

TPSA

Best performance was achieved using fingerprints alone.

#### 5️⃣ Modeling Approach

Regression task: Predict pIC50

Train/test split: 80/20
Cross-validation: 5-fold

Models evaluated:

Random Forest

Support Vector Regression

K-Nearest Neighbors

Gradient Boosting

Linear Regression

#### Results
Best Model: Random Forest (Fingerprints)

R² ≈ 0.57

RMSE ≈ 0.89 pIC50 units

Cross-validation R² ≈ 0.56

Interpretation:

The model explains ~57% of activity variance using 2D structural information only.
This is consistent with literature-level QSAR performance for enzyme inhibition modeling.

#### 7️⃣ Scientific Insights

Structural fingerprints dominate prediction performance.

Adding simple global descriptors did not improve performance.

Linear regression failed (negative R²), confirming nonlinear SAR.

Tree-based models are best suited for sparse molecular fingerprints.

Model shows acceptable generalization (CV aligned with test performance).

#### 8️⃣ Limitations

Random train/test split may inflate performance due to scaffold overlap.

Only 2D descriptors used (no 3D information).

No external validation set.

No scaffold-based splitting applied.

#### 9️⃣ Potential Improvements

Scaffold split validation

SHAP analysis for interpretability

Activity classification modeling

3D descriptor integration

Deep learning models (Graph Neural Networks)

External validation with new compounds

#### 🔟 Skills Demonstrated

This project demonstrates:

Bioinformatics data retrieval (ChEMBL API)

Cheminformatics using RDKit

QSAR modeling

Feature engineering

Model evaluation and comparison

Cross-validation methodology

Scientific interpretation of ML results
