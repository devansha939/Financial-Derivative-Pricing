# Option Pricing Analysis for American Airlines (AAL)

A comprehensive project analyzing option pricing for American Airlines (AAL) using historical and advanced volatility models. This repository contains the project report and the Jupyter notebook with all code, data analysis, and results.

---

## **Project Overview**

This project investigates the pricing of European call and put options for American Airlines (AAL) stock. It covers the entire workflow from data collection, statistical analysis, volatility modeling (including GARCH), to option pricing using Black-Scholes, Cox-Ross-Rubinstein (CRR) binomial, and Monte Carlo simulation methods. The study compares the impact of historical and GARCH-based volatility estimates on option prices.

---

## **Contents**

- `FDP_Report.pdf` - Detailed project report with methodology, analysis, and results.
- `FDP_assignment.ipynb` - Jupyter notebook containing all code for data processing, statistical tests, volatility modeling, and option pricing.

---

## **Key Steps and Methodology**

### **1. Data Collection**
- Historical daily price data for AAL downloaded from Yahoo Finance (Sep 2005 – May 2025)[1][2].
- Data includes Open, High, Low, Close, and Volume.

### **2. Data Analysis**
- Visualization of price history and log returns.
- Log returns computed as $$ r_t = \ln\left(\frac{P_t}{P_{t-1}}\right) $$.

### **3. Normality Testing**
- Visual checks: QQ plot, histogram with normal curve overlay.
- Statistical tests: Jarque-Bera, Kolmogorov-Smirnov, Anderson-Darling.
- Conclusion: Log returns are not normally distributed (heavy tails, significant deviations from normality)[1].

### **4. Volatility Estimation**
- Historical volatility estimated from log returns and annualized ($$64.49\%$$)[1].
- Advanced volatility modeling using GARCH(1,1) to capture volatility clustering and persistence.
- GARCH forecast volatility: $$76.73\%$$[1].

### **5. Risk-Free Rate**
- 3-month U.S. Treasury Bill rate ($$4.20\%$$) used as the risk-free rate, retrieved from FRED[1].

### **6. Independence Testing**
- Autocorrelation (ACF, PACF) and Ljung-Box test applied to log returns.
- Evidence of serial correlation in returns, suggesting deviation from the random walk hypothesis[1].

### **7. Option Pricing Models**
- **Black-Scholes**: Standard closed-form pricing for European options.
- **CRR Binomial**: Discrete-time lattice model.
- **Monte Carlo Simulation**: Simulates multiple price paths for option payoff estimation.

### **8. Results**
- Option prices computed with both historical and GARCH volatilities.
- GARCH-based prices are significantly higher, reflecting increased forecast volatility.
- All three pricing methods yield consistent results within each volatility scenario[1].

---

## **Results Summary**

| Method           | Volatility Source | Call Price | Put Price  |
|------------------|------------------|------------|------------|
| Black-Scholes    | Historical       | $0.764     | $0.730     |
| CRR Binomial     | Historical       | $0.764     | $0.730     |
| Monte Carlo      | Historical       | $0.766     | $0.730     |
| Black-Scholes    | GARCH            | $0.905     | $0.872     |
| CRR Binomial     | GARCH            | $0.905     | $0.871     |
| Monte Carlo      | GARCH            | $0.908     | $0.871     |

---

## **Conclusions**

- GARCH modeling reveals higher expected future volatility for AAL compared to historical estimates.
- Option prices are sensitive to volatility inputs; GARCH-based prices are ~18–19% higher.
- Statistical tests show AAL returns are non-normal and autocorrelated, justifying the use of advanced volatility models.
- All pricing methods are consistent; choice of volatility model has the greatest impact on results[1].

---

## **How to Use**

1. **Clone the repository** and open `FDP_assignment.ipynb` in Jupyter or Google Colab.
2. **Run all cells** to reproduce the analysis, from data download to final option pricing.
3. **Consult `FDP_Report.pdf`** for detailed explanations, figures, and interpretation of results.

---

## **Dependencies**

- Python 3.x
- numpy
- pandas
- matplotlib
- scipy
- statsmodels
- yfinance
- arch

Install all dependencies via pip:

```bash
pip install numpy pandas matplotlib scipy statsmodels yfinance arch
```

---

## **Author**

Devansh Garg  
2021EEB1164  
Financial Derivatives Pricing, IIT Ropar

---

## **License**

This project is for academic and educational purposes.

---

## **References**

- Yahoo Finance (AAL data)
- Federal Reserve Economic Data (FRED)
- Project report and notebook in this repository

---

*For questions or suggestions, please open an issue or contact the author.*
