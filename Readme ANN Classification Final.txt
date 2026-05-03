Readme Phishing Email ANN

Phishing Email Detection with Neural Networks

A production-oriented machine learning pipeline that classifies emails as phishing or safe using a combination of TF-IDF text features, engineered signals, and a PyTorch-based Artificial Neural Network (ANN).
========================================================================================================================================
Overview

Phishing remains one of the most common entry points for cyberattacks. This project builds a robust classification system that detects phishing emails by combining:

	-Natural language patterns (via TF-IDF)
	-Behavioral indicators (e.g., links, urgency keywords)
	-A deep learning classifier optimized for binary classification

The pipeline follows machine learning best practices, including proper data splitting, no data leakage, and strong evaluation metrics.
========================================================================================================================================

Key Features:

Hybrid Feature Engineering
	-TF-IDF vectorization (unigrams → trigrams)
	-Manual features (links, urgency terms, message length)
Neural Network Classifier
	-Fully connected ANN (256 → 128 → 1)
	-ReLU activations with dropout regularization
Stable Training Setup
	-BCEWithLogitsLoss for numerical stability
	-Mini-batch training with PyTorch
Evaluation Metrics
	-ROC-AUC (primary metric)
	-Accuracy
	-F1 Score
Robust Data Pipeline
	-Handles malformed CSV rows during loading
	-Cleans HTML, whitespace, and noisy samples
========================================================================================================================================

Dataset

This project uses a publicly available dataset from Kaggle:

🔗 https://www.kaggle.com/datasets/subhajournal/phishingemails

	File: Phishing_Email.csv

You will need to download the csv file and then upload in colab before running the program 

Preprocessing includes:
	-Lowercasing text
	-Removing HTML tags
	-Filtering short or low-quality emails
	-Extracting structured features
========================================================================================================================================

Model Architecture

Component	Description
Input Layer	TF-IDF + engineered features
Hidden Layer 1	256 units + ReLU + Dropout
Hidden Layer 2	128 units + ReLU + Dropout
Output Layer	1 neuron (logit output)

Output Design (Binary Classification)
Output		Activation				Loss
1 neuron	Sigmoid (applied during evaluation)	BCEWithLogitsLoss

========================================================================================================================================

Project Structure
├── data/
│   └── Phishing_Email.csv
├── models/
│   └── model.pt
├── train.py
├── README.md
========================================================================================================================================

Installation

This project runs in Google Colab.

No installation is required.  
Just open the notebook and run the cells.


========================================================================================================================================

Usage:

1. Open the notebook:
   ANN_Classification_Final.ipynb

2. Upload the dataset:
   `Phishing_Email.csv`

3. Run all cells from top to bottom

What the notebook does

- Cleans and preprocesses email text
- Extracts TF-IDF and engineered features
- Splits data into train / validation / test sets
- Trains an ANN model for classification
- Outputs evaluation metrics:
  - Accuracy
  - F1 Score
  - ROC-AUC

Example Output
Epoch 10
Train Loss: 0.2451
Val Loss  : 0.1987
Accuracy  : 0.91
ROC-AUC   : 0.95
F1 Score  : 0.89

========================================================================================================================================

Key Design Decisions

1. No Data Leakage
	TF-IDF and scaling are fit only on training data
2. BCEWithLogitsLoss
	Combines sigmoid + binary cross entropy
	More stable than applying sigmoid manually
3. Sparse + Dense Feature Fusion
	Combines semantic (text) and behavioral (manual) signals

Results:

Metric		Performance
Accuracy	~0.99
F1 Score	~0.99
ROC-AUC		~0.98

(Results may vary depending on preprocessing and random initialization)
========================================================================================================================================

Future Improvements
	add class imbalance handling (weighted loss)
	Optimize decision threshold beyond 0.5
	Deploy as an API for real-time phishing detection
========================================================================================================================================

License

MIT License
========================================================================================================================================
Summary

This project demonstrates a complete machine learning pipeline:

	Data cleaning and preprocessing
	Feature engineering
	Model training
	Evaluation using meaningful metrics

It is structured for reproducibility and reflects practical approaches used in real-world cybersecurity systems.