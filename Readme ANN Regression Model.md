ANN Regression Model 

ANN Teen Digital Habits → Mental Health Prediction

A machine learning project that predicts stress level from digital behavior patterns using a PyTorch-based Artificial Neural Network (ANN).

Notebook: ANN_Teen_mental_health_final.ipynb
Dataset: Kaggle – Digital Habits vs Mental Health
https://www.kaggle.com/datasets/abhishekdave9/digital-habits-vs-mental-health-dataset
=========================================================================================================================================
Overview

This project models the relationship between teen digital habits (e.g., screen time, sleep hours) and mental health outcomes, specifically stress level (regression target).

The system uses a supervised learning approach with:

	structured tabular features
	normalized inputs
	deep neural network regression model

The goal is to predict a continuous stress score and evaluate prediction accuracy using regression metrics.
=========================================================================================================================================

Problem Type
Task		Output		Activation		Loss Function	Metrics
Regression	1 neuron	None (linear output)	MSELoss		RMSE, MAE, R²

=========================================================================================================================================


Key Features

Tabular feature learning
	All dataset features except target used as inputs
Data normalization
	Standardization using training mean and std only
Deep learning regression model
	Fully connected ANN (64 → 64 → 1)
	ReLU activations
	Dropout-free final regression output
Stable optimization
	Adam optimizer with weight decay
	Gradient clipping (prevents instability from outliers)
Full evaluation pipeline
	R² score
	RMSE, MAE, MSE
	residual analysis
=========================================================================================================================================
Dataset
	Source: Kaggle – Digital Habits vs Mental Health
	Target variable: stress_level

Input features include:

	social_media_platforms_used
	hours_on_TikTok
	sleep_hours

=========================================================================================================================================

Model Architecture
Layer		Size		Activation
Input		N features	-
Hidden 1	64		ReLU
Hidden 2	64		ReLU
Output		1		Linear

=========================================================================================================================================

Data Pipeline
1. Train / Validation / Test Split
	70% training
	15% validation
	15% testing
2. Normalization (No Data Leakage)
	Mean and standard deviation computed only from training data
	Applied consistently to validation and test sets
3. PyTorch Dataset Wrapper
	Converts NumPy arrays → tensors
	Enables batch training with DataLoader

=========================================================================================================================================

Training Setup
	Loss function: MSELoss
	Optimizer: Adam
	Learning rate: 1e-3
	Weight decay: 1e-4
	Gradient clipping: max_norm = 1.0
	Epochs: 100

Evaluation Metrics
Validation / Test Metrics
	R² Score → how well model explains variance
	MSE → average squared error
	RMSE → interpretable error scale
	MAE → average absolute error

Results
Test Performance
	R² Score: ~0.73
	RMSE: ~1.05
	MAE: ~0.85
	Residual mean: ~0.08
	Residual std: ~1.05

Interpretation
	Model explains ~73% of variance in stress levels
	Predictions are reasonably close with low average error
	Residual distribution indicates minimal systematic bias

Example Predictions
Real Stress	Predicted	Error
9.00		8.67		0.33
6.00		5.62		0.38
10.00		9.36		0.64
2.00		3.60		1.60

=========================================================================================================================================

Key Design Decisions
1. Regression formulation
	No activation in output layer
	Direct continuous value prediction
2. Robust training
	Gradient clipping applied to prevent instability from outliers
3. Proper evaluation
	Multiple metrics used (R², RMSE, MAE)
	Residual analysis included for error distribution
4. Strict anti-leakage design
	Normalization computed only on training data

Limitations
	Dataset is observational and not clinical-grade
	Stress prediction is approximate, not diagnostic
	Performance depends on feature quality and dataset noise

Future Improvements
	Feature selection / correlation pruning
	More advanced architectures 
	Hyperparameter optimization 
	
=========================================================================================================================================

How to Run
In Google Colab

Open:
	ANN_Teen_mental_health_final.ipynb
Upload dataset:
	digital_habits_vs_mental_health.csv
Run all cells sequentially
=========================================================================================================================================

Summary

This project demonstrates a full regression-based deep learning pipeline, including:

	data preprocessing
	normalization without leakage
	neural network training
	evaluation with statistical metrics

It is designed to model how digital behavior correlates with mental health indicators using modern machine learning techniques.