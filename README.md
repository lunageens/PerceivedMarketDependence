# Perceived Market Dependence and Its Effect on Stock Returns

This repository contains the data, code, and supporting materials for my master’s thesis: “Perceived Market Dependence and its Effect on Stock Returns: An Empirical Analysis of European Markets” (University of Antwerp, 2025).

<br>

## 1. Project Overview

### 1.1 Scope

Traditional asset pricing models, such as the CAPM, assume that investors measure market risk using beta—the correlation between a stock and the overall market. 
However, recent research (Ungeheuer & Weber, 2020) suggests that investors instead rely on a simpler heuristic: the frequency of comovement. Investors seem to price how often a stock moves with the market (directional comovement) more than how much it moves (beta).
This thesis tests whether frequency of comovement predicts stock returns in European markets, and compares it to traditional beta-based measures.

### 1.2 Results

- Measure: Frequency of comovement = % of days a stock’s return shares the sign of the market return.
- Finding (EU, 2002–2024): High-comovement stocks earn a significant return premium after controlling for standard factors (Carhart; FF3/FF5).
- Beta vs. comovement: Correlation between beta and comovement ≈ 0.01 → they capture different risks. Long–short high minus low comovement is positive; beta long–short is negative.
- Implication: Comovement is a distinct, behaviorally aligned dimension of market risk that helps with pricing and portfolio construction.

<br>

## 2. Repository Structure

### 2.1 What’s in here
The main directories are:

```
Documentation/                  # PDFs (thesis, academic & journalistic summaries), figures, examples
Raw data DataStream/            # Files to Reproduce Input data from DataStream (stocks/index, daily returns) + robustness folders
Raw data Factors/               # Files on Factor Data (FF3/FF5, Carhart, BAB, QMJ, etc.)
Tests/
  Main Results/                 # Notebooks, portfolio files, plots, final tables
  Robustness Tests/             # Alternative definitions, sample splits, extra diagnostics
```

### 2.2 Key files
Several inputs originate from DataStream/Robeco/Ken French libraries. Files from DataStream (daily returns, index constituents) were not uploaded, only the instruction to do so, since this a paid data source. Please ensure proper access/attribution.


```
Documentation/GeensLuna-2024.pdf – full thesis
Documentation/Samenvatting_Journalistic.pdf – readable summary; can be found in a more updated version on my Linkedin (See Link repo). 
Tests/Main Results/Data_Monthly.ipynb and Models_Monthly.ipynb – main analysis pipeline
Tests/Main Results/Monthly Results.xlsx – portfolio/alpha results
```

Plots: Return_Ranks1to5.png, CummulativeReturn_Ranks1and5.png, ComoveBeta_Ranks1and5.png, etc.
- Return_Ranks1to5.png – average returns by comovement quintile (monotonicity).
- CummulativeReturn_Ranks1and5.png – cumulative performance High vs. Low comovement.
- ComoveBeta_Ranks1and5.png – near-zero alignment between comovement and beta.

<br>

## 3. Reproducing results

**Step 1: Clone**

```
git clone https://github.com/lunageens/PerceivedMarketDependence.git
cd PerceivedMarketDependence
```
<br>

**Step 2: Environment**  
<br>
Python ≥ 3.10 recommended

```
pip install pandas numpy scipy statsmodels jupyter matplotlib openpyxl xlrd
```
<br>

**Step 3: Run the main notebook**

Open: Tests/Main Results/Data_Monthly.ipynb

Steps inside:

- Load market & stock returns (STOXX Europe 600 constituents)
- Compute monthly beta and comovement frequency
- Sort into comovement quintiles (holding comovement constant within each portfolio; beta varies)
- Form long–short portfolios (High minus Low comovement)
- Estimate alphas via CAPM, Carhart 4-factor, FF3/FF5 (Newey–West, lag=1)
- Output plots/tables → Tests/Main Results/Monthly Results.xlsx and PNG charts

<br>

**Step 4: Robustness**
<br>
See Tests/Robustness Tests/ (alternative definitions, sample splits, value-weighted portfolios, Fama–MacBeth regressions).

<br>

## 4. Additional Information

### 4.1 Cite
For proper citations, see Linkedin article, journalistic summaries, and thesis. 

Ungeheuer, M., & Weber, M. (2020). The Perception of Dependence, Investment Decisions, and Stock Prices (SSRN 2739130). 

Carhart (1997); Fama & French (1993, 2015); Newey & West (1986).

Geens, L. (2025). Perceived Market Dependence and its Effect on Stock Returns (University of Antwerp).

<br>

### 4.2 Acknowledgements

Supervised by Prof. Dr. Jan Annaert, University of Antwerp.

<br>

### 4.3 Contact

Questions or collaboration ideas? Open an issue or reach out to Luna Geens.
