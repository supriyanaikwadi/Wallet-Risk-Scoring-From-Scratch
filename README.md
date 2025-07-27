# Wallet Risk Scoring (Simulated) 

This project computes risk scores for Ethereum wallet addresses based on simulated Compound protocol data.

##  Files

- `wallet_risk_scoring_simulated.ipynb`: Jupyter notebook to run risk scoring using simulated data.
- `wallet_risk_scores.csv`: Output CSV with risk scores (generated after running the notebook).
- `README.md`: This file.
- `analysis.md`: Explanation of logic, features, and scoring method.

##  How to Use

1. Download or clone the repository.
2. Place `Wallets.csv` (with `wallet_id` column) in the root folder.
3. Run the notebook `wallet_risk_scoring_simulated.ipynb` in Jupyter.
4. Output will be saved as `wallet_risk_scores.csv`.

##  Requirements

Install required Python packages using:

bash
pip install pandas tqdm scikit-learn

