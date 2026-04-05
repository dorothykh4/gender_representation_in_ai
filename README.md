# Investigating Gender Representation in AI-Generated Images of Careers

## Overview
This project investigates gender bias in AI-generated images across different professional contexts. AI-generated images of people in various careers and banking institutions are labeled by both humans (via Google Forms) and an AI classifier (Nyckel API), and the resulting labels are analyzed for gender representation bias using statistical methods.

---

## Research Question
Do AI image-generation tools reproduce, amplify, or counterbalance gender disparities observed in real-world employment statistics?

---

## Project Structure
```
├── README.md
├── requirements.txt
├── .gitignore
│
├── Images banks/
│   ├── images/      # AI-generated images of 5 banks
│        ├── ChatGPT_individuals
│        ├── Midjourney_individuals
│        └── Stable_Diffusion_individuals   
│   ├── Human Labeling    # Google Form labeling results
│        ├── google_form_responses.csv
│        ├── human_labeling_confidence.ipynb
│   ├── AI Labeling        # Nyckel API labeling
│        ├── ai_labeling_nyckel.ipynb
│        ├── gender_labels_ChatGPT_individuals.csv
│        ├── gender_labels_Midjourney_individuals.csv
│        ├── gender_labels_Stable_Diffusion_individuals.csv
│   ├── Analysis             
│        ├── bias_amplification.ipynb    # bias-amplification score
│        ├── chi_square.ipynb            # chi-square test
│        ├── descriptive_stats.ipynb     # exploratory data analysis
│        ├── final_labels.csv
│        ├── z_test.ipynb                # z-test
│   └── labeling.ipynb        # cleaning and combining human and ai labeling
│
└── Images professions/
│   ├── images/      # AI-generated images of 10 professions
│        ├── ChatGPT_faces
│        ├── Midjourney_faces
│        └── Stable_Diffusion_faces
│   └── Analysis
│        ├── Human Labeling    # Google Form labeling results
│             ├── google_form_professions.csv
              ├── google_form_responses.csv
│             ├── human_labeling_confidence.ipynb
│        ├── AI Labeling        # Nyckel API labeling
│             ├── ai_final_labeling.ipynb
│             ├── ai_labeling_nyckel.ipynb
│             ├── gender_labels_ChatGPT_faces.csv
│             ├── gender_labels_Midjourney_faces.csv
│             ├── gender_labels_Stable_Diffusion_faces.csv  
│        ├── bias_amplification.ipynb    # bias-amplification score
│        ├── chi_square.ipynb            # chi-square test
│        ├── descriptive_stats.ipynb     # exploratory data analysis
│        ├── final_labels.csv
│        ├── z_test.ipynb                # z-test
│        └── labeling.ipynb              # cleaning and combining human and ai labeling
```

---

## Data
- **AI-generated images** were created using DALL-E, Midjourney, and Stable Diffusion for 10 professions and 5 banking institutions
- **Human labels** were collected via Google Forms, where participants labeled the perceived gender of each image
- **AI labels** were generated using the [Nyckel](https://www.nyckel.com/) image classification API

---

## Methodology
Each folder follows the same pipeline:

1. **Image Labeling** — Images are classified by gender using the Nyckel API (`01_labeling.ipynb`)
2. **Exploratory Data Analysis** — Distribution of gender labels across professions/banks visualized using bar charts, heatmaps, and summary statistics (`02_eda.ipynb`)
3. **Statistical Analysis** (`03_analysis.ipynb`):
   - **Z-test** — Tests whether the proportion of a gender label differs significantly from an expected baseline
   - **Chi-square test** — Tests for association between profession/bank and gender label distribution
   - **Bias Amplification Score** — Measures the degree to which the AI exaggerates real-world gender imbalances

---

## Setup

### 1. Clone the repository
```bash
git clone https://github.com/dorothykh4/gender_representation_in_ai.git
cd gender_representation_in_ai
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up environment variables
Copy example to `.env` and fill in your credentials:

example:
```bash
NYCKEL_CLIENT_ID=your_client_id
NYCKEL_CLIENT_SECRET=your_client_secret
```

### 4. Run the notebooks
Open Jupyter and run notebooks within each folder.

```bash
jupyter notebook
```

---

## Requirements
See `requirements.txt`. Key packages:
- `nyckel` — AI image classification API
- `pandas`, `numpy` — data manipulation
- `scikit-learn`, `scipy`, `statsmodels` — statistical analysis
- `seaborn`, `matplotlib` — visualization
- `python-dotenv` — environment variable management

---

## Author
Daria Khmara — khmara@uni.minerva.edu
