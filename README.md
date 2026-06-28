# Optimizing Recycled Aggregate Concrete
# Project Description

**Goals** -> This study aims to optimize the mechanical properties and environmental/economic benefits of concrete through machine learning models. Based on the listed datasets, the machine learning models identify the importance of variables that affect the mechanical properties of concrete, including, but not limited to, varying levels of ground granulated blast-furnace slag, fly ash, age, and cement. By creating these models, future research can be conducted on predicted/new mixtures that have both sufficient compressive strength and environmental/economic benefits for regular use.


**Dataset** -> The models are trained based on the following datasets:

- Yeh, I. (1998). Concrete Compressive Strength [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5PK67.
  - Includes cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, fine aggregate, and age as features
  - Includes concrete compressive strength as a target value
  - Units are kg/m^3, except for age and concrete compressive strength, which are listed as "day" and "MPa."


**Modeling Approach** -> The notebooks clean up the given dataset and use a train-test split (80-20) to measure the accuracy and reliability of the model. Linear regression serves as a baseline model for editing other machine learning models. A total of three models are analyzed:

- Linear regression, a regression model used for a baseline (linear)
- Random forest, a parallel machine learning model (bagging)
- Gradient boosting, a sequential machine learning model (boosting)

One of the three models is selected based on the R^2 value. Before this, outliers in the datasets are filtered, and correlations are made between variables in the datasets. Finally, the selected model will use both the correlations and the data to determine mixtures that optimize concrete compressive strength. Sustainability proxies are also used to consider environmental and economic trade-offs. A Pareto-optimal mixture is displayed to indicate the mixture.


**Model Explanation** -> Relevant details and explanations of each model will be covered in this section.

(Note that 8/9 of the numeric columns in the dataset are used in the train-test split (excludes compressive strength), and a solid line over a variable, such as ȳ, indicates the average value during the explanation section)

- Linear Regression:
  - Short Explanation
    - The parameters of linear regression involve an intercept (A) and a slope (B). A simple linear regression equation is often written as such: y=Ax+B. The intercept represents the value of the independent variable as the dependent variable approaches 0. The slope represents the average change of the dependent variable as the independent variable changes.
  - Calculating R^2 and MAE
    - Let's assume y<sub>1 </sub>is the predicted value of the dependent variable while y<sub>2 </sub>is the actual value of the dependent variable.
    - Then, R^2 = 1 ( Σ (y<sub>2</sub> - y<sub>1</sub>)² ) / ( Σ (y<sub>2</sub> - ȳ<sub>2</sub>)² ) and MAE = (1 / n) Σ |y<sub>2</sub> - y<sub>1</sub>|.
      - Note that at the top of the sigma notation is n and at the bottom is i=1, where n is the total number of observations and i=1 indicates the first observation.
  - Limitations
    - Linear regression is heavily affected by outliers and does not suit datasets that have not already been linearized. That is to say, linear regression is not suited for non-linear relationships between variables.

- Random Forest:
  - Relevant Variables
    - n_estimators: controls the number of decision trees and improves the model's performance at the cost of computational cost and training time.
    - random_state: ensures reproducibility of the model.
    - n_jobs: determines the number of CPU cores to run the regression model.
    - max_depth: only in the hyperparameter grid in Notebook 2, defines the longest sequential path of an individual decision tree.
    - min_samples_leaf: ensures each tree has a minimum number of samples.
    - All other variables are unchanged and set to default.
  - Variable Significance
    - Increases in n_estimators and n_jobs allow for improved result quality and speed, respectively. Note that n_estimators generally reach a point of diminishing returns at 200 trees.
    - max_depth and min_samples_leaf are used to prevent overfitting, where the model learns the training data to a point where the model is ineffective in analyzing new datasets. Decreasing max_depth and increasing min_samples_leaf help this issue.
  - Calculating R^2 and MAE
    - Let's assume y<sub>1 </sub>is the predicted value of the dependent variable while y<sub>2 </sub>is the actual value of the dependent variable.
    - Then, R^2 = 1 ( Σ (y<sub>2</sub> - y<sub>1</sub>)² ) / ( Σ (y<sub>2</sub> - ȳ<sub>2</sub>)² ) and MAE = (1 / n) Σ |y<sub>2</sub> - y<sub>1</sub>|.
      - Note that at the top of the sigma notation is n and at the bottom is i=1, where n is the total number of observations and i=1 indicates the first observation.
  - Limitations
    - Random forest models are limited by their inability to extrapolate, or the ability to predict values outside the range of the training data.
    - Random forest regression is memory-intensive for larger data sets and may be hard to interpret.
    - Accuracy decreases with an increase in highly correlated variables, creating a bias that dilutes feature importance.
    - Irrelevant values also distort importance scores and hinder each split or node during learning through diluting the feature list random forest models select from.

- Gradient Boosting:
  - Relevant Variables
    - random_state: ensures reproducibility of the model.
    - n_estimators: affects the number of boosting stages (defined as a "tree").
    - max_depth: defines the max number of splits, and consequently the complexity, of each tree.
    - learning_rate: defines the contribution of each tree.
    - All other variables are unchanged and set to default.
  - Variable significance
    - n_estimators minimizes model error by increasing the number of decision trees.
    - max_depth allows for complex data interaction and can be increased if learning_rate is low and n_estimators is too high.
    - learning_rate allows for each decision tree to contribute more, requiring fewer n_estimators as learning_rate increases.
    - Each variable is prone to overfitting, so balancing these 3 is crucial for an accurate model.
  - Calculating R^2 and MAE
    - Let's assume y<sub>1 </sub>is the predicted value of the dependent variable while y<sub>2 </sub>is the actual value of the dependent variable.
    - Then, R^2 = 1 ( Σ (y<sub>2</sub> - y<sub>1</sub>)² ) / ( Σ (y<sub>2</sub> - ȳ<sub>2</sub>)² ) and MAE = (1 / n) Σ |y<sub>2</sub> - y<sub>1</sub>|.
      - Note that at the top of the sigma notation is n and at the bottom is i=1, where n is the total number of observations and i=1 indicates the first observation.
  - Limitations
    - Gradient boosting models are very prone to overfitting and thus affected by very large datasets and noisy data, because they must fix and correct each error.
      - A large number of boosting stages focus the model on outliers.
      - learning_rate and max_depth cause overfitting at high values.
    - Similar to random forest, gradient boosting models cannot extrapolate and are computationally expensive.


**Figure Overview** -> This section will briefly describe the "figures" section of this GitHub (note that gradient boosting was considered the best model, and thus is used in all the figures):

- feature_importance_GradientBoosting_tuned.png
  - Provides a visualization for the given CSV file: "permutation_importance_GradientBoosting_tuned.csv".
  - Defines the importance of each feature in determining concrete compressive strength based on the best model.
- pred_vs_actual_GradientBoosting_tuned.png
  - Provides a graph representing the prediction accuracy of the best model regarding concrete compressive strength.
  - Shows a reasonable level of accuracy for determining feature importance
- tradeoff_strength_vs_co2_proxy.png + tradeoff_strength_vs_cost_proxy.png:
  - These figures provide the estimated CO2 or cost of production based on the predicted concrete compressive strength of concrete using SCMs and different aggregates (supplemental cementitious materials).
  - Notebook 1 displays optimal mixtures for strength trade-offs.


**Results** -> The results of this journal yielded a clear definition of feature importance regarding concrete compressive strength. There also exist mixtures for concrete compressive strength (MPa) while optimizing either cost (USD) and CO₂ (kg/m^3). Future studies can utilize the notebooks and results of this study to guide real-world testing and application in construction.


**How to run models:**

<u>Notebook 1<u>
1. Open eco_concrete_strength_notebook1 and run the setup code to install dependencies (located above step 1).
2. Edit the DATA_DIR location to the desired CSV data in a Google Drive location located in step 1.
    - Refer to comments for clarity within the notebook.
3. Continue running the notebook in sequence and read the comments for clarification.
4. Replace the placeholder values with the desired CO<sub>2 </sub>and cost values based on research in step 8
    - Rename the feature map if using different variables.
    - Refer to comments for units
5. (Optional) Edit the RF (random forest) parameters, then rerun the notebook to optimize the figure and results.

<u>Notebook 2<u>
1. Open eco_concrete_stength_notebook2 and install dependencies.
2. Edit the DATA_DIR and BASE_DIR locations, and set DATA_DIR based on which option is chosen, as listed in step 1.
    - BASE_DIR is set up similarly to DATA_DIR, but will instead receive figures and outputs yielded by Notebook 2 for publication usage.
3. Continue running the notebook in sequence and read the comments for clarification.
4. Replace the placeholder values with the desired CO<sub>2 </sub>and cost values based on research in step 8
    - Rename the feature map if using different variables.
    - Refer to comments for units
5. (Optional) Edit the GBR (gradient boosting regressor) or RF parameters, then rerun the notebook to optimize the figure and results.
