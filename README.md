# Mlops-dvc-wandb
This repository contains a fully reproducible machine learning pipeline project based on the Titanic dataset. It uses DVC for data and pipeline versioning and Weights &amp; Biases (wandb) for experiment tracking. The project is organized for clarity and modularity to facilitate easy extension and collaboration.


# Titanic ML Pipeline Project

## Project Overview

This project implements a reproducible machine learning pipeline to predict survival on the Titanic dataset. It leverages DVC (Data Version Control) to handle data and model versioning, and Weights & Biases (wandb) for tracking experiments.

The pipeline consists of sequential stages including data loading, preprocessing, and model training, with all steps automated and dependencies tracked to ensure reproducibility.



## Repository Structure

| Folder / File       | Description                                                |
|---------------------|------------------------------------------------------------|
| `src/`              | Contains source code scripts for data loading, preprocessing, and training |
| `dvc.yaml`          | DVC pipeline configuration describing stage commands, dependencies, and outputs |
| `params.yaml`       | Configuration parameters for model training and preprocessing |
| `requirements.txt`  | Python dependencies required to run this project           |
| `README.md`         | This documentation file                                     |
| `.gitignore`        | Specifies files and folders ignored by Git                 |



## Pipeline Stages (via `dvc.yaml`)

| Stage        | Script            | Inputs                            | Outputs                       | Description                                 |
|--------------|-------------------|---------------------------------|-------------------------------|---------------------------------------------|
| **loaddata** | `srcloaddata.py`  | None                            | `dataraw.csv`                 | Loads raw Titanic data                       |
| **preprocess**| `srcpreprocess.py`| `dataraw.csv`                   | `dataXtrain.csv`, `dataXtest.csv`, `dataytrain.csv`, `dataytest.csv` | Cleans and splits dataset                   |
| **train**    | `srctrain.py`     | Preprocessed train/test data, `params.yaml` | `model.pkl`                  | Trains model and saves trained model        |



## Installation

1. Clone the repository:
    ```
    git clone <repository-url>
    cd <repository-folder>
    ```

2. Create a Python virtual environment (optional but recommended):
    ```
    python -m venv venv
    source venv/bin/activate   # On Windows: venv\Scripts\activate
    ```

3. Install dependencies:
    ```
    pip install -r requirements.txt
    ```

4. Log in to Weights & Biases to enable experiment tracking:
    ```
    wandb login
    ```


## Usage

- Initialize DVC in the project directory:
    ```
    dvc init
    ```

- Run the pipeline stages automatically with DVC:
    ```
    dvc repro
    ```

- The trained model will be saved as `model.pkl` in the root directory.

- Modify `params.yaml` to change training parameters such as test size, random seed, or max iterations.


## Configuration (`params.yaml`)

| Parameter     | Value | Description                          |
|---------------|-------|------------------------------------|
| `testsize`    | 0.2   | Fraction of the dataset for testing |
| `randomstate` | 42    | Random seed for reproducibility    |
| `maxiter`     | 200   | Max training iterations             |


## Acknowledgments

- This project uses open-source tools DVC and Weights & Biases for experiment tracking.
- Thanks to the original Titanic dataset providers and scikit-learn contributors.



