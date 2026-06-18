# 📊 UPI Transaction Pattern EDA (2017–2025)
### India's Digital Payment Revolution — End-to-End Analysis

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=flat&logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-5.x-3F4F75?style=flat&logo=plotly&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-2ea44f?style=flat)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat)

---

## 📌 Table of Contents
1. [Project Overview](#project-overview)
2. [Problem Statement](#problem-statement)
3. [Dataset Description](#dataset-description)
4. [Project Structure](#project-structure)
5. [Key Findings](#key-findings)
6. [Technologies Used](#technologies-used)
7. [How to Run](#how-to-run)
8. [Visualisations](#visualisations)
9. [Data Source & Calibration](#data-source--calibration)
10. [Author](#author)

---

## 🎯 Project Overview

This project performs a comprehensive **Exploratory Data Analysis (EDA)** on **52.5 Lakh UPI transactions** spanning 9 years (2017–2025) across 7 major UPI applications. The analysis covers the complete lifecycle of India's digital payment revolution — from the early Paytm-dominated era to the PhonePe–Google Pay duopoly of 2025.

The dataset has been calibrated to real **NPCI monthly statistics**, ensuring all transaction volumes, app market shares, failure rates, and P2P/P2M ratios reflect published benchmark figures.

---

## ❓ Problem Statement

India's UPI ecosystem processed over **₹20 lakh crore** in transactions in FY2024–25 — yet the story behind the numbers remains underexplored. This project answers 12 core analytical questions:

| # | Question |
|---|----------|
| 1 | How did UPI transaction volume grow from 3L (2017) to 52.5L (2025 sample)? |
| 2 | Which UPI app dominated each year — and how did Paytm fall from 38% to 6%? |
| 3 | Is the average ticket size rising or declining — and what does that signal? |
| 4 | How did COVID-19 permanently reshape digital payment habits? |
| 5 | Which hours, days, and festive events drive peak UPI activity? |
| 6 | How did P2M (merchant payment) share grow from 22% to 65%? |
| 7 | What is the Diwali / festive season effect on UPI volumes? |
| 8 | Which Indian states lead in UPI transaction volume and value? |
| 9 | How has the failure rate improved from 28% (2018) to 1.5% (2025)? |
| 10 | What is driving the explosive growth of ₹0–100 micro-transactions? |
| 11 | Which banks are the most active sender and receiver banks? |
| 12 | What does the volume–value divergence tell us about India's payment habits? |

---
## 📁 Dataset Description 

⚠️ Due to GitHub file size limitations, the complete dataset is not included in this repository.

Dataset Download

🔗 Google Drive Link: (https://drive.google.com/drive/folders/1wwvhQhBj2u4R3Nc7PVGpkmhzhbMHXIE2?usp=drive_link)

The dataset contains approximately 52.5 lakh UPI transactions covering the period from 2017 to 2025.

After downloading, place the CSV files inside the following folder structure:


├── data/
    ├── upi_transactions_2017.csv
    ├── upi_transactions_2018.csv
    ├── upi_transactions_2019.csv
    ├── upi_transactions_2020.csv 
    ├── upi_transactions_2021.csv
    ├── upi_transactions_2022.csv
    ├── upi_transactions_2023.csv
    ├── upi_transactions_2024.csv
    └── upi_transactions_2025.csv

## 📁 Dataset Overview

| File | Year | Rows | Key Event |
|------|------|------|-----------|
| `upi_transactions_2017.csv` | 2017 | 3,00,000 | UPI launches — Paytm, BHIM, PhonePe available |
| `upi_transactions_2018.csv` | 2018 | 4,00,000 | Amazon Pay enters |
| `upi_transactions_2019.csv` | 2019 | 5,00,000 | PhonePe vs GPay battle begins |
| `upi_transactions_2020.csv` | 2020 | 5,50,000 | WhatsApp Pay enters (Nov 2020) |
| `upi_transactions_2021.csv` | 2021 | 6,00,000 | Post-COVID digital surge |
| `upi_transactions_2022.csv` | 2022 | 6,50,000 | Duopoly consolidates |
| `upi_transactions_2023.csv` | 2023 | 7,00,000 | P2M dominance era |
| `upi_transactions_2024.csv` | 2024 | 7,50,000 | ₹20 lakh crore monthly milestone |
| `upi_transactions_2025.csv` | 2025 | 8,00,000 | Micro-payment dominance |
| **Total** | **2017–2025** | **52,50,000** | 9 years · 22 columns · 7 apps |

### 📋 Column Reference

| Column | Type | Description |
|--------|------|-------------|
| `txn_id` | string | Unique transaction identifier |
| `datetime` | datetime | Full timestamp of transaction |
| `date` | date | Date of transaction |
| `year`, `month`, `day` | int | Date components |
| `month_name`, `day_of_week` | string | Readable date labels |
| `hour`, `minute`, `second` | int | Time components |
| `app` | category | UPI app (PhonePe, GPay, Paytm, BHIM, etc.) |
| `app_launch_year` | int | Verified launch year per app |
| `txn_type` | category | P2P (person-to-person) or P2M (person-to-merchant) |
| `category` | category | Transaction category (Transfer, Food, Rent, etc.) |
| `amount_rs` | float | Transaction amount in ₹ |
| `ticket_segment` | category | Amount bucket (₹0–100, ₹101–500, etc.) |
| `sender_bank` | category | Originating bank |
| `receiver_bank` | category | Receiving bank |
| `sender_state` | category | State of sender |
| `receiver_state` | category | State of receiver |
| `status` | category | Success / Failed / Pending |
| `failure_reason` | category | Reason if failed (else 'NA') |
| `is_weekend` | int | 1 if Saturday/Sunday |
| `is_festive_season` | int | 1 if in Diwali/Holi/New Year window |
| `hour_bucket` | category | Time-of-day label (Morning Peak, Evening Peak, etc.) |

> ⚠️ **App Launch Accuracy (Browser-Verified):** PhonePe (Aug 2016) · Paytm UPI (Oct 2016) · BHIM (Dec 2016) · Google Pay/Tez (Sep 2017) · Airtel Pay (2017) · Amazon Pay (2018) · WhatsApp Pay (Nov 2020). Each app appears **only from its verified launch year**.

---

## 🗂️ Project Structure

```
upi-transaction-pattern-eda/
│
├── data/
│   ├── upi_transactions_2017.csv
│   ├── upi_transactions_2018.csv
│   ├── ...
│   └── upi_transactions_2025.csv
│
├── UPI_EDA_Project.ipynb        ← Main analysis notebook
├── visuals/                     ← Auto-generated charts (.html, .png)
│   ├── viz_01_app_dist.png
│   ├── viz_02_market_rev.png
│   └── ...
│
├── README.md                    ← This file
└── requirements.txt             ← Python dependencies
```

---

## 🔍 Key Findings

| # | Finding | Data Evidence |
|---|---------|---------------|
| 1 | **600× volume growth** | 3L txns (2017) → 52.5L sample (2025) |
| 2 | **Paytm's fall from grace** | 38% share (2017) → 6% (2025) — RBI restrictions + competition |
| 3 | **Ticket size declining** | ₹2,800 avg (2017) → ₹1,100 (2025) — UPI became micro-payment tool |
| 4 | **P2M dominance** | 22% → 65% — UPI is now India's primary merchant payment rail |
| 5 | **WhatsApp Pay absent before Nov 2020** | Verified against NPCI approval date |
| 6 | **COVID accelerated adoption permanently** | No reversal post-lockdown |
| 7 | **Failure rate collapsed** | 28% (2018) → 1.5% (2025) |
| 8 | **Festive season spike** | Oct–Nov consistently 20–30% above baseline |
| 9 | **Maharashtra leads** | Top state by both volume and value |
| 10 | **₹0–100 exploded** | 8% share (2017) → 31% (2025) — chai, auto, groceries |
| 11 | **Twin daily peaks** | 9–11am (commute/commerce) and 7–9pm (evening retail) |
| 12 | **SBI + HDFC = 40% of all transactions** | Dominant retail bank rails |

---

## 🛠️ Technologies Used

| Library | Version | Purpose |
|---------|---------|---------|
| `pandas` | ≥ 2.0 | Data loading, cleaning, groupby, merging |
| `numpy` | ≥ 1.24 | Numerical operations, array manipulation |
| `matplotlib` | ≥ 3.7 | Static charts — bars, lines, pies, heatmaps |
| `seaborn` | ≥ 0.12 | Statistical visualisations — violin, heatmap, KDE |
| `plotly` | ≥ 5.14 | Interactive charts — stacked bars, scatter, sunburst |
| `jupyter` | ≥ 6.5 | Notebook environment |

---

## 🚀 How to Run

### Step 1 — Clone the repository
```bash
git clone https://github.com/shubhampatil75/upi-transaction-pattern-eda.git
cd upi-transaction-pattern-eda
```

### Step 2 — Install dependencies
```bash
pip install -r requirements.txt
```

### Step 3 — Set your data path
Open `UPI_EDA_Project.ipynb` and update `DATA_PATH` in **Phase 2 — Cell 1**:
```python
DATA_PATH = r"C:\Your\Path\To\Data"   # ← Change this
```

### Step 4 — Run the notebook
```bash
jupyter notebook UPI_EDA_Project.ipynb
```
Then go to **Kernel → Restart & Run All**.

---

## 📊 Visualisations

The notebook generates **22 charts** across 12 phases:

| Phase | Chart | Library |
|-------|-------|---------|
| 4 | Transaction status split · App distribution · Category bar · Amount histogram | Plotly + Matplotlib |
| 5 | Monthly volume trend · YoY growth · Seasonality heatmap | Plotly + Seaborn |
| 6 | App share stacked bar · Bank analysis · Ticket size comparison | Plotly + Matplotlib |
| 7 | Hourly pattern · Day-of-week · Festive vs Normal | Plotly + Matplotlib |
| 8 | P2P vs P2M shift · P2M share line | Plotly |
| 9 | Failure rate trend · Failure reasons heatmap | Matplotlib + Seaborn |
| 10 | State volume · State avg amount | Plotly |
| 11 | Ticket segment evolution · Category amount heatmap | Plotly + Seaborn |

All interactive charts are saved to the `visuals/` folder as `.html` files.

---

## 📌 Data Source & Calibration

This is a **synthetic dataset calibrated to real NPCI benchmark figures**:

| Metric | Source | Value Used |
|--------|--------|-----------|
| Monthly transaction volumes | NPCI official statistics | Matched year-wise |
| App market shares | NPCI, Inc42, Economic Times | PhonePe 49%, GPay 37% (2025) |
| Failure rate trend | RBI Payment System Report | 28% (2018) → 1.5% (2025) |
| P2M share | NPCI Annual Report | 22% (2017) → 65% (2025) |
| Average ticket size | RBI Annual Report | ₹2,800 (2017) → ₹1,100 (2025) |
| WhatsApp Pay launch | NPCI official | November 2020 |

---

## 👤 Author

**Shubham Patil** — Data Science & Analytics | 
- 📧 Email: shubhampatil752002@gmail.com
- 🔗 LinkedIn: https://www.linkedin.com/in/shubham-patil-340aa5272
- 🐙 GitHub: https://github.com/shubhampatil75

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

*⭐ If you found this project helpful, please star the repository!*
