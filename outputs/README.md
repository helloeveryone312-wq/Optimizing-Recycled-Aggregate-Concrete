**Important Definitions** -> Please read this section for clarification on important terms covered in this README:
- CV: cross-validation
- R²: coefficient of determination
- MAE: mean absolute error in MPa
- Permutation importance: change in model score when one feature is randomly shuffled

Note that permutation importance is model-specific and data-specific and should not be treated as a universal ranking. Also, refer to the outputs from 02_cv_tuning_and_outputs.ipynb as the authoritative source for final model performance.

**Output Descriptions** -> This section covers each output and assigns a short interpretation or description of its significance. Baseline and RCA outputs are separated for the sake of clarity. Additionally, some RCA outputs present in the repo are excluded due to being self-explanatory and to create a more concise list of key outputs that are significant to the study. For example, rca_flagged_rows_for_manual_review.csv is a list of flagged rows from the dataset that are subject to manual review. Thus, additional interpretation is not needed. Furthermore, interpretations of table outputs, such as permutation_importance_RandomForest_tuned_rca.csv, are already analyzed in the README from the "figures" section of the present repo. Thus, those reports are also not included in the output descriptions. Note that this does not mean that all table outputs are automatically excluded.

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

<ins>rca_aggregate_cement_ratio_audit.csv<ins>

The consistency rate between reported and calculated aggregate cement ratios is low (16.3%). This indicates that the sensitivity analysis and other sections of the code should not use calculated aggregate values to avoid reducing the model's predictive performance using the current dataset. Aggregate-cement ratio is therefore retained as a source-provided feature for the sake of feature comparison in Section 6.

Further analysis of the dataset found that a/c is calculated with the volume of aggregates divided by the volume of cementitious materials. The actual volume cannot be accurately confirmed, so the value was tested using the reported aggregate and cement values in the dataset. Thus, the low consistency rate does not indicate flaws within the dataset itself, but rather stems from an imprecise interpretation of the a/c value in the code. The original paper for the a/c definition and the original dataset are listed below for reference:

- Awoyera, P. O., Simwanda, L., Vasić, M. V., Mydin, M. A. O., Imoh, U. U., Fadugba, O. G., Asiz, A., & Rad, M. M. (2026). Hybrid generative-ensemble approach for predicting recycled aggregate concrete strength properties. Scientific reports, 16(1), 15205. https://doi.org/10.1038/s41598-026-42598-6
- Awoyera, P. O. Mechanical Properties of Recycled Aggregate Concrete, Mendeley Data, Version 1, DOI 10.17632/2pxdbh6vx7.1. (2025).

<ins>rca_feature_sets_rca.csv + rca_feature_ablation_group_cv_rca.csv<ins>

Each feature set has a different composition of features to optimize the data that subsequent models are trained on. The compact feature set avoids placing several deterministic versions of the same quantity into one model, while the full engineered set is retained only for an ablation comparison. Section 9 of the notebook runs multiple regression models on different feature sets to compare feature set impact on predictive performance. The results demonstrated that the verified original feature set produced the strongest cross-validation performance with the highest R^2 value. Therefore, it is concluded that adding engineered and redundant variables does not appear to improve the generalization within the present dataset.

<ins>rca_group_tuning_summary_rca.csv + rca_final_model_test_results_rca.csv + rca_tuning_effect_summary_rca.csv<ins>

Model selection was performed in Section 10 of the code using grouped cross-validation on the training data. The R^2 value from this grouped cross-validation is used to select the best-performing regression model (referred to as selection_group_cv_r2). The selected model is then retrained using the training split and run on the held-out test set to then be used for error analysis. Note that whether a model is tuned or not does not determine if it is selected. If an untuned model has a higher grouped cross-validation R^2 value, that model should be selected over the tuned models. The results of the grouped cross-validation are listed in rca_group_tuning_summary_rca.csv, and the primary held-out metrics are listed in rca_final_model_test_results_rca.csv for the selected model.

Section 11 compares the tuned and untuned versions of this selected model and records the results. This is used to quantify the effects of tuning on the selected model, and can be seen in rca_tuning_effect_summary_rca.csv. The tuning effect for the R^2 was a 0.003 increase, possibly indicating that tuning had a limited effect on improving the model's predictive performance.

Please note that the R^2 value reported is not a universal model performance value, but rather the predictive performance on a given held-out split from the RCA dataset for the metrics present in rca_final_model_test_results_rca.csv and rca_tuning_effect_summary_rca.csv.

<ins>error_by_recycled_fraction_rca.csv + error_by_strength_band_rca.csv<ins>

A subgroup error analysis demonstrates the absolute error of the tuned random forest model selected from grouped cross-validation of the training set. The analysis evaluates the held-out test set predictions and records the mean, median, and maximum absolute error, alongside the number of mixtures in a specific subgroup. The test set is first categorized into recycled fraction ranges and then compressive strength bands (quartiles). Higher absolute error values suggest a greater observed error on specific splits, such as on the (0.493, 0.647] recycled aggregate fraction range and Q1 for compressive strength bands, yielding a MAE greater than 7 MPa. However, the small subgroup count prevents broader generalizations of the observed results.

<ins>rca_nested_grouped_oof_predictions_rca.csv<ins>

The selected model configuration from Section 12 of the code is used to generate nested group-aware out-of-fold predictions for every cleaned observation. These predictions are used for the Pareto analysis so that each row is predicted by a model that was not trained on that row's mixture group. The CSV lists the metrics after five nested OOF folds are conducted.

<ins>rca_sustainability_factor_scenarios_used_rca.csv<ins>

A list of observed emissions values, categorized into low, central, and high scenarios, is assigned to their respective features in the verified original feature set. Since the values are pulled from multiple sources across features, with different system boundaries, locations, and studies, the following Pareto analysis section should be considered an emissions proxy, not a complete LCA. Unlike the previous notebooks, cost analysis is not included in the present notebook. All values are in kg CO₂e/kg material. Multiplication by mixture quantities in kg/m³ produces kg CO₂e/m³

<ins>predicted_stable_pareto_candidates_rca.csv + measured_stable_pareto_candidates_rca.csv<ins>

Despite having accompanying figures, similar to permutation_importance_RandomForest_tuned_rca.csv, an important limitation must be mentioned regarding mixture quantities. Each mixture contains an unusually high combined aggregate mass per cubic metre for conventional normal-weight concrete. An exact specification for how to interpret the four aggregate types is not present in the paper methodology section from which the dataset is used (https://doi.org/10.1038/s41598-026-42598-6). Thus, the reported aggregate contents for mixtures are retained without assuming they are erroneous, as the value is still physically plausible; however, this should be listed as a limitation to maintain research transparency.

<ins>____<ins>
