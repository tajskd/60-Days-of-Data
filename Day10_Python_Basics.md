# Day 10 – Python Foundations: From Installation to First Analysis

## Overview
Today marked my transition from Excel/SQL to Python. The goal was to set up a working Python environment, load my Superstore dataset, and replicate my previous analyses using Pandas. 

## Environment Setup
- **Tool:** Anaconda Distribution (includes Python, Jupyter Notebook, and 600+ data packages).
- **File Size:** 1GB+ (took a while to download and install, but worth it for the all-in-one setup).
- **Editor:** Jupyter Notebook (launched via Anaconda Navigator, runs in my web browser but executes locally on my machine).
- **Folder Structure:** All files saved in `C:\Users\[User]\Data_Analytics_60Days\`.

*Key Takeaway:* Jupyter Notebook is a web-based interface, but it is not a cloud tool. The app (Anaconda) runs the engine; the browser is just the windshield I look through.

---

## Loading the Data

After launching Jupyter and navigating to my project folder, I uploaded `superstore_clean.csv` and wrote my first Python script.

### Code:
```python
import pandas as pd

# Load the dataset
df = pd.read_csv("superstore_clean.csv")

# Quick look at the data
print(df.head())
print(df.shape)
