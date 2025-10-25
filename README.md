## 💰 Project Overview
- Sales data ETL and exploratory analysis notebook
- A compact, reproducible demonstration of data sourcing, cleaning, feature engineering, exploratory data analysis, time-series and category-level revenue visualizations applied to a retail sales dataset.

<img width="852" height="547" alt="HeightWeight-ScatterPlot" src="https://github.com/user-attachments/assets/44e60e39-58ec-4564-a783-902b9151cd85" />


### 📋 Purpose
- Provide a clear example of loading a sales CSV, inspecting and cleaning data, engineering business-ready features (profit, margins, age groups), computing descriptive statistics, testing distributional assumptions, performing correlation analysis, and visualizing revenue trends and category/country contributions.


### 📚 Datasets in the Notebook
- - Sales_data CSV (Google Drive): contains columns such as Revenue, Cost, Customer Age, Date, Product Category, Country, and other transactional fields; loaded from a Google Drive path and cleaned through targeted column drops, row removal, and duplicate elimination.


## 🧰 Core techniques demonstrated
- Data loading: pd.read_csv from a local/Drive path.
- Dataset inspection: df.info(), df.describe(), df.head() for schema and summary statistics.
- Missing-value handling: df.drop(...) for columns and df.dropna() for row-level cleaning.
- Duplicate handling: df.duplicated() and df.drop_duplicates().
- Feature engineering: compute Profit_per_Transaction, Profit_Margin, and Age_Group using pd.cut.
- Central tendency: mean, median, and mode for Cost and Revenue.
- Univariate visualization: histograms and boxplots for age, revenue and other numeric columns.
- Correlation analysis: corr() and seaborn heatmap for numerical features.
- Bivariate/multivariate visualization: scatter plots, regression overlays, pairplots.
- Time-series aggregation: convert Date to period, group by Month and plot revenue trends.
- Category and geographic aggregation: groupby Product Category and Country for top contributors.


## ▶️ Usage and Key Cells to Inspect
### 🧪 Part 1 Data load and initial inspection
- Load dataset with pd.read_csv("/content/drive/MyDrive/SigmaData/Sales_data.csv") or update the path.
- Inspect with df.head(5), df.info(), df.describe() to confirm schema, types, and basic statistics.

### 🧾 Part 2 Missing values and duplicates
- Check missing values: df.isnull().sum().
- Drop low-value columns (example: Column1) with df.drop('Column1', axis=1).
- Remove rows with missing values using df.dropna(), then remove duplicates with df.drop_duplicates().

### 📈 Part 3 Feature engineering and central tendencies
- Create Profit_per_Transaction: Revenue - Cost.
- Create Profit_Margin: (Profit_per_Transaction / Revenue) * 100.
- Create Age_Group with pd.cut on Customer Age using defined bins and labels.
- Compute mean, median, mode for Cost and Revenue and print concise summaries.

### 🔍 Part 4 Univariate and bivariate EDA
- Plot Age_Group distribution with sns.histplot and inspect dominant cohorts.
- Visualize Revenue and detect outliers with sns.boxplot.
- Scatterplot Revenue vs Profit_per_Transaction colored by Age_Group to inspect group-level effects.
- Pairplot selected numeric columns to inspect pairwise relationships.

### 🧭 Part 5 Correlation and multivariate inspection
- Build correlation matrix on numeric columns: numerical_df = df_dataset.select_dtypes(include=np.number); corr_matrix = numerical_df.corr().
- Plot heatmap with seaborn to identify strong positive/negative relationships (e.g., Cost vs Revenue).

### 📊 Part 6 Time series and aggregation visuals
- Convert Date to datetime and Month period: df_dataset['Month'] = pd.to_datetime(df_dataset['Date']).dt.to_period('M').
- Aggregate monthly revenue and plot trend line.
- Aggregate revenue by Product Category and by Country and plot top contributors.

### 🗂️ Part 7 Export
- Export cleaned and feature-enriched dataset: df_dataset.to_csv('final_sales_data.csv', index=False).

  
## 📊 Notes and Findings
### 📌 Central tendencies
- Mean, median, and mode for Revenue and Cost show Revenue > Cost on average, indicating overall profitability.

### ⚖️ Variability and outliers
- Boxplots reveal outliers in Revenue spanning high values; these may signal high-margin products or data-entry extremes requiring inspection.

### 🧾 Customer demographics
- Age_Group analysis shows the bulk of customers in the 25–34 and 35–44 cohorts; marketing and targeting should prioritize these segments.

### 🔗 Correlation insights
- Strong positive correlation observed between Cost and Revenue, suggesting higher inventory investment drives higher sales volume and revenue.

### 📈 Temporal and categorical insights
- Monthly revenue trend shows growth over the observed period with seasonal peaks; Bikes category dominates revenue and United States is the top country by revenue.



## 🤝 Contributing
### 🚀 Suggested next steps and improvements
-	Factor notebook logic into testable modules under src/ and add unit tests in tests/.
-	Replace hardcoded file paths with a small config (YAML/JSON) or CLI arguments.
-	Add robust file-loading helpers that present clear errors and suggestions if CSVs are missing or malformed.
-	Replace dropna-based cleansing with targeted imputation strategies where appropriate; log dropped rows for audit.
-	Implement outlier detection (IQR or Z-score) and automated reporting for extreme transactions.
-	Add segmentation analyses (by product, country, age group) with statistical testing for group differences.
-	Add regression modeling (Revenue ~ Cost + Age_Group + Product Category) with diagnostic plots and cross-validation.
- Add Jupyter-friendly cell outputs and inline comments to help readers reproduce steps interactively.

### 🧭 Style and process
- Follow PEP8 for any Python modules and use a pre-commit hook for linting.
- Prefer small, well-documented functions rather than large blocks of procedural code inside the notebook.
- Tests should call functions in src/ instead of running notebook cells.
Thank you for your contributions 🎉

