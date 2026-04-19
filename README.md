# Anomaly Detection & Outlier Analysis: Bangkok Airbnb Market

This repository focuses on identifying and analyzing statistical anomalies within the **Bangkok Airbnb** dataset (17,432 listings). The goal is to ensure data integrity and detect "noise", such as price typos or suspicious listing behaviors—before the data is used for further business reporting.

---

## 📖 Key Definitions

Before diving into the analysis, it is important to understand the specific terminology used in this project:

* **Anomaly:** A data point that is so different from others that it raises suspicion it was created by an error or a different process (e.g., a typo or a scam).
* **Outlier:** A value that is "outside" the normal range of the rest of the data.
* **Robust:** A statistical method that is strong enough to not be easily ruined or "confused" by extreme errors.
* **Dimension:** In data, this refers to the number of variables (columns) being looked at at the same time.
* **Threshold:** A limit or "boundary" line. If a number crosses this line, it is flagged as an anomaly.

---

## 🛠️ Analysis Framework

The analysis is divided into three levels of complexity based on the number of variables examined simultaneously.

### 1. Univariate Analysis (Single Variable)
Focuses on identifying outliers in a single column (e.g., `price`).

| Method | Description | Formula / Threshold |
| :--- | :--- | :--- |
| **Z-Score** | Measures how many standard deviations a point is from the average. | $$z = \frac{x - \mu}{\sigma}$$ |
| **IQR** | Uses the middle 50% of data to set "fences" or boundaries. | $$Q_{3} + (1.5 \times IQR)$$ |
| **MAD** | A version of the Z-score that uses the median to avoid being influenced by extreme errors. | $$\text{median}(|x_{i} - \tilde{x}|)$$ |

**Visual Tools:** Histograms and Box Plots.

---

### 2. Bivariate Analysis (Two Variables)
Examines the relationship between two columns to find "broken rules" (e.g., a price that doesn't make sense for a specific location).

* **Scatterplots:** Used to visually see dots that fall far from the main group.
* **Correlation Coefficient:** A number between -1 and 1 that describes how two variables move together.
* **Residual Analysis:** Calculates the "leftover" error between the actual price and what a mathematical model predicted the price should be.
    * **Residual Formula:** $$\text{Actual} - \text{Predicted}$$

---

### 3. Multivariate Analysis (Multiple Variables)
Detects complex anomalies by looking at patterns across many columns at once (Price, Reviews, Availability, etc.).

* **Isolation Forest:** An algorithm that "isolates" points. Outliers are "lonely" and different, so they are separated much faster than normal points.
* **One-Class SVM:** Draws a mathematical "fence" around the densest area of data. Anything outside this fence is flagged.

---

## 🚀 Getting Started

### Prerequisites
You will need Python installed along with the following libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn pyod
```

**Usage**

Clone the repository:

```bash
git clone [https://github.com/hyunito/anomaly-detection-and-outliers.git](https://github.com/hyunito/anomaly-detection-and-outliers.git)
```
Ensure listings_bangkok.csv is in the root directory.

Run the Jupyter Notebooks to see the visual and statistical analysis.
