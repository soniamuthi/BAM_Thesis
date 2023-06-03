# Code Repository for BAM Master's Thesis

The copyright of the Master Thesis rests with the author. The author is responsible for its contents. RSM is only responsible for the educational coaching and cannot be held liable for the content.

The structure of the repository is as follows:
.
├── Baseline_and_DA_R     # R code for baseline models and Dominance Analysis in R
├── EDA     # Code related to exploratory data analysis                     
├── RetrivedData      # Code for retriving all required data for each season and additional datasets
├── 2019data.csv      # Final dataset for 2019 season
├── 2020data.csv      # Final dataset for 2020 season
├── 2021data.csv      # Final dataset for 2021 season
├── 2022data.csv      # Final dataset for 2022 season
├── FI_Results.xlsx     # Excel file with detailed Feature Importance calculations
├── mergedData.csv      # Final dataset for all seasons              
├── mergedData.ipynb    # Code for merging data from all seasons
├── merf_RF_2models.ipynb     # MERF RandomForest model
├── merf-lgb_2models.ipynb      # MERF
├── merf-svr_2models.ipynb
├── merf-xgboost_2models.ipynb
├── merf-linear_2models.ipynb
├── robustness.ipynb
└── robustness_subset.ipynb

It is important to note that the initial data extraction in the "Retrieve Data" folder was performed locally using cache memory. Due to the large size of the files, the intermediary data was not uploaded to the repository. Therefore, the paths in the code refer to local paths. The code has been provided for the purpose of reproducibility, but the final datasets have been uploaded separately as follows: "2019data.csv," "2020data.csv," "2021data.csv," and "2022data.csv."
