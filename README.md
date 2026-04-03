# Project Description

Goals: This journal aims to optimize the mechanical properties and environmental/economic benefits of recycled aggregate concrete (RAC) through machine learning models. Based on the listed datasets, the machine learning models identify variables that affect the mechanical properties of RAC, including blast furnace slag, fly ash, age, and water-to-cement ratio. By creating these models, future research can be conducted based on the predicted mixtures that have both sufficient compressive strength and environmental/economic benefits for the regular use of RAC.


Dataset: The models are trained based on the following dataset: Yeh, I. (1998). Concrete Compressive Strength [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5PK67.


Modeling Approach: The models use a train-test split (80-20) to measure the accuracy and reliability of the model. Three models are used: linear regression, gradient boosting, and random forest.

- The following three models are evaluated on a train-test split dataset, where 8/9 of the numeric columns in the dataset are used, which excludes compressive strength:

  - Linear Regression:
    - The parameters of linear regression involve an intercept (A) and a slope (B). A simple linear regression equation is often written as           such: y=Ax+B. The intercept represents the value of the independent variable as the dependent variable approaches 0. The slope represents       the average change of the dependent variable as the independent variable changes. For calculating R^2 and MAE, let's assume y<sub>1             </sub>is the predicted value of the dependent variable while y<sub>2 </sub>is the actual value of the dependent variable. Then, R^2 = 1         ( Σ (y<sub>2</sub> - y<sub>1</sub>)² ) / ( Σ (y<sub>2</sub> - ȳ<sub>2</sub>)² ) and MAE = (1 / n) Σ |y<sub>2</sub> - y<sub>1</sub>|.
    - It is important to note that linear regression is heavily affected by outliers and does not suit datasets that have not already been            linearized. That is to say, linear regression is not suited for non-linear relationships between variables.

  - Gradient Boosting:
    - give parameters, then reference figure in figure folder (ex. As seen in Fig. 1 in the figures folder, the following can be deduced, key         output results of code (r^2, mean error), finally put limitations
  
  - Random Forest:
    - give parameters, then reference figure in figure folder (ex. As seen in Fig. 1 in the figures folder, the following can be deduced, key         output results of code (r^2, mean error), finally put limitations


One of the three models is selected based on the R^2 value. Before this, outliers in the datasets are filtered, and correlations are made between variables in the datasets. Finally, the selected model will use both the correlations and the data to determine a mixture that optimizes a mechanical property in relation to environmental/economic cost. A Pareto-optimal mixture is displayed to indicate the mixture. (rewrite based on model summaries)


How to run models:
(insert steps needed for running and yielding results)
