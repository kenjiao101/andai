# Poverty and Internet Access in Indonesia: A Statistical Case Study (2024)

### Analyzing poverty and internet access across Indonesian provinces using correlation, regression, and chi-square testing to quantify Indonesia's digital divide.

## 📝 Table of Contents

1. [Overview](#-overview)
2. [Problem Statement](#-problem-statement)
3. [Dataset](#-dataset)
4. [Tech Stack](#-tech-stack)
5. [Screenshots](#-screenshots)
6. [Results and Performance](#-results-and-performance)
7. [Getting Started](#-getting-started)
8. [Limitations](#-limitations)

---

## 📌 Overview

This project is a statistical analysis examining the relationship between poverty and household internet access across Indonesian provinces. It combines exploratory data analysis with two independent testing approaches: a continuous approach using Pearson correlation and linear regression, and a categorical approach using chi-square and Fisher's exact tests, applied to 2024 data from BPS (Statistics Indonesia) covering `37` provinces. The workflow moves from data cleaning and merging, through univariate and bivariate exploration, into regression modeling with full assumption checks, then into categorical association testing with effect size and post-hoc comparisons. The output is a cross-validated finding: poverty rate and internet access are strongly associated, confirmed independently by both the continuous and the categorical method.

## ❓ Problem Statement

**Konteks:** Internet access varies widely across Indonesian provinces, from over `97%` in Kepulauan Riau to just above `12%` in Papua Pegunungan, and poverty rates show a similarly wide spread, from `4.00%` to `32.97%`. Both patterns are individually well documented in routine BPS reporting.

**Gap:** What routine descriptive reporting does not answer is whether these two patterns are statistically connected, and if so, how strongly, how reliably, and whether the relationship holds up when tested through more than one statistical method.

**Solusi:** This project tests the poverty-internet access relationship using two independent methods: a continuous approach (Pearson correlation and linear regression, with full assumption checking) and a categorical approach (chi-square test of independence and Fisher's exact test, with effect size and post-hoc comparison), then checks whether the two methods agree.

## 📊 Dataset

### Metadata

| Attribute | Detail |
|---|---|
| **Source** | BPS (Badan Pusat Statistik / Statistics Indonesia), 2 tables |
| **Link** | [Internet Access Table](https://www.bps.go.id/id/statistics-table/2/Mzk4IzI=/persentase-rumah-tangga-yang-pernah-mengakses-internet-dalam-3-bulan-terakhir-menurut-provinsi-dan-klasifikasi-daerah.html), [Poverty Rate Table](https://www.bps.go.id/id/statistics-table/2/MTkyIzI=/persentase-penduduk-miskin--p0--menurut-provinsi-dan-daerah.html) |
| **Format** | CSV |
| **Size** | `37` rows (provinces) x `5` columns after cleaning and merge |
| **License** | Not verified, check BPS terms of use before redistributing the raw CSVs |
| **Time Coverage** | `2024` (poverty figure uses March 2024 / Semester 1 for temporal consistency) |
| **Accessed on** | `[Fill in actual data access date]` |

### Data Dictionary (Key Columns)

| Column | Data Type | Description | Example Value |
|---|:---:|---|---|
| `Provinsi` | `str` | Province name, standardized to uppercase | `"PAPUA PEGUNUNGAN"` |
| `Kemiskinan_Persen` | `float` | Poverty rate, percentage of poor population (P0), March 2024 | `32.97` |
| `Internet_Total` | `float` | **Target variable** - percentage of households with internet access in the last 3 months | `12.15` |
| `Kategori_Kemiskinan` | `str` | **Derived variable** - poverty rate binned into Low / Medium / High by quartile | `"Tinggi"` |
| `Kategori_Internet` | `str` | **Derived variable** - internet access binned into Low / Medium / High by quartile | `"Rendah"` |

## 🛠️ Tech Stack

| Layer | Technology | Role in the Project |
|:---:|:---:|---|
| Language | Python 3 | Core language for data cleaning, statistical testing, and visualization |
| Environment | Google Colab | Interactive execution, exploration, and staged reporting |
| Data Processing | Pandas, NumPy | Cleaning, province-name standardization, merging, quartile-based categorization |
| Visualization | Matplotlib, Seaborn | Distribution plots, scatter plots with trendlines, contingency heatmaps, regression diagnostic plots |
| Statistical Modeling | Scikit-learn | Linear regression fitting (`LinearRegression`), `R²` calculation |
| Statistical Testing | SciPy (`scipy.stats`) | Pearson correlation, F-test, t-test, Shapiro-Wilk, Breusch-Pagan, chi-square, Fisher's exact test |
| Version Control | Git + GitHub | Source control and documentation of changes |

## 🎥 Screenshots

### Poverty Rate vs. Internet Access (Bivariate Relationship)

<p align="center">
  <img width="700" height="430" alt="image"
       src="[URL gambar - scatter plot bivariate dari notebook section 3.3 Analisis Bivariate]" />
</p>

Provinces with higher poverty consistently cluster toward lower internet access, with a Pearson correlation of `r = -0.8215` across the `37` provinces analyzed.

### Linear Regression Fit

<p align="center">
  <img width="700" height="430" alt="image"
       src="[URL gambar - regression plot dari notebook section 5.6 Visualisasi Regresi]" />
</p>

The fitted line, `Internet Access = 108.16 - 1.96 x Poverty Rate`, explains `R² = 0.6748` of the variance and is statistically significant at `p < 0.001`.

### Poverty vs. Internet Access Crosstabulation

<p align="center">
  <img width="600" height="450" alt="image"
       src="[URL gambar - heatmap crosstabulation dari notebook section 4.5 atau 6.4 Visualisasi Chi-Square]" />
</p>

Of the `10` provinces in the high-poverty tier, `7` fall into the low-internet-access tier against an expected count of only `2.43`, the single largest contributor to the chi-square statistic at `42.50%`.

### Fisher's Exact Test: High-Poverty vs. High-Access Provinces

<p align="center">
  <img width="800" height="400" alt="image"
       src="[URL gambar - visualisasi tabel 2x2 dari notebook section 6.3.1 Fisher's Exact Test]" />
</p>

None of the provinces in the high-poverty tier reach the high-internet-access tier (`Odds Ratio = 0`), a pattern confirmed as statistically significant by Fisher's exact test at `p = 0.036`.

## 📈 Results and Performance

### Method Comparison Summary

| Method | Statistic | Value | p-value | Conclusion |
|:---:|:---:|:---:|:---:|---|
| Pearson Correlation | `r` | `-0.8215` | `< 0.001` | Very strong negative correlation |
| Linear Regression | `R²` | `0.6748` | `< 0.001` (F-test) | Poverty explains `67.48%` of variance in internet access |
| Chi-Square Test | `chi-square` | `20.18` | `< 0.001` | Significant association between categories |
| Fisher's Exact Test | `Odds Ratio` | `0` | `0.036` | Confirms zero high-poverty / high-access overlap |

### Key Findings

1. **Poverty rate and internet access are very strongly and negatively correlated.** Pearson correlation across `37` provinces is `r = -0.8215` (`R² = 0.6748`, `p < 0.001`), meaning poverty alone explains about two-thirds of the variance in provincial internet access.
2. **Each 1 percentage point increase in poverty is associated with roughly a 2 percentage point drop in internet access.** The fitted model is `Internet Access = 108.16 - 1.96 x Poverty Rate`, significant overall (`F = 72.62`, `p < 0.001`) and at the coefficient level (`t = -8.52`, `p < 0.001`, 95% CI `[-2.43, -1.49]`), valid within the observed poverty range of `4.00%` to `32.97%`.
3. **The regression's homoscedasticity and independence assumptions are violated, so its p-values should be read as approximate.** Residuals pass the normality test (`Shapiro-Wilk p = 0.09`) but fail the Breusch-Pagan homoscedasticity test (`p < 0.001`) and show a Durbin-Watson statistic of `1.04`, below the acceptable `1.5` to `2.5` range.
4. **A categorical test independently confirms the relationship, with a very strong effect size.** Splitting both variables into Low / Medium / High tiers by quartile, chi-square testing shows a significant association (`chi-square = 20.18`, `df = 4`, `p < 0.001`), with Cramer's V at `0.5222`, classified as very strong for a `3x3` table.
5. **Because most contingency cells were too sparse for chi-square, Fisher's exact test was used as a more reliable check.** With `77.8%` of cells below the expected-frequency-of-5 threshold, a collapsed `2x2` table (High poverty vs. Low-Medium, crossed with High access vs. Low-Medium) was tested with Fisher's exact test, confirming significance at `p = 0.036`.
6. **Not one high-poverty province reaches high internet access.** The `2x2` table shows an odds ratio of `0`: zero provinces combine a high-poverty classification with high internet access, the most extreme form of the pattern the regression already pointed to.
7. **The high-poverty, low-access combination is the single largest driver of the chi-square result.** It contributes `42.50%` of the total chi-square statistic, with `7` provinces observed against an expected `2.43`, a standardized residual of `2.93`.
8. **The categorical and continuous methods reach the same conclusion independently.** Cramer's V (`0.52`) and Pearson's r (`-0.82`) are both classified as "very strong" by their respective conventional thresholds, a meaningful robustness check on the overall finding.

## 🚀 Getting Started

> This project is part of a larger collection repository. Clone the collection repo first (see the root README), then navigate into this folder.

1. Navigate to this project folder:
```bash
cd digital-divide-indonesia
```

2. Create a virtual environment (Optional):
```bash
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Download the two datasets from the links in the [Dataset](#-dataset) section, then place them in `data/raw/`.

5. **Important, reproducibility note**: the original notebook was developed in Google Colab and uses the file upload widget (`google.colab.files.upload()`) in section 1.2. To run it locally (Jupyter/VS Code), replace that cell with direct file reading from a local folder:
```python
df_internet_raw = pd.read_csv('data/raw/internet_access_2024.csv', skiprows=3, encoding='utf-8')
df_kemiskinan_raw = pd.read_csv('data/raw/poverty_rate_2024.csv', skiprows=4, encoding='utf-8')
```

6. Run the notebook:
```bash
jupyter notebook notebooks/digital_divide_statistical_analysis.ipynb
```
Execute the cells sequentially from top to bottom.

## ⚠️ Limitations

- **Interpretation of the regression coefficient:** the slope (`-1.9603`) is only valid within the observed poverty range of `4.00%` to `32.97%`. The intercept (`108.16%`) falls outside a realistic `0%` to `100%` bound and has no standalone interpretation, since it represents an extrapolation to `0%` poverty, a value outside the observed data.
- **Scope:** the analysis covers `37` of Indonesia's `38` provinces for a single year (`2024`) and establishes statistical association, not causation. Confounding factors such as infrastructure investment, geography, and education level are outside the scope of this project.
- **Data:** one province (DKI Jakarta) was dropped during merging due to a missing rural internet access value, and it is a fully urban outlier relative to the rest of the sample, so its exclusion is not necessarily random with respect to the variables studied. The internet indicator also measures self-reported access in the last `3` months, not connection quality or speed.
- **Technical Limitation:** the regression's homoscedasticity and no-autocorrelation assumptions are both violated (`Breusch-Pagan p < 0.001`, `Durbin-Watson = 1.04`), so its confidence intervals should be treated as approximate rather than exact. The notebook also depends on Colab's interactive `files.upload()` step and will not run end-to-end locally without the modification noted in [Getting Started](#-getting-started).
