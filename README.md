# RLCS Multivariate Statistics Analysis

A professional-grade multivariate statistical pipeline built from scratch to analyze Rocket League Championship Series (RLCS) player performances. This project uses advanced statistical methods (Mahalanobis Distance, Hotelling's T² tests, Simultaneous Confidence Intervals) to answer key business questions regarding meta shifts, regional differences, and elite benchmarking in professional Rocket League.

## 🚀 Environment

This project is **primarily designed to be executed in Google Colab**. The raw dataset (~220k+ games) is downloaded dynamically via the Kaggle API to avoid uploading massive files locally. 

## 📁 Project Structure

The following files are included in this submission:

- `RLCS_Multivariate_Analysis.ipynb`: The main Jupyter Notebook containing the full end-to-end data pipeline, statistical tests (built from scratch using matrix algebra), and business interpretations.
- `auxiliary_data/disbanded_teams.csv`: A historical mapping file used to identify the regions of disbanded RLCS teams that are no longer listed on the live Liquipedia portal.
- `auxiliary_data/liquipedia_teams_cache.csv`: A cached response from the Liquipedia `Portal:Teams` API. This ensures the programmatic region-mapping pipeline runs instantly and avoids API rate-limit errors.

## ⚙️ Google Colab Setup Instructions

To run this notebook successfully in Google Colab, please follow these steps:

### 1. Configure Colab Secrets
The notebook requires three environment variables to run. In Google Colab, click the **Secrets** icon (🔑) on the left sidebar and add the following:
- `KAGGLE_USERNAME`: Your Kaggle username.
- `KAGGLE_KEY`: Your Kaggle API key (found in your Kaggle account settings).
- `USER_AGENT_EMAIL`: Your email address (used respectfully as a `User-Agent` header when querying the Liquipedia API).

### 2. Upload Auxiliary Data
Before running the notebook, upload the two auxiliary data files directly into your Colab session storage (the root directory where Colab looks for files):
- `disbanded_teams.csv`
- `liquipedia_teams_cache.csv`

### 3. Execution
Once the secrets are configured and the two CSVs are uploaded, simply select **Runtime > Run all**. The notebook will:
1. Dynamically download the raw dataset from Kaggle.
2. Clean and map all team regions.
3. Execute the full multivariate analysis pipeline.
4. Output all statistical tables and advanced grouped sub-plots.

## 📊 Statistical Methods Implemented
* **Matrix Algebra (Numpy):** Mean vectors, Covariance Matrices, and Correlation structures calculated entirely from scratch.
* **Multivariate Outlier Detection:** Mahalanobis Distance ($\chi^2$ evaluated).
* **One-Sample Hotelling T²:** Comparing the 2025 "Rest of League" against a Top 8 Elite Benchmark.
* **Two-Sample Hotelling T²:** Comparing North American (NA) vs. European (EU) performance profiles with Bonferroni-corrected post-hoc t-tests.
* **Simultaneous Confidence Intervals:** Comparing $T^2$-based margins vs. Bonferroni margins.
* **Paired Hotelling T²:** Season-over-Season meta shift analysis (RLCS 21-22 vs 2025) demonstrating a classic "Multivariate Paradox".
