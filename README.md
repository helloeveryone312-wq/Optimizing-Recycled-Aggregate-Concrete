# Project Description

Goals: This journal aims to optimize the mechanical properties and environmental/economic benefits of recycled aggregate concrete (RAC) through machine learning models. Based on the listed datasets, the machine learning models identify variables that affect the mechanical properties of RAC, including blast furnace slag, fly ash, age, and water-to-cement ratio. By creating these models, future research can be conducted based on the predicted mixtures that have both sufficient compressive strength and environmental/economic benefits for the regular use of RAC.


Dataset: The models are trained based on the following dataset: Yeh, I. (1998). Concrete Compressive Strength [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5PK67.


Modeling Approach: The models use a train-test split (80-20) to measure the accuracy and reliability of the model. Three models are used: linear regression, gradient boosting, and random forest.

- Note that 8/9 of the numeric columns in the dataset are used in the train-test split, which excludes compressive strength, and a solid line over a variable, such as ȳ, indicates average value:

  - Linear Regression:
    - The parameters of linear regression involve an intercept (A) and a slope (B). A simple linear regression equation is often written as such: y=Ax+B. The intercept represents the value of the independent variable as the dependent variable approaches 0. The slope represents the average change of the dependent variable as the independent variable changes.
    - For calculating R^2 and MAE, let's assume y<sub>1 </sub>is the predicted value of the dependent variable while y<sub>2 </sub>is the actual value of the dependent variable. Then, R^2 = 1 ( Σ (y<sub>2</sub> - y<sub>1</sub>)² ) / ( Σ (y<sub>2</sub> - ȳ<sub>2</sub>)² ) and MAE = (1 / n) Σ |y<sub>2</sub> - y<sub>1</sub>|. Note that at the top of the sigma notation is n and at the bottom is i=1, where n is the total number of observations and i=1 indicates the first observation.
    - It is important to note that linear regression is heavily affected by outliers and does not suit datasets that have not already been linearized. That is to say, linear regression is not suited for non-linear relationships between variables.

  - Gradient Boosting:
    - The parameters of gradient boosting involve 3 main parameter groups: The first group consists of the boosting parameters. These include parameters such as the learning rate and n_estimators, which affect the contribution and number of boosting stages (defined as a "tree").
    - The second group of parameters relates specifically to the boosting stages. These parameters include max_depth, the limit to the number of nodes in a single boosting stage; min_samples_split, the minimum number of samples required to split an internal node (higher values prevent overfitting); min_samples_leaf, the minimum number of samples required to be contained within a node; and max_leaf_nodes, limiting the total number of terminal nodes. Nodes are decision points within individual "trees" that predict and correct mistakes.
    - The final group consists of regularization parameters, controlling variance. These parameters include subsample, the fraction of training samples used for fitting each boosting stage, and max_features, the number of features considered in each boosting stage.
    - For calculating R^2 and MAE, let's assume y<sub>1 </sub>is the predicted value of the dependent variable while y<sub>2 </sub>is the actual value of the dependent variable. Then, R^2 = 1 ( Σ (y<sub>2</sub> - y<sub>1</sub>)² ) / ( Σ (y<sub>2</sub> - ȳ<sub>2</sub>)² ) and MAE = (1 / n) Σ |y<sub>2</sub> - y<sub>1</sub>|. Note that at the top of the sigma notation is n and at the bottom is i=1, where n is the total number of observations and i=1 indicates the first observation.
    - The gradient boosting model is limited by being computationally expensive and being prone to overfitting. Gradient boosting is affected by very large datasets and noisy data because it must fix and correct each error it encounters. The model also may heavily focus on outliers through the process of reducing errors, and the large number of boosting stages makes analyzing the model very difficult.
  
  - Random Forest:
    - The parameters controlling the whole model include parameters such as n_estimators, which control the number of decision trees (note that this variable improves the model's performance at the cost of computational cost and training time). Additionally, random_state ensures reproducibility of the model, and n_jobs determines the number of CPU cores to run the regression model.
    - Individual trees are determined by parameters such as max_depth and min_samples_split/leaf, which control overfitting; max_leaf_nodes, controlling the size of each tree; and max_features, which determines the number of features to consider for the best split.
    - For calculating R^2 and MAE, let's assume y<sub>1 </sub>is the predicted value of the dependent variable while y<sub>2 </sub>is the actual value of the dependent variable. Then, R^2 = 1 ( Σ (y<sub>2</sub> - y<sub>1</sub>)² ) / ( Σ (y<sub>2</sub> - ȳ<sub>2</sub>)² ) and MAE = (1 / n) Σ |y<sub>2</sub> - y<sub>1</sub>|. Note that at the top of the sigma notation is n and at the bottom is i=1, where n is the total number of observations and i=1 indicates the first observation.
    - Random forest models are limited by their inability to extrapolate, or the ability to predict values outside the range of the training data. Similar to gradient boosting, random forest regression is memory-intensive for larger data sets and may be hard to interpret. It's also important to note that random forest struggles with datasets that contain a high number of irrelevant features.


One of the three models is selected based on the R^2 value. Before this, outliers in the datasets are filtered, and correlations are made between variables in the datasets. Finally, the selected model will use both the correlations and the data to determine a mixture that optimizes a mechanical property in relation to environmental/economic cost. A Pareto-optimal mixture is displayed to indicate the mixture. (rewrite based on model summaries)


How to run models:

1. Open eco_concrete_strength_notebook1 (Notebook 1) and run the setup code to install dependencies
2. When running step 1, make sure you have a dedicated location in Google Drive that the notebook can detect the CSV data from. This can be set in the DATA_DIR function.
3. Continue running the notebook in sequence and read the comments for clarifications
4. In step 8, replace the placeholder values with the desired CO<sub>2 </sub>and cost values based on research (you can repeat this step for Notebook 1).
5. Open eco_concrete_stength_notebook2 and repeat the same steps. BASE_DIR is set up similarly to DATA_DIR, but will instead receive figures and outputs yielded by Notebook 2.
