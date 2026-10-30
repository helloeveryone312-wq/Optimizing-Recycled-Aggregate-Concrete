**Important Definitions** -> Please read this section for clarification on important terms covered in this readme:
- CV: cross-validation
- R²: coefficient of determination
- MAE: mean absolute error in MPa
- Permutation importance: change in model score when one feature is randomly shuffled

Note that permutation importance is model-specific and data-specific and should not be treated as a universal ranking. Also, refer to the outputs from 02_cv_tuning_and_outputs.ipynb as the authoritative source for final model performance.

**Output Descriptions** -> This section covers each output and a short description of what each contains. Baseline and RCA outputs are separated for the sake of clarity.

*Baseline:*

<ins>baseline_model_comparison_cv_baseline.csv<ins>

This compares the three models' provided R^2 values and the MAE, showing the mean and standard deviation (std) of each based on a 5-fold cross-validation on the training set data. Using this summary, the higher-performing, more accurate model among the three can be determined. This CSV is created in either 01_baseline_strength_model.ipynb or 02_cv_tuning_and_outputs.ipynb, yielding the same result.

<ins>baseline_model_test_results_baseline.csv + test_set_results_baseline.csv<ins>

These CSVs present the results of the three models on the test set, as shown in their respective notebooks; the test set was held out from training and used only for final model evaluation. The CSV provides an R^2 value on the test set and compares it to the training set results, yielding an MAE for each model. Each model is evaluated using cross-validation, as specified in the code comments in the notebooks. Notably, this comes from the models that ran through hyperparameter tuning in 02_cv_tuning_and_outputs.ipynb, but have lower R^2 values than the models in 01_baseline_strength_model.ipynb when run on the test set. This indicates that the hyperparameter tuning may have decreased the model accuracy. However, the evaluation process between notebooks differs; thus, 02_cv_tuning_and_outputs.ipynb should still be considered the authoritative source for final model performance.

<ins>permutation_importance_GradientBoosting_baseline.csv + permutation_importance_GradientBoosting_tuned_baseline.csv<ins>

This represents the permutation importance of each feature considered in evaluating concrete compressive strength, based on the selected model (in this case, gradient boosting). In other words, a higher value indicates an important feature to the selected model when making predictions about concrete compressive strength. These features are stored in a table with their respective means and standard deviations. The tuned CSV comes from 02_cv_tuning_and_outputs.ipynb, where the model is run through hyperparameter tuning before determining permutation importance.

<ins>pareto_candidates_baseline.csv<ins>

This contains 26 different Pareto-optimal mixtures based on the tradeoff proxy analysis processed by a Gradient Boosting model in 02_cv_tuning_and_outputs.ipynb. For better visualization, refer to the Pareto candidates figures in the present repo.

<ins>sustainability_results_baseline.csv<ins>

The CSV contains the original UCI dataset and adds two additional columns, being "co2_proxy_kg_per_m3" and "cost_proxy_usd_per_m3." These values are used to make the figures for proxy analysis and determine Pareto-optimal mixtures. For better visualization, refer to the tradeoff proxy figures in the present repo.

*RCA:*


