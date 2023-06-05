# Code Repository for BAM Master's Thesis

The copyright of the Master Thesis rests with the author. The author is responsible for its contents. RSM is only responsible for the educational coaching and cannot be held liable for the content.

The structure of the repository is as follows:

- Baseline_and_DA_R/                 # R code for baseline models and Dominance Analysis in R
- EDA/                               # Code related to exploratory data analysis
- RetrivedData/                      # Code for retrieving all required data for each season and additional dataset
- 2019data.csv                       # Final dataset for 2019 season
- 2020data.csv                       # Final dataset for 2020 season
- 2021data.csv                       # Final dataset for 2021 season
- 2022data.csv                       # Final dataset for 2022 season
- FI_Results.xlsx                    # Excel file with detailed Feature Importance calculations
- mergedData.csv                     # Final dataset for all seasons
- mergedData.ipynb                   # Code for merging data from all seasons
- merf_RF_2models.ipynb              # MERF RandomForest model
- merf-lgb_2models.ipynb             # MERF LightGBM model
- merf-svr_2models.ipynb             # MERF SVR model
- merf-xgboost_2models.ipynb         # MERF XGBoost model
- merf-linear_2models.ipynb          # MERF linear regression model
- robustness.ipynb                   # Robustness check MERF XGBoost model with different outcome variable
- robustness_subset.ipynb            # Robustness check MERF XGBoost model with different outcome variable on a subset


It is important to note that the initial data extraction in the "Retrieve Data" folder was performed locally using cache memory. Due to the large size of the files, the intermediary data was not uploaded to the repository. Therefore, the paths in the code refer to local paths. The code has been provided for the purpose of reproducibility, but the pre-final datasets have been uploaded separately as follows: "2019data.csv," "2020data.csv," "2021data.csv," and "2022data.csv." The final dataset that can be used to run the models is "mergedData.csv".

The final chosen model and the corresponding feature importance analysis can be found under "merf-xgboost_2models.ipynb" file.

