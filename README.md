# Machine Learning Prediction of Concrete Compressive Strength Using Supplementary Cementitious Material Features
# Project Description

**Goals** -> This study aims to optimize the mechanical properties and environmental/economic benefits of concrete through machine learning models. Based on the listed datasets, the machine learning models identify the importance of variables that affect the mechanical properties of concrete, including, but not limited to, varying levels of ground granulated blast-furnace slag, fly ash, age, and cement. By creating these models, future research can be conducted on predicted/new mixtures that have both sufficient compressive strength and environmental/economic benefits for regular use.


**Current Project Stage** -> This section will explain the current and future stages of the study to provide insight into how it will develop.

- Current stage: finishing RCA Notebook 3 and updating relevant information in GitHub.
- Next stage: identify and integrate RCA-specific figures and outputs.
- Final stage: finish paper for JHSS submission.


**Dataset** -> The models are trained based on the following datasets:

- Yeh, I. (1998). Concrete Compressive Strength [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5PK67.
  - Includes cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, fine aggregate, and age as input features.
  - Includes concrete compressive strength as a target value.
  - Units are kg/m^3, except for age and concrete compressive strength, which are listed as "day" and "MPa."

- Awoyera, Paul (2025), “Mechanical Properties of Recycled Aggregate Concrete”, Mendeley Data, V1, doi: 10.17632/2pxdbh6vx7.1.
  - Includes water-cement ratio, aggregate-cement ratio, water, cement, natural fine aggregate, natural coarse aggregate, recycled coarse aggregate, and recycled fine aggregate as input features.
  - Includes compressive strength, split tensile strength, flexural strength, and modulus of elasticity as target values.
  - Units are dimensionless for w/c and a/c, kg/m^3 for all other input features, and MPA for all target values.


**Modeling Approach** -> The notebooks clean up the given dataset and use a train-test split and cross-validation to measure the accuracy and reliability of the model. Linear regression is used as a baseline model for comparison against more flexible tree-based methods. More information exists within the notebook comments. A total of three models are analyzed:

- Linear regression, a linear regression model used for a baseline.
- Random forest, an ensemble bagging model that averages many decision trees.
- Gradient boosting, an ensemble boosting model that builds trees sequentially to correct previous errors.

One of the three models is selected based on the R^2 value. Before this, outliers in the datasets are filtered, and correlations are computed between variables. Finally, the selected model will use both the correlations and the data to determine mixtures that optimize concrete compressive strength. Sustainability proxies are also used to consider environmental and economic trade-offs. A Pareto-optimal mixture is displayed to indicate the mixture.

It's important to note that gradient boosting and random forest models are limited by their inability to extrapolate, and linear regression has trouble fitting the multivariable, non-linear data used in this study. Depending on the model's configurations, they can prove to be computationally expensive as well. More information can be found in docs/model_explanations.md in the present README. Additionally, 01_baseline_strength_model.ipynb contains untuned gradient boosting and random forest models, while 02_cv_tuning_and_outputs.ipynb conducts hyperparameter tuning for the final figures and outputs.


**Figure Overview** -> Due to the number of figures across all three code notebooks, a more detailed summary is included in the "figures" folder of this repository.

**Results** -> The results of this project showed a clear definition of feature importance regarding concrete compressive strength. There also exist mixtures for concrete compressive strength (MPa) while optimizing either cost (USD/kg) or CO₂ (kg CO₂e/kg).

01_baseline_strength_model.ipynb Exploratory Baseline Results: Gradient boosting was selected for downstream interpretation because it achieved the highest held-out test R² and the lowest test MAE, as seen below.

- Linear Regression: R² = 0.618, MAE = 9.030 MPa
- Random Forest tuned: R² = 0.863, MAE = 4.890 MPa
- Gradient Boosting tuned: R² = 0.872, MAE = 4.862 MPa

02_cv_tuning_and_outputs.ipynb Tuned Final Baseline Results: Gradient Boosting was selected for downstream interpretation because it achieved the highest held-out test R² and the lowest test MAE, as seen below.

- Linear Regression: R² = 0.579, MAE = 9.03 MPa
- Random Forest tuned: R² = 0.831, MAE = 5.027 MPa
- Gradient Boosting tuned: R² = 0.887, MAE = 4.484 MPa

02_cv_tuning_and_outputs.ipynb Pareto Exploration Results: See the "figures" folder and notebook for tabled results.

03_rca_dataset_modeling_and_pareto_analysis.ipynb Tuned Final RCA Results: Random forest was selected for downstream interpretation because it achieved the highest grouped cross-validation R², as seen below.

- Linear Regression: Group CV R² = 0.462
- Random Forest tuned: Group CV R² = 0.696, Test Set R² = 0.887, MAE = 3.518 MPa, RMSE = 4.597 MPa
- Gradient Boosting tuned: Group CV R² = 0.673

03_rca_dataset_modeling_and_pareto_analysis.ipynb Pareto Exploration Results: See the "figures" folder and notebook for tabled results.

Additionally, it is important to note that the gradient boosting model held a stronger mean cross-validation R² throughout the first and second notebooks, but random forest performed stronger in the third notebook. However, when testing the different regression models on multiple repeated grouped splits, 03_rca_dataset_modeling_and_pareto_analysis.ipynb favored neither random forest nor gradient boosting consistently. Regardless, the gradient boosting model was used for figures in 01_baseline_strength_model.ipynb and 02_cv_tuning_and_outputs.ipynb, and a random forest model was used for figures in 03_rca_dataset_modeling_and_pareto_analysis.ipynb.

Future studies can utilize the notebooks and results of this study to guide real-world testing and application in construction.
 

**Notebook Map** -> The notebooks and their specific function/purpose in this study will be listed in this section of the README. Additional information on how to run these notebooks is provided in the next section.

<u>01_baseline_strength_model.ipynb<u>
- Acts as an exploratory, baseline notebook with exploratory data analysis (EDA).
- Contains initial untuned models, residuals, and tradeoff plots.
- Includes cross-validation with training and test data

<u>02_cv_tuning_and_outputs.ipynb<u>
- Acts as the final baseline modeling notebook.
- Uses grouped cross-validation and hyperparameter tuning to train the best model.
  - This only occurs in the training set, not the test set (80-20 train-test split).
- Saves tuned figures and CSV outputs for publication usage; refer to this notebook for the final baseline results.
- Includes sustainability proxy analysis and Pareto exploration with a list of Pareto-optimal mixtures

<u>03_rca_dataset_modeling.ipynb<u>
- Acts as the primary RCA analysis notebook.
- Uses grouped cross-validation and hyperparameter tuning to train the best model.
  - This only occurs in the training set, not the test set (80-20 train-test split).
  - Repeated grouped splits are run to ensure model consistency across multiple test sets.
- Saves tuned figures and CSV outputs for publication usage; refer to this notebook for the final RCA results.
- Includes sustainability proxy analysis and Pareto exploration with a list of Pareto-optimal mixtures


**How to run models:**

<u>01_baseline_strength_model.ipynb<u>
1. Open 01_baseline_strength_model.ipynb and run the setup code to install dependencies.
2. Set RUN_MODE to either repo or drive, depending on the dataset location in step 1. If RUN_MODE = repo, upload necessary data files in the "data" folder.
    - Refer to comments for clarity within the notebook.
3. Continue running the notebook in sequence and read the comments for clarification.
4. (Optional) Edit the RF (random forest) parameters, then rerun the notebook to optimize the figure and results.

<u>02_cv_tuning_and_outputs.ipynb<u>
1. Open 02_cv_tuning_and_outputs.ipynb and install dependencies.
2. Set RUN_MODE to either repo or drive, depending on the dataset location in step 1. If RUN_MODE = repo, upload necessary data files in the "data" folder.
3. Continue running the notebook in sequence and read the comments for clarification.
4. Replace working_factors with updated literature results for CO<sub>2 </sub>and cost values based on current relevance in step 10
    - Rename the feature map if using different variables.
    - Refer to comments for units
5. (Optional) Edit the GBR (gradient boosting regressor) or RF parameters, then rerun the notebook to optimize the figure and results.

<u>03_rca_dataset_modeling_and_pareto_analysis.ipynb<u>
1. Open 03_rca_dataset_modeling_and_pareto_analysis.ipynb and install dependencies.
2. Set RUN_MODE to either repo or drive, depending on the dataset location in step 1. If RUN_MODE = repo, upload necessary data files in the "data" folder.
3. Continue running the notebook in sequence and read the comments for clarification. Upload dataset corrections if necessary.
4. Upload sustainability_factor_scenarios.csv to run sustainability proxy analysis.
5. (Optional) Edit the GBR (gradient boosting regressor) or RF parameters, then rerun the notebook to optimize the figure and results. N_REPEATED_GROUP_SPLITS may also be increased or decreased based on the runtime limit.

**Author Note:** The next phase of this study will be finalizing RCA figures and outputs in the repository before moving on to writing.
