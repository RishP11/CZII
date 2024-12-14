# CZII - CryoET Object Identification

---

### _Find small biological structures in large 3D Volumes_

#### Overview
This repository hosts code and documentation for the Kaggle competition **CryoET Object Identification**. The goal of this challenge is to develop machine learning algorithms that automatically annotate five classes of protein complexes within curated real-world cryo-electron tomography (cryoET) datasets.

---

### Competition Details

#### Link to the Competition
[Visit the Kaggle Competition Page](https://www.kaggle.com/competitions/czii-cryo-et-object-identification/overview)

#### Description
Protein complexes, such as oxygen-carrying hemoglobin or keratin in hair, play crucial roles in cellular function. Understanding these interactions is key to advancing human health and developing new treatments for diseases. Cryo-electron tomography (cryoET) enables the creation of 3D images (tomograms) at near-atomic resolution, capturing proteins in their intricate natural environments. However, automated identification of proteins within tomograms remains an unsolved challenge.

This competition seeks to unlock the mysteries of the cell by leveraging machine learning to identify proteins in cryoET tomograms. Success in this task could reveal the “dark matter” of the cell, paving the way for thousands of biological discoveries.

Participants are tasked with detecting five classes of protein complexes in a dataset curated from real-world tomograms. The competition prioritizes recall over precision, especially for harder-to-detect proteins, by employing a custom evaluation metric.

---

### Evaluation

Submissions are evaluated using the **F-beta metric** with a beta value of 4, which prioritizes recall over precision. Key aspects include:

- **Recall Dominance**: The higher beta value (4) emphasizes the importance of recall, heavily penalizing missed detections while being more lenient with false positives.
- **True Positive Definition**: A detected particle is considered a true positive if it lies within 0.5 of the particle’s radius.
- **Weighted Scoring**: The five target particle types are scored with different weights:
  - Easy particles (ribosome, virus-like particles, apo-ferritin): Weight = 1
  - Hard particles (thyroglobulin, β-galactosidase): Weight = 2
- **Micro-Averaging**: Precision and recall are computed across the entire dataset before applying the F-beta formula.
- **Unscored Particles**: Beta-amylase particles are included in the training data but have a weight of 0 and do not affect scoring.

---

### Submission Format

Your submission must contain a header and adhere to the following format:

```csv
id,experiment,particle_type,x,y,z
0,TS_5_4,beta-amylase,2983.596,3154.13,764.124
1,TS_5_4,beta-amylase,2983.596,3154.13,764.124
2,TS_5_4,beta-galactosidase,2983.596,3154.13,764.124
```

#### Columns:
- **id**: A unique integer for each prediction.
- **experiment**: The tomogram ID.
- **particle_type**: Predicted protein class.
- **x, y, z**: Predicted 3D coordinates of the particle.

---

### Repository Structure

```plaintext
.
├── data/                   # Scripts and utilities for data preprocessing
├── models/                 # Machine learning model implementations
├── notebooks/              # Jupyter notebooks for EDA and experimentation
├── scripts/                # Helper scripts for training and evaluation
├── submissions/            # Generated submission files
├── README.md               # This README file
└── requirements.txt        # Python dependencies
```

---

### Getting Started

#### Prerequisites
- Python 3.8 or later
- Kaggle CLI for downloading competition data
- GPU-enabled machine for training models

#### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your_username/czii-cryoet-object-identification.git
   cd czii-cryoet-object-identification
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Download the competition data using the Kaggle CLI:
   ```bash
   kaggle competitions download -c czii-cryo-et-object-identification
   ```

---

### License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

### Acknowledgments

We thank Kaggle and the organizers of the CryoET Object Identification competition for providing this unique opportunity to contribute to advancements in protein structure analysis.

