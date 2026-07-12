**Important Definitions** -> Please read this section for clarification on important terms covered in this readme:
- CV: cross-validation
- R²: coefficient of determination
- MAE: mean absolute error in MPa
- Permutation importance: change in model score when one feature is randomly shuffled

Note that permutation importance is model-specific and data-specific and should not be treated as a universal ranking.

**Output Descriptions** -> This section covers each output and a short description of what each contains.

<ins>cv_summary.csv<ins>

This compares the three models' provided R^2 values and the MAE, showing the mean and standard deviation (std) of each based on a 5-fold cross-validation on the training set data. Using this summary, the higher-performing model among the three can be determined.

<ins>test_set_results.csv<ins>

This presents the results of the three models using the test set, which was held out from training and used only for final model evaluation. The CSV provides an R^2 value on the test set and compares it to the training set results, yielding an MAE for each model. Notably, this ranking was used over the one in cv_summary.csv to determine the most accurate model, as the values in this CSV were tested on untouched data.

<ins>permutation_importance_GradientBoosting_tuned.csv<ins>

This represents the permutation importance of each feature considered in evaluating concrete compressive strength, based on the selected model (in this case, GradientBoosting). These features are stored in a table with their respective means and standard deviations.

<ins>pareto_candidates_baseline.csv<ins>

This contains 24 different Pareto optimal mixtures based on the tradeoff proxy analysis processed by a Gradient Boosting model in 01_baseline_strength_model. The current results contain values that are not realistic, as seen in column "co2_proxy_kg." Thus, this figure will be updated once CO2 and cost factors are accurate in the notebooks.
