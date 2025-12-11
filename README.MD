# CinemaSuccessSage 

**Predicting Movie Success Using Machine Learning**

This repository contains the code and resources for the project **"Predicting Movie Success Using Machine Learning"** (CS 5805). The project leverages metadata from over 6,000 movies to predict commercial success (revenue) and audience reception (user ratings) using machine learning models including Linear Regression, Random Forest, XGBoost, and Neural Networks.

## Project Structure

```bash
CinemaSuccessSage/
├── data/
│   ├── raw/                  # Place downloaded datasets here (see instructions below)
│   └── processed/            # Generated parquet files after running notebooks
├── models/                   # Saved model artifacts (.pkl, .pth)
├── notebooks/                # Jupyter notebooks for analysis and modeling
│   ├── eda.ipynb
│   ├── pre_processing.ipynb
│   ├── baseline_models.ipynb
│   ├── advanced_models.ipynb
│   ├── neural_network.ipynb
│   └── evaluation_cv.ipynb
├── reports/                  # Generated figures and tables
├── requirements.txt          # Python dependencies
└── README.md
```

## Installation

1. **Clone the repository:**
   ```bash
    git clone https://github.com/gavin-barro/CinemaSuccessSage.git
    cd CinemaSuccessSage

   ```

2. **Install dependencies:** 
Ensure you have Python 3.13 installed. Install the required packages using pip:
    ```bash
    pip install -r requirements.txt
    ```

## Installation

Due to file size limits, the raw datasets are not included in this repository. You must download them from Kaggle and place them in the data/raw/ directory exactly as described below.

1. **The Movies Dataset**
    - Source: Kaggle: The Movies Dataset (rounakbanik)
    - Action: Download and unzip.
    - Placement: Create a folder named TheMovieDataset inside data/raw/ and place the CSV files there.
        - Path: data/raw/TheMovieDataset/movies_metadata.csv, credits.csv, etc.

2. **TMDB Movie Dataset (2024)**
    - Source: Kaggle: TMDB Movies Dataset 2024 (asaniczka)
    - Action: Download the CSV file.
    - Placement: Place the file TMDB_movie_dataset_v11.csv directly in the data/raw/ root
        - Path: data/raw/TMDB_movie_dataset_v11.csv

3. **MovieLens 20M Dataset**
    - Source: Kaggle: MovieLens 20M Dataset (grouplens)
    - Action: Download and unzip.
    - Placement: Create a folder named MovieLens inside data/raw/ and place the CSV files there.
        - Path: data/raw/MovieLens/rating.csv, movie.csv, etc.

    ```bash
    data/raw/
    ├── TheMovieDataset/       # Contains movies_metadata.csv, etc.
    ├── MovieLens/             # Contains rating.csv, etc.
    └── TMDB_movie_dataset_v11.csv
    ```

## Getting Started (Reproducibility)
To reproduce the results reported in the paper, execute the notebooks in the following order. All random seeds are set to 42 for consistency.

1. **Data Exploration & Initial Cleaning**
    - Run notebooks/eda.ipynb
    - Output: Cleaning raw data and initial visualizations.

2.  **Preprocessing & Feature Engineering**
    - Run notebooks/pre_processing.ipynb
    - Output: Merges datasets, handles missing values, and saves processed parquet files to data/processed/.

3. **Baseline Models**
    - Run notebooks/baseline_models.ipynb
    - Models: Linear Regression (Ridge) and Random Forest.

4. **Advanced Models**
    - Run notebooks/advanced_models.ipynb
    - Models: XGBoost (Gradient Boosting) with hyperparameter tuning.

5. **Neural Network**
    - Run notebooks/neural_network.ipynb
    - Models: PyTorch Feed-Forward Neural Network.

6. **Final Evaluation**
    - Run notebooks/evaluation_cv.ipynb
    - Output: 5-Fold Cross-Validation metrics (RMSE, R²) for all models.

## Results Summary

| Model          | Revenue R²| Revenue RMSE |   Ratings R²| Ratings RMSE|
|----------------|---------- |--------------|-------------|-------------|
| **XGBoost**        | **0.66 ± 0.01**|	 **1.18 ± 0.01**	|  **0.61 ± 0.01** |  **0.31 ± 0.01** |
| Random Forest  |0.63 ± 0.02|	1.23 ± 0.02	| 0.56 ± 0.01 |	0.31 ± 0.01 |
| Neural Network |0.58 ± 0.02|	1.28 ± 0.02	| 0.57 ± 0.02 |	0.31 ± 0.01 |
| Linear (Ridge) |0.44 ± 0.01|	1.35 ± 0.03	| 0.40 ± 0.01 |	0.42 ± 0.01 |

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Author
    - Gavin Barro
    - Virginia Polytechnic Institute and State University
    - CS 5805: Machine Learning (December 2025)