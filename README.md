# From Traditional to Unmanned: Which Retail Checkout System is the Most Profitable?

---

## Project Overview

This project conducts a comprehensive financial and qualitative analysis to evaluate the viability of three retail checkout systems for a Singaporean convenience store context:

- **Alternative 1**: Conventional Checkout System (2 cashiers)
- **Alternative 2**: Four-Unit Self-Checkout System (1 support staff)
- **Alternative 3**: Checkout-free / Unmanned System (Pick 'N' Go)

The analysis spans a 3-year study period aligned with a typical commercial lease term in Singapore, incorporating both financial modelling and customer preference analysis to produce an actionable recommendation for retailers.

---

## Methods & Techniques

### 1. After-Tax Cash Flow (ATCF) Modelling
Built discounted cash flow models for each alternative incorporating initial investment, one-off PSG grant subsidies, annual benefits, O&M costs, manpower costs, shrinkage costs, and salvage value. Applied Singapore's corporate tax rate (17%) and a 3-year Capital Allowance Scheme. Computed **Present Worth (PW)** at MARR = 10% for base-case comparison.

| Alternative | Base Case PW |
|---|---|
| Conventional Checkout | $93,556.21 |
| Self-Checkout (4-unit) | $117,009.83 ✅ |
| Checkout-free / Unmanned | -$495,853.69 ❌ |

### One-Way Range Sensitivity Analysis (Tornado Charts)
Generated tornado charts using **Excel + Sensit** to identify the most sensitive input factors for each alternative's PW. Key findings:
- Alt 1: Annual benefits, manpower cost, and O&M cost are most sensitive
- Alt 2: Annual sales volume, one-off subsidy, and initial investment are most sensitive
- Alt 3: Initial investment, annual benefits, and market value at EoY 3 are most sensitive

### Monte Carlo Simulation (Python)
Ran **100,000 simulation trials** modelling uncertainty in all cost and benefit inputs using appropriate probability distributions (triangular, normal, uniform). Computed expected PW, standard deviation, downside risks, upside potentials, and Value-at-Risk (VaR) for each alternative. Also simulated IRR distributions for Alternatives 1 and 2.

| Alternative | Mean PW | Std Dev | P(PW ≤ 0) |
|---|---|---|---|
| Conventional | $112,668 | $50,926 | 1.32% |
| Self-Checkout | $177,679 | $76,103 | 0.96% |
| Unmanned | -$854,891 | $208,593 | ~100% |

### 4. Probabilistic Risk Analysis with @Risk
Re-ran simulations using **@Risk** with alternative distribution choices (lognormal for O&M and manpower costs) to validate Python results. Computed expected after-tax PW and IRR distributions, upside/downside probabilities, and performed **stochastic dominance** and **mean-variance dominance** analysis across all three alternatives.

### 5. What-If Scenario Analysis (Rainbow Diagrams)
Conducted break-even and sensitivity analysis on initial investment cost and annual sales volume for each pair of alternatives. Derived algebraic break-even points and decision rules, e.g.:
- Alt 1 vs Alt 2: Alt 2 preferred for all feasible initial costs of Alt 1
- Alt 3 vs Alt 1/2: Alt 3 requires a **+580.69%** increase in annual sales to become competitive

### 6. Analytical Hierarchy Process (AHP)
Surveyed 5 shoppers (aged 21–40) to assess qualitative checkout preferences across three criteria: **wait time**, **smoothness**, and **customer service**. Derived normalised eigenvector matrices and calculated composite weights for each alternative.

Criteria weights: Wait Time (49.31%) > Smoothness (31.21%) > Customer Service (19.49%)

Overall AHP ranking: Unmanned Shop (0.42) > Self-Checkout (0.30) > Conventional Cashier (0.28)

> Notably, this creates a financial–qualitative trade-off: the checkout-free system is most preferred by customers but financially infeasible within a 3-year horizon.

---

## Key Findings & Recommendation

Based on both financial and qualitative analysis, **Alternative 2 (Self-Checkout)** is the recommended option for most retailers, as it offers the highest base-case PW, the lowest probability of loss across simulations, and competitive customer experience scores.

**Alternative 1** remains a sound fallback for risk-averse retailers or those with limited upfront capital, given its lower variance and consistently positive returns.

**Alternative 3** is not financially viable within a 3-year study period under any realistic sales scenario, a finding that aligns with real-world observations such as Amazon's removal of its Just Walk Out technology from Amazon Fresh stores.

---

## Tools & Languages

- **Python** — NumPy, SciPy, Matplotlib (Monte Carlo simulation)
- **Excel** — Cash flow modelling, sensitivity analysis, AHP matrices
- **Sensit** — Tornado chart generation
- **@Risk** — Probabilistic simulation and distribution fitting
