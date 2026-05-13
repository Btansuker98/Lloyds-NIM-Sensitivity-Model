# Lloyds Bank – Net Interest Margin Sensitivity Model

## Overview
This project analyzes how changes in interest rates impact a bank’s profitability, focusing on:

- Net Interest Income (NII)
- Net Interest Margin (NIM)
- Net Income (after tax)

The model is based on Lloyds Bank’s historical financial data and simulates interest rate shocks (±100bps).

---

## Model Visualizations

### Base NIM Trend
Shows the evolution of Lloyds Bank's reported Net Interest Margin over time.
<img width="837" height="353" alt="nim_trend" src="https://github.com/user-attachments/assets/834c0477-ed30-45ca-af0f-da7170326dfd" />

---

### ΔNIM Sensitivity (+100bps)
Illustrates how NIM reacts to a +100bps interest rate shock.
<img width="849" height="368" alt="delta_nim" src="https://github.com/user-attachments/assets/6e967e67-5397-42cf-bffe-ed8e07d9efd9" />

---

### ΔNII Sensitivity (+100bps)
Shows the impact of interest rate increases on Net Interest Income.
<img width="829" height="377" alt="delta_nii" src="https://github.com/user-attachments/assets/2280f7fc-ee44-48db-94d1-d128002679ce" />

---

## Key Objective
To quantify how interest rate movements translate into:

- ΔNII (earnings sensitivity)  
- ΔNIM (bps change in margin)  
- ΔNet Income (shareholder impact)  

---

## Banking Fundamentals

Banks operate as financial intermediaries:

- Borrow from depositors  
- Lend to customers  

👉 Profit driver:
**Spread = Loan Yield − Deposit Cost**

---

## Core Metric: Net Interest Margin (NIM)

NIM = Net Interest Income / Average Interest-Earning Assets (AIEA)

NIM measures the bank’s ability to generate income from its assets.

---

## Model Structure

The model is structured into four main components:

### 1. Raw Data (01_RawData)
- Historical financials from Lloyds Bank annual reports
- Loans, deposits, funding, AIEA
- Reported Banking NIM

### 2. Control Panel (00_Control)
- Model assumptions (betas, repricing speeds)
- Tax rate
- Hedge adjustment factor

### 3. Scenario Engine (02_Scenarios)
Applies interest rate shocks to the balance sheet.

### 4. Summary Outputs (03_Summary)
- Base NIM (reported)
- ΔNII (±100bps)
- ΔNIM (bps)
- ΔNet Income
- Hedged results

---

## Model Calibration

The model is calibrated using reported data:


Implied NII = Reported NIM × AIEA

This ensures alignment with actual bank profitability.

---

## Core Model Logic


ΔNII =
Loans × βL × repricingL × shock
− Deposits × βD × repricingD × shock
− Funding × βF × repricingF × shock

New NIM = (Base NII + ΔNII) / AIEA

---

## Key Drivers

### 1. Beta (Pass-through)
Measures how much of interest rate changes are passed to customers.

- Loan Beta → impacts asset yield  
- Deposit Beta → impacts funding cost  
- Funding Beta → market-driven  

---

### 2. Repricing Speed
Determines how quickly balances adjust (within 12 months).


Effective Sensitivity = Beta × Repricing

---

## Key Insight

👉 **Beta Spread drives profitability**


Beta Spread = Loan Beta − Deposit Beta

- Higher spread → higher profitability  
- Lower deposit beta → competitive advantage  

---

## Scenario Analysis

The model simulates:

- +100bps rate increase  
- -100bps rate decrease  

Outputs include:

- Change in earnings (ΔNII)  
- Change in margin (ΔNIM)  
- Post-tax impact (ΔNet Income)  

---

## Hedge Adjustment

A hedge factor is applied to reflect risk management practices:

- Adjusted ΔNII  
- Adjusted ΔNIM  
- Adjusted ΔNet Income  

---

## Key Conclusion

When interest rates rise:

- Loans reprice faster ✅  
- Deposits reprice slowly ✅  
- Funding reprices quickly ❌  

👉 Net effect: **Bank benefits from rising interest rates**

---

## Limitations

- Linear model  
- No lag effects  
- No rate floors  
- No segment-level breakdown  

---

## Disclaimer

This model is created for personal learning purposes only.  
All financial data is sourced from publicly available Lloyds Bank annual reports.  
The model does not constitute financial advice.
