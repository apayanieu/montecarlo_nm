# Monte Carlo Simulation for Option Pricing  
A Numerical Methods Project

---

## 1. Project Overview

This repository contains a self-contained numerical study of **Monte Carlo simulations for option pricing**.

The main goals are:

- To implement and analyze **Monte Carlo pricing** for:
  - A **European call option** (model with closed-form solution).
  - An **arithmetic Asian call option** (no simple closed-form solution).
- To study **convergence properties** of Monte Carlo estimators:
  - As the number of simulated paths \(N\) increases.
  - As the time discretization \(M\) is refined for path-dependent options.
- To connect the theory with **real financial data**, using:
  - Historical prices of the SPDR S&P 500 ETF (SPY) to estimate volatility.
  - Real SPY option prices to compare model prices vs market prices and to compute **implied volatility**.

---

## 2. The Notebook:

The core of the project is implemented in a single Jupyter notebook:

- `montecarlo.ipynb`  
  Main notebook containing:
  - Theoretical setup and model description (Black–Scholes).
  - Monte Carlo pricing of a European call.
  - Monte Carlo pricing of an arithmetic Asian call.
  - Variance reduction via a geometric Asian control variate.
  - Convergence experiments in \(N\) and \(M\).
  - Historical SPY data download and volatility estimation.
  - Comparison of model prices to **real SPY option market prices**.
  - Computation of implied volatility.
    
---

## 3. Mathematical & Numerical Focus

The project focuses on **Monte Carlo simulation as a numerical estimation of expectations**,
with:

- Convergence justified by the **Law of Large Numbers (LLN)**.
- Fluctuations of order \(O(N^{-1/2})\) described by the **Central Limit Theorem (CLT)**.

In this context:

1. **European Call (Benchmark Problem)**  
   Under Black–Scholes, the discounted payoff of a European call has an analytic price:

   - The notebook:
     - Implements the **closed-form Black–Scholes formula**.
     - Simulates terminal prices \(S_T\) via geometric Brownian motion.
     - Compares Monte Carlo estimates to the analytic value.
     - Empirically confirms the \(O(N^{-1/2})\) convergence rate.

2. **Asian Call (Path-Dependent Problem)**  
   The arithmetic Asian option does not have a simple closed-form price:

   - The notebook:
     - Simulates full GBM paths on a time grid with \(M\) steps.
     - Computes the arithmetic average of the path and its discounted payoff.
     - Studies sensitivity to both:
       - Number of paths \(N\),
       - Time discretization \(M\).
     - Uses a **geometric Asian option** with known analytic price as a **control variate** to reduce variance.

3. **Real Data & Model vs Market**

   The notebook:

   - Downloads SPY historical prices.
   - Computes daily log-returns and annualized **historical volatility**.
   - Uses this historical volatility:
     - In the Black–Scholes formula.
     - In Monte Carlo simulations for a European call.
   - Downloads a SPY option chain, selects a near-ATM call, and:
     - Compares model prices (BS & MC with historical vol) to the **market price**.
     - Computes the **implied volatility** from the market price.

---

## 4. Setup & Dependencies

### 4.1. Software Requirements

- Python 3.9+ (3.10+ recommended)
- Jupyter Notebook

Python packages:

- `numpy`
- `scipy`
- `pandas`
- `matplotlib`
- `yfinance`
- `datetime` (standard library)
- `typing` (standard library, for type hints if used)
