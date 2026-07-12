# Machine Learning Prediction of Concrete Compressive Strength Using Supplementary Cementitious Material Features
# Project Description

**Goals** -> This study aims to optimize the mechanical properties and environmental/economic benefits of concrete through machine learning models. Based on the listed datasets, the machine learning models identify the importance of variables that affect the mechanical properties of concrete, including, but not limited to, varying levels of ground granulated blast-furnace slag, fly ash, age, and cement. By creating these models, future research can be conducted on predicted/new mixtures that have both sufficient compressive strength and environmental/economic benefits for regular use.


**Current Project Stage** -> This section will explain the current and future stages of the study to provide insight into how it will develop.

- Current stage: baseline model stabilized on UCI concrete compressive strength data.
- Next stage: identify and integrate RCA-specific dataset.
- Final stage: update model, GitHub, figures, and paper for JHSS submission.


**Dataset** -> The models are trained based on the following datasets:

- Yeh, I. (1998). Concrete Compressive Strength [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5PK67.
  - Includes cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, fine aggregate, and age as features
  - Includes concrete compressive strength as a target value
  - Units are kg/m^3, except for age and concrete compressive strength, which are listed as "day" and "MPa."

The current UCI data **DOES NOT** include RCA replacement percentage, recycled aggregate source, parent concrete strength, RCA water absorption, RCA density, or plastic fiber content. This will be integrated later with an RCA-specific dataset.


**Modeling Approach** -> The notebooks clean up the given dataset and use a train-test split (80-20) to measure the accuracy and reliability of the model. Linear regression is used as a baseline model for comparison against more flexible tree-based methods. A total of three models are analyzed:

- Linear regression, a linear regression model used for a baseline.
- Random forest, an ensemble bagging model that averages many decision trees.
- Gradient boosting, an ensemble boosting model that builds trees sequentially to correct previous errors.

One of the three models is selected based on the R^2 value. Before this, outliers in the datasets are filtered, and correlations are made between variables in the datasets. Finally, the selected model will use both the correlations and the data to determine mixtures that optimize concrete compressive strength. Sustainability proxies are also used to consider environmental and economic trade-offs. A Pareto-optimal mixture is displayed to indicate the mixture.

It's important to note that gradient boosting and random forest are limited by their inability to extrapolate, and linear regression has trouble fitting multivariable non-linear data that is used in this study. Depending on the model's configurations, they can prove to be computationally expensive as well. More information can be found in docs/model_explanations.md in the present README.


**Figure Overview** -> This section will briefly describe the "figures" section of this GitHub (note that gradient boosting was considered the best model, and thus is used in all the figures):

- feature_importance_GradientBoosting_tuned.png
  - Provides a visualization for the given CSV file: "permutation_importance_GradientBoosting_tuned.csv".
  - Defines the importance of each feature in determining concrete compressive strength based on the best model.
- pred_vs_actual_GradientBoosting_tuned.png
  - Provides a graph representing the prediction accuracy of the best model regarding concrete compressive strength.
  - Shows a reasonable level of accuracy for determining feature importance
- tradeoff_strength_vs_co2_proxy.png + tradeoff_strength_vs_cost_proxy.png:
  - These figures provide the estimated CO₂ in kg CO₂e per kg of material or cost in USD per kg of material based on the predicted concrete compressive strength of concrete using SCMs and different aggregates (supplemental cementitious materials).
  - Labeled as a proxy analysis due to improper current values.


**Results** -> The results of this project showed a clear definition of feature importance regarding concrete compressive strength. There also exist mixtures for concrete compressive strength (MPa) while optimizing either cost (USD) or CO₂ (kg/m^3).

Notebook 2 Results: Gradient Boosting was selected for downstream interpretation because it achieved the highest held-out test R² and the lowest test MAE, as seen below:

- Linear Regression: R² = 0.628, MAE = 7.75 MPa
- Random Forest tuned: R² = 0.881, MAE = 3.79 MPa
- Gradient Boosting tuned: R² = 0.920, MAE = 3.12 MPa

Additionally, it is important to note that the Random Forest model held a slightly stronger mean cross-validation R² compared to Gradient Boosting in cv_summary.csv. However, Gradient Boosting performed best on the held-out test set and was therefore selected over Random Forest.

Future studies can utilize the notebooks and results of this study to guide real-world testing and application in construction.
 

**Notebook Map** -> The notebooks and their specific function/purpose in this study will be listed in this section of the README. Additional information on how to run these notebooks is provided in the next section.

<u>01_baseline_strength_model.ipynb<u>
- Acts as an exploratory, baseline notebook with exploratory data analysis (EDA).
- Contains initial models, residuals, tradeoff plots, and Pareto exploration.

<u>02_cv_tuning_and_outputs.ipynb<u>
- Acts as the final baseline modeling notebook.
- Uses cross-validation and hyperparameter tuning to create the best model.
  - This only occurs in the training set, not the test set (80-20 train-test split).
- Saves figures and CSV outputs for publication usage; refer to this notebook for the final baseline results.

<u>03_rca_dataset_modeling.ipynb<u>
- Future notebook planned to be added for recycled aggregate dataset modeling.


**How to run models:**

<u>01_baseline_strength_model.ipynb<u>
1. Open eco_concrete_strength_notebook1 and run the setup code to install dependencies (located above step 1).
2. Edit the DATA_DIR location to the desired CSV data in a Google Drive location located in step 1.
    - Refer to comments for clarity within the notebook.
3. Continue running the notebook in sequence and read the comments for clarification.
4. Replace the placeholder values with the desired CO<sub>2 </sub>and cost values based on research in step 8
    - Rename the feature map if using different variables.
    - Refer to comments for units
5. (Optional) Edit the RF (random forest) parameters, then rerun the notebook to optimize the figure and results.

<u>02_cv_tuning_and_outputs.ipynb<u>
1. Open eco_concrete_strength_notebook2 and install dependencies.
2. Edit the DATA_DIR and BASE_DIR locations, and set DATA_DIR based on which option is chosen, as listed in step 1.
    - BASE_DIR is set up similarly to DATA_DIR, but will instead receive figures and outputs yielded by Notebook 2 for publication usage.
3. Continue running the notebook in sequence and read the comments for clarification.
4. Replace the placeholder values with the desired CO<sub>2 </sub>and cost values based on research in step 8
    - Rename the feature map if using different variables.
    - Refer to comments for units
5. (Optional) Edit the GBR (gradient boosting regressor) or RF parameters, then rerun the notebook to optimize the figure and results.

<u>03_rca_dataset_modeling.ipynb<u>
(planned for RA dataset modeling)


**Author Note:** The next phase of this study will replace or supplement the current baseline dataset with an RCA-specific dataset so the model can directly evaluate recycled aggregate replacement effects.
