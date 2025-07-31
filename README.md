# BlockHouse Quant Research Assignment

This repository contains the complete analysis, modeling, and implementation for the **BlockHouse Quant Research Assignment**. The project focuses on modeling **temporary market impact** and designing **optimal execution strategies** using real equity order book data from three tickers: `CRWV`, `FROG`, and `SOUN`.

---

## 🧠 Project Overview

- **Goal**: Model how large market orders impact prices temporarily and use this to design better execution strategies.
- **Approach**:
  - Resample nanosecond-level limit order book data into 1-minute snapshots.
  - Compute minute-wise slippage across different hypothetical order sizes.
  - Fit both **linear** and **power-law** impact models to estimate temporary price impact.
  - Extract time-varying coefficients (`aₜ`, `bₜ`, `cₜ`, `dₜ`) from regressions.
  - Use these models for real-time greedy allocation to minimize execution cost.
- **Outcome**:
  - Power-law model consistently outperforms linear (higher R² values).
  - Optimal allocation using power-law model leads to lower cumulative market impact.

---

## 📁 Repository Structure

```
Blockhouse-Quant-Research-Assignment/
├── complete_notebook.ipynb         # Main notebook containing full analysis
├── CRWV.zip
├── FROG.zip
├── SOUN.zip
├── ...generated_csvs                 # Fitted model coefficients and impact logs
└── README.md                       # Project documentation (you're here!)
```

---

## ⚙️ How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/saimjawed254/Blockhouse-Quant-Intern-Assignment.git
cd Blockhouse-Quant-Intern-Assignment
```

### 2. Install Dependencies

You can install the required libraries using:

```bash
pip install pandas numpy matplotlib seaborn tqdm scikit-learn scipy os glob
```

### 3. Extract Zipped Ticker Data

To bypass GitHub's 100MB upload limit, raw data files are zipped and analysis is done on one of the csvs from each ticker(2025-04-03 used here).

Extract them like this for Linux:

```bash
unzip CRWV.zip -d CRWV/
unzip FROG.zip -d FROG/
unzip SOUN.zip -d SOUN/
```

Extract them like this for Windows:

```bash
mkdir CRWV
tar -xf CRWV.zip -C CRWV
mkdir FROG
tar -xf FROG.zip -C FROG
mkdir SOUN
tar -xf SOUN.zip -C SOUN
```

Or do it manually from the system files 

After unzipping, you should have the following structure:

```
├── CRWV/
│   └── CRWV_2025-04-03_00_00_00.csv
├── FROG/
│   └── ...
├── SOUN/
│   └── ...
```

### 4. Run the Notebook

Make sure the extracted data folders are accessible, as the notebook reads directly from them.

---

## 📈 Key Outputs

- CSV logs of fitted impact model coefficients for each minute.
- R² comparison between linear and power-law models.
- Visual plots of:
  - Time-varying `aₜ`, `bₜ`, `cₜ`, `dₜ` coefficients
  - Market impact curve fitting
  - Allocation cost comparison (linear vs power-law)

---

## 🔍 Model Summary

The general power-law form used is:

g_t(x) = a_t * x + b_t * x^2 + c_t * log(x + 1) + d_t * sqrt(x)

- Fit per-minute using slippage vs order size across all three tickers.
- Used for real-time greedy allocation in execution strategy.
- Compared side-by-side with traditional linear models.

---

## 📫 Contact

For questions, feedback, or remarks:

**Saim Jawed**  
India  
saimj.ug23.cs@nitp.ac.in
saimjawed7404@gmail.com
[LinkedIn Profile](https://linkedin.com/in/saim-jawed)

---
