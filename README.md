# Autonomous Aircraft Tactical Pop-Up Attack Using Imitation and Generative Learning

This repository contains the implementation of models developed for predicting aircraft control inputs during pop-up attack maneuvers in air combat scenarios. The methodology combines imitation learning techniques and generative learning to train and evaluate models using flight data from a high-fidelity flight simulator and synthetic data generated with a Variational Autoencoder (VAE).

## Project Overview

This study explores the development of models using two configurations:
- **Baseline:** Excludes derived variables, such as linear velocities, angular velocities, and accelerations, to analyze performance without temporal dependencies.
- **Full:** Includes all available state variables, emphasizing the importance of derived variables in capturing the temporal dynamics of the maneuver.

## Project Structure

### Main Files
- `eda.ipynb`: Notebook for Exploratory Data Analysis (EDA), providing insights into the flight data's characteristics.
- `vae.ipynb`: Notebook for training the Variational Autoencoder (VAE) and generating synthetic flight data.
- `mlp-baseline.ipynb`, `lstm-baseline.ipynb`, `gru-baseline.ipynb`: Notebooks for training baseline versions of the models (MLP, LSTM, GRU) without derived variables.
- `mlp-full.ipynb`, `lstm-full.ipynb`, `gru-full.ipynb`: Notebooks for training full versions of the models (MLP, LSTM, GRU) with all state variables.
- `mlp-baseline-augmented.ipynb`, `lstm-baseline-augmented.ipynb`, `gru-baseline-augmented.ipynb`: Notebooks for training baseline models with augmented datasets using synthetic data.
- `mlp-full-augmented.ipynb`, `lstm-full-augmented.ipynb`, `gru-full-augmented.ipynb`: Notebooks for training full models with augmented datasets using synthetic data.

### Output Directories
- `metrics/`: Contains CSV files with evaluation results, such as RMSE, R², training time, and inference time.
- `models/`: Contains trained models saved in `.keras` format.
- `plots/`: Stores visualizations, including training and validation loss curves and trajectory comparisons.

## How to Run the Project

1. **Exploratory Data Analysis (EDA):**
   - Open `eda.ipynb` and run all cells to explore and visualize the flight data.
   - This step provides insights into the characteristics of the original flight data and prepares it for further processing.

2. **Train Baseline and Full Models:**
   - Choose a model type (MLP, LSTM, GRU) and a configuration (baseline or full).
   - Open the corresponding notebook (e.g., `mlp-baseline.ipynb` for baseline MLP or `lstm-full.ipynb` for full LSTM).
   - Run all cells to preprocess the data, train the model, and evaluate its performance for both baseline and full configurations.

3. **Generate Synthetic Data:**
   - Open `vae.ipynb`.
   - Train the VAE model on the adjusted flight data and generate synthetic flight data.
   - Save the generated data in the appropriate `generated_flights_[X]/` directory, based on the number of synthetic flights generated.
   - The synthetic data is automatically smoothed using a centered moving average with a window size of 10 frames.
   - The smoothed data is saved in the corresponding `smoothed_flights_[X]/` directories.

4. **Train Models with Augmented Data:**
   - Open the augmented training notebooks (e.g., `mlp-baseline-augmented.ipynb`, `lstm-full-augmented.ipynb`).
   - Train the models using the combined dataset (original + smoothed synthetic data).
   - Evaluate the models and compare performance with the baseline and full configurations.

5. **Evaluate Results:**
   - Check the `metrics/` directory for CSV files containing evaluation results such as RMSE, R², training time, and inference time.
   - Open the `plots/` directory for visual comparisons, including training and validation loss curves and predicted versus actual trajectories.


## Requirements

The project requires the following Python libraries:

- `tensorflow`
- `numpy`
- `pandas`
- `scikit-learn`
- `matplotlib`

You can install these dependencies using pip:

```bash
pip install tensorflow numpy pandas scikit-learn matplotlib
