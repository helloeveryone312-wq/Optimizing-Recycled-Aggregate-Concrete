# Notebook Descriptions

**Notebook Map Overview** -> The notebooks and their specific functions and purposes in this study will be listed in this section of the README. Additional information on how to run these notebooks is provided in the next section.

01_baseline_strength_model.ipynb is used as an exploratory baseline notebook for exploratory data analysis (EDA). Its initial models analyze feature importance, target distribution, and feature correlation. This notebook also has Pareto exploration, utilizing cost and sustainability proxies estimated from recent literature.

02_cv_tuning_and_outputs.ipynba acts as the final baseline modeling notebook and should be referred to for the final baseline results. Unlike 01_baseline_strength_model.ipynb, this notebook utilizes cross-validation and hyperparameter tuning on the training set (from an 80-20 train-test split) to create the best model. It also saves figures and the CSV outputs for publication usage.

More information about 03_rca_dataset_modeling.ipynb will be written later after it has been fully implemented.
