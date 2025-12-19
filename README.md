# Predictive Maintenance of Turbofan Engines (NASA C-MAPSS)

**Course:** Machine Learning Project
**Date:** December 2025
**Specialization:** Modeling and Numerical Mechanics

## Group Members
* Gwennael Ribnikar
* Elodie Wang
* Anthony Prezeau

---

## Project Description
This repository contains the source code and the final report for our Machine Learning project. The objective is to develop a predictive maintenance solution for the aeronautics industry using the NASA C-MAPSS dataset.

The main goal is to predict the Remaining Useful Life (RUL) of turbofan engines based on time-series sensor data. Accurate RUL estimation allows for in time maintenance, optimizing operational costs and ensuring flight safety.

## Methodology

We adopted a generalized approach by merging the four sub-datasets (FD001 to FD004) to build a robust model capable of handling multiple fault modes and operating conditions.

### 1. Data Processing
* **Data Cleaning:** Removal of constant features and selection of sensors based on correlation analysis.
* **Feature Engineering:** Implementation of rolling features (mean, standard deviation, and trend) over 10-cycle windows to capture the velocity of degradation.
* **Target Engineering:** RUL clipping at 125 cycles to focus the learning process on the critical end-of-life phase.

### 2. Modeling Strategy
We implemented and compared three different approaches:
* **Baseline:** Random Forest Regressor.
* **Gradient Boosting:** XGBoost optimized with rolling features.
* **Deep Learning:** A hybrid CNN-LSTM architecture. The CNN layers extract local features from sensor noise, while LSTM layers capture long-term temporal dependencies.

### 3. Final Solution
Our final model is a Weighted Ensemble combining the predictions of XGBoost and CNN-LSTM. This approach leverages the stability of decision trees and the pattern recognition capabilities of neural networks.

## Results

Performance was evaluated using the Root Mean Squared Error (RMSE) on the test set.

| Model | RMSE (Cycles) |
|-------|---------------|
| Random Forest (Baseline) | 19.71 |
| Ensemble (XGBoost + CNN-LSTM) | 17.63 |

The residual analysis shows that the model is reliable in the critical zone (RUL < 20 cycles), limiting the risk of overestimating the remaining life of an engine.

## Repository Structure

* **Project_Notebook_Finale.ipynb**: The Jupyter Notebook containing the data pipeline, model training, and evaluation.
* **Project_Report.pdf**: The detailed scientific report explaining our approach and results.
* **README.md**: Project documentation.

## Installation and Usage

To reproduce the results, please follow these steps:

1. **Clone this repository:**
   ```bash
   git clone [https://github.com/WangELu/MachineLearningProject.git](https://github.com/WangELu/MachineLearningProject.git)
   
2.**Install the required libraries:**
   pip install pandas numpy matplotlib seaborn scikit-learn xgboost tensorflow

3. **Prepare the Data:**
   Locate the file resources.zip included in this repository.
   
   Unzip it inside the main folder.

4. **Run the Code:**
   Open the notebook Project_Notebook_Finale.ipynb and run all cells sequentially.

## References

* A. Saxena and K. Goebel, "C-MAPSS Data Set", NASA Ames Prognostics Data Repository (2008).

