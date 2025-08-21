# FMCG Warehouse Optimization (Regression + Classification)

Forecast optimal shipment weight to warehouses and flag overstock risk using Python.  
**Regression:** Ridge Regression (Test R² ≈ 0.9745, RMSE ≈ 1850 tons).  
**Classification:** KNN (K=1) with Test Error ≈ 0.2%, Sensitivity ≈ 0.996, Specificity ≈ 0.999.  

- [View Notebook on GitHub](notebooks/fmcg_warehouse_optimization.ipynb)  
- [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/KalyaniChikshe/fmcg-warehouse-optimization/blob/main/notebooks/fmcg_warehouse_optimization.ipynb)

---

## Problem
A fast-moving consumer goods (FMCG) firm faced stockouts in some regions and excess inventory in others. We model shipment volume and segment warehouses to guide logistics and inventory planning.

---

## Data
Dataset: [Supply Chain Optimization for a FMCG Company](https://www.kaggle.com/datasets/suraj9727/supply-chain-optimization-for-a-fmcg-company)  

Key features include:  
- Retail shop count  
- Refill requests  
- Transport/storage issues  
- Hub distance  
- Zone and warehouse capacity  

---

## Methods
- **EDA & Feature Engineering:** log/sqrt transforms, interaction terms (e.g., shop density × refill)  
- **Regression:** OLS + subset selection (forward/backward/best), Ridge & Lasso comparison → Ridge chosen for robustness  
- **Classification:** Logistic (convergence warnings), LDA, KNN (K=1) → KNN chosen (lowest error, no instability)  

---

## Results
- **Ridge Regression:** Test R² ≈ 0.9745, RMSE ≈ 1850 tons  
- **KNN (K=1):** Test Error ≈ 0.2%, Sensitivity ≈ 0.996, Specificity ≈ 0.999  

**Key shipment drivers (from Ridge):**  
- Storage issues (+) → strongest positive driver  
- Transport issues (–) → reduce allocation  
- Retail density × refill frequency (+) → increases shipment volume  
- Location, zone, and capacity → contextual effects  

---

## Repo Contents
- `notebooks/fmcg_warehouse_optimization.ipynb` — full workflow (EDA → modeling → evaluation)  
- `screenshots/` — selected plots and model visuals  
- `requirements.txt` — minimal dependencies  

---

## How to Run (Locally)
```bash
git clone https://github.com/KalyaniChikshe/fmcg-warehouse-optimization.git
cd fmcg-warehouse-optimization
pip install -r requirements.txt
jupyter notebook notebooks/fmcg_warehouse_optimization.ipynb
