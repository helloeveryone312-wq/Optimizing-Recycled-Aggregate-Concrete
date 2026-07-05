**Data Transparency** -> The data is from UC Irvine's Machine Learning Repository. The download links are as follows:
- https://archive.ics.uci.edu/dataset/165/concrete+compressive+strength (directly from the archive)
- https://www.kaggle.com/datasets/elikplim/concrete-compressive-strength-data-set/data (Kaggle download by Ahiale Darlington, stored in REPO)

**Dataset Description** -> This section will describe all the details regarding the dataset used.
1. CSV name: concrete_data
2. Where is the CSV from: UC Irvine Machine Learning Repository ("Concrete Compressive Strength")
3. DOI: https://doi.org/10.24432/C5PK67
4. Included in REPO: Yes
5. Number of rows: 1030
6. Number of input features: 8
7. Target: concrete compressive strength in MPa
8. Units: kg/m³ for mixture ingredients, days for age, MPa for strength
9. What the CSV contains: cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, fine aggregate, age, concrete compressive strength. Note that "blast furnace slag" refers to ground granulated blast furnace slag (GGBFS), and both aggregates are natural aggregates, not recycled.
10. Where is this used and how: the CSV is used in both 01_baseline_strength_model.ipynb and 02_cv_tuning_and_outputs.ipynb. The data is used to train baseline models and is utilized in all outputs/figures except the Pareto exploration (though a model trained on the data is used in this case).
11. Notebook outputs of the CSV: the current outputs consist of ranking the permutation importance of each feature using a Gradient Boosting model, test set results from a train-test split ranking the performance of 3 models based on R^2 and MAE, and a summary ranking the models on their R^2 value based on a 5-fold cross-validation on the training set.
12. Limitation: CSV does not contain any direct RCA feature or information for cost/CO₂ proxies.
