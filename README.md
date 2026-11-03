# Task 25: Basic Data Cleaning - Titanic Dataset

## Project Overview
This project demonstrates a fundamental end-to-end data cleaning workflow on the **Titanic Dataset**. Data cleaning is a critical step in the machine learning lifecycle to transform raw, noisy data into a reliable, high-quality dataset suitable for analysis and model training.

---

## Deliverables
- **Original Dataset:** `titanic.csv`
- **Cleaned Dataset:** `titanic_cleaned.csv`
- **Jupyter Notebook:** Data cleaning notebook with code cells and markdown explanations
- **Documentation:** `README.md` (this file)

---

## Tools Used
- **Python 3**
- **Pandas** (Data manipulation and cleaning)
- **NumPy** (Numerical operations)
- **Jupyter Notebook** (Interactive environment)

---

## Data Cleaning Steps & Decisions

### 1. Data Inspection
- Loaded `titanic.csv` into a Pandas DataFrame.
- Checked structural details (`df.info()`), dataset shape, initial rows, and existing column data types.

### 2. Missing Value Identification & Handling
- **`age`**: Found missing values across rows. Missing values were imputed using the dataset's **median age** ($28.0$ years) to preserve distribution without skewing from extreme values.
- **`embarked` / `embark_town`**: Missing categorical entries were imputed using the **mode** (most frequent value, `'S'` / `'Southampton'`).
- **`deck`**: Identified a high proportion of missing values (only 202 non-null entries remaining out of 781 after duplicate removal). Kept as-is or dropped during feature selection depending on downstream model requirements.

### 3. Duplicate Removal
- Checked for identical rows across the dataset.
- Removed **110 duplicate rows**, reducing total records from the initial row count to **781 clean records**.

### 4. Data Type Correction & Standardization
- Converted non-numeric and categorical variables (`sex`, `embarked`, `class`, `who`, `deck`, `embark_town`, `alive`) into standardized object/string and category dtypes to optimize memory and ensure correct analytical representation.

---

## Final Dataset Summary

| Metric / Attribute | Value |
| :--- | :--- |
| **Total Cleaned Rows** | 781 |
| **Duplicates Removed** | 110 |
| **Average Survived Rate** | ~41.36% |
| **Median Age** | 28.0 years |
| **Mean Fare** | $34.75 |

---

## Interview Questions & Answers

### Q1: What is data cleaning?
**Answer:**  
Data cleaning is the process of identifying, correcting, or removing incomplete, duplicate, incorrectly formatted, corrupt, or redundant data from a dataset. It ensures data consistency, reliability, and accuracy before feeding data into analytical tools or machine learning algorithms.

---

### Q2: Why is data cleaning important before machine learning?
**Answer:**  
- **Garbage In, Garbage Out (GIGO):** Machine learning models learn patterns directly from the input data. Inaccurate or noisy data leads to biased or flawed model predictions.
- **Prevents Pipeline Failures:** Algorithms in libraries like Scikit-Learn cannot natively handle `NaN` values or inconsistent data types, leading to execution crashes.
- **Improves Model Efficiency & Accuracy:** Clean data helps algorithms converge faster during optimization and leads to better generalization on unseen testing data.

---

### Q3: What problems can poor-quality data cause?
**Answer:**  
- **Biased Models & False Conclusions:** Duplicate records skew summary statistics (e.g., mean, variance), which misleads stakeholders and skews decision-making.
- **Overfitting & Noise:** Unhandled outliers and corrupt entries can cause models to memorize noise rather than learning genuine relationships.
- **System Errors & High Maintenance:** Unformatted data types (such as numbers formatted as text strings) create bugs during feature encoding and pipeline deployment.
