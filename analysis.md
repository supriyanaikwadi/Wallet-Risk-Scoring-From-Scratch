# Analysis Report: Wallet Risk Scoring

##  Objective

To assign a risk score (0–1000) to each wallet address based on its on-chain activity and behavior in the Compound protocol.

##  Data Collection

In this simulation:
- Wallet addresses are loaded from `Wallets.csv`
- Simulated function `fetch_wallet_data()` provides mock data

In real deployment, this function should pull live data from:
- Compound V2 subgraph (The Graph)
- Alchemy or Covalent API

##  Features Used

1. borrow_to_supply_ratio: Higher value implies more leverage (risky)
2. repaid_to_borrow_ratio: Indicates user's repayment responsibility (higher = safer)
3. liquidations: Number of times wallet got liquidated (more = risky)
4. health_factor: Compound's native metric for liquidation threshold (higher = safer)

##  Scoring Method

- All features are normalized using `MinMaxScaler`
- Weighted sum is applied using the following weights:

| Feature                 | Weight |
|-------------------------|--------|
| borrow_to_supply_ratio  | 0.3    |
| repaid_to_borrow_ratio  | 0.3    |
| liquidations (inverse)  | 0.2    |
| health_factor           | 0.2    |

- Score is scaled to 0–1000

##  Output

Final output is a CSV file `wallet_risk_scores.csv` with:

| wallet_id | score |
|-----------|-------|
| 0xABC...   | 732   |
| 0xDEF...   | 485   |

##  Notes

- In production, plug in live APIs for accurate risk scoring.
- Feature weights can be tuned using model optimization techniques.