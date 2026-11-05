**Figure Overview** -> This section will briefly describe the "figures" section of this GitHub (note that gradient boosting was considered the best and selected model, and thus is used in all the figures):

<ins>Baseline Figures:<ins>
- target_distribution_baseline.png
  - Represents the distribution of concrete compressive strength between each row in the dataset.
  - Shows a right-skewed distribution of the data, indicating a larger amount of data between 0-40 MPa.
- correlation_heatmap_baseline.png
  - Demonstrates the exploratory relationships between target and feature columns in the dataset.
  - Shows a positive correlation between cement, age, and superplasticizer, and a weaker or negative correlation with water, fly ash, and aggregates with concrete compressive strength.
- pred_vs_actual_GradientBoosting_baseline.png + pred_vs_actual_GradientBoosting_tuned_baseline.png
  - Provides a graph representing the prediction accuracy of the best model regarding concrete compressive strength.
  - Shows a reasonable level of accuracy for determining feature importance, determined by test set results.
  - The tuned scatterplot graph had the selected model go through hyperparameter tuning before creating the figure.
- residual_plot_GradientBoosting_baseline.png + residual_plot_GradientBoosting_tuned_baseline.png
  - This plot shows the residuals at different levels of concrete compressive strength based on the predictions of the gradient boosting model.
  - Demonstrates the model is accurate with an uncertainty of ±5 MPa for most predictions.
  - The tuned scatterplot graph had the selected model go through hyperparameter tuning before creating the figure.
- feature_importance_GradientBoosting_baseline.png + feature_importance_GradientBoosting_tuned_baseline.png
  - Defines the importance assigned by the selected model to each feature in predicting concrete compressive strength.
  - The tuned feature importance graph had the selected model go through hyperparameter tuning before creating the figure.
- tradeoff_strength_vs_co2_proxy_baseline.png + tradeoff_strength_vs_cost_proxy_baseline.png:
  - These figures provide the estimated CO₂ in kg CO₂e per m^3 of material or cost in USD per m^3 of material based on the predicted concrete compressive strength of concrete using SCMs (supplemental cementitious materials) and different aggregates.
  - Units are presented in predicted compressive strength in MPa on the y-axis.
  - Labeled as a proxy analysis due to inconsistent, varying values across features and industries.
- pareto_candidates_baseline.png + pareto_candidates_cost_baseline.png
  - Provides a highlighted graph with optimal mixtures to minimize CO₂ and cost while maximizing the concrete compressive strength, respectively.
  - The graphical results stem from a proxy analysis and should not be considered fully accurate.
  - Units are presented in CO₂ in kg CO₂e per m^3 of material or cost in USD per m^3 on the x-axis.
  - Units are presented in predicted compressive strength in MPa on the y-axis.
 
<ins>RCA Figures<ins>
- target_distribution_rca.png
  - Shows the distribution of mixture compressive strength in the RCA dataset.
  - Indicates heavy clustering between 30-50 MPa.
- recycled_aggregate_fraction_distribution_rca.png
  - Shows the distribution of recycled aggregate fraction in the RCA dataset.
  - Demonstrates a greater number of mixtures with a recycled aggregate fraction of 0.2 or 0.4-0.5, with fewer mixtures present at a higher recycled aggregate content.
- strength_vs_recycled_fraction_rca.png
  - Shows the concrete compressive strength as a function of the proportion of recycled aggregate to natural aggregate present within a mixture using a scatterplot.
  - High frequency of mixtures between 30-50 MPa and 0.4-0.5 recycled aggregate fraction.
  - Low frequency of mixtures in 60-80 MPa and 0-0.4 recycled aggregate fraction.
- correlation_heatmap_rca.png
  - Demonstrates the exploratory relationships between target and feature columns in the dataset.
  - Indicates a positive correlation between cement and compressive strength, but a negative correlation between compressive strength and water-cement ratio.
- pred_vs_actual_RandomForest_tuned_rca.png
  - Plots the predicted value of compressive strength by the primary hold-out model against the actual compressive strength of the mixture using a scatterplot.
  - Shows moderately accurate predictions regarding medium-strength mixtures, with larger errors at higher and lower strength mixtures.
- residual_plot_RandomForest_tuned_rca.png
  - Represents calculated residual values based on the predicted vs. actual compressive strength values of a given mixture.
  - Similar to pred_vs_actual_RandomForest_tuned_rca.png, though more detailed conclusions cannot be reached without a larger test set.
- feature_importance_RandomForest_tuned_rca.png
  - Defines the importance assigned by the selected model to each feature in predicting concrete compressive strength.
  - Based on the primary hold-out model and reports water-cement ratio and water content to be the strongest predictive variables within the fitted model.
- repeated_group_validation_r2_rca.png
  - Shows a boxplot of the R^2 values across 30 repeated splits.
  - Reports a 5-number summary of 0.624, 0.740, 0.806, 0.855, 0.928.
- repeated_group_validation_mae_rca.png
  - Shows a boxplot of the MAE values across 30 repeated splits.
  - Reports a 5-number summary of 2.325, 3.872, 4.093, 4.758, 7.259.
- measured_vs_predicted_stable_pareto_frontiers_rca.png
  - Shows cleaned observed mixtures and highlights Pareto candidates across two frontiers: measured and out-of-fold predicted compressive strength.
  - Indicates a difference between model-based candidate selection and using measured strength of the mixture.
  - Demonstrates a limited overlap between stable candidate sets.
- stable_pareto_residual_plot_rca.png
  - Shows overlapping candidates from both measured and out-of-fold frontiers.
  - Demonstrates that model-based Pareto candidate identification should be treated as exploratory due to limited overlap.


 **Figure Analysis** -> This section will go more in depth about the contents of figures in the present repo. Specifically, any relationships, outliers, and behaviors the figure may contain are discussed in the context of the notebook. The figures will be split between baseline and RCA-related figures. Please refer to the tuned figures in 02_cv_tuning_and_outputs.ipynb and the validation results in 03_rca_dataset_modeling_and_pareto_analysis.ipynb as the authoritative source for final model performance.

*Baseline:*

<ins>target_distribution_baseline.png<ins>

The baseline target distribution graph shows a few peaks around 20-40 MPa, but generally follows a right-skewed distribution. As a result, concrete compressive strength ranges between 10 and 40 MPa are densely represented, while compressive strength values outside of those ranges should be more cautiously interpreted in Stage 1 due to sparse representation.

<ins>correlation_heatmap_baseline.png<ins>

The purpose of this graph is to analyze the exploratory relationships between variables in the UCI dataset. The heatmap demonstrates that age, cement, and superplasticizer have a positive correlation with concrete compressive strength, showing they're useful when making concrete compressive strength predictions. Other features seem to have a lesser or negative correlation, indicating that these features are less useful in making strength predictions. However, it only provides exploratory context for the present data and should not be interpreted as causal evidence or as a replacement for model-based feature importance.

<ins>pred_vs_actual_GradientBoosting_baseline.png + pred_vs_actual_GradientBoosting_tuned_baseline.png<ins>

The figures exhibit moderate clustering around the plotted line, indicating an acceptable predictive performance for gradient boosting on the baseline dataset. Specifically, this conclusion should only apply up to a concrete compressive strength of 40 MPa, as the graph demonstrates a noticeably higher predictive error with fewer data points at higher compressive strengths.

<ins>residual_plot_GradientBoosting_baseline.png + residual_plot_GradientBoosting_tuned_baseline.png<ins>

Model accuracy is shown to be accurate, with a moderate amount of predictive variance and a tighter residual spread up to a compressive strength of 40 MPa. The model seems to underpredict at a lesser magnitude more frequently; however, it also overpredicts more often at a higher magnitude. A different spread of data may change the current results, but the residuals lie in an acceptable range for the model's overall accuracy.

<ins>feature_importance_GradientBoosting_baseline.png + feature_importance_GradientBoosting_tuned_baseline.png<ins>

The model depends on age, cement, and blast furnace slag when predicting concrete compressive strength. This does not indicate direct physical causation, just the model's dependence when making predictions. However, even though this graph matches real-world observations to an extent, it's also important to note that low-importance variables, such as fly ash, do not reflect their significance in practical applications. Additionally, correlated variables can distort the permutation importance values.

<ins>tradeoff_strength_vs_co2_proxy.png + tradeoff_strength_vs_cost_proxy.png<ins>

Both figures are considered a proxy analysis due to the inconsistent values of cost and CO₂. The study attempts to find relevant values close to the present day, but a mismatch will almost always persist. Although a positive relationship exists between increasing cost/CO₂ and increasing concrete compressive strength, it is clear that a non-linear relationship exists between cost/CO₂ and predicted strength. This indicates that there are many different mixtures to optimize either factor based on the chosen features.

<ins>pareto_candidates_baseline.png + pareto_candidates_cost_baseline.png<ins>

The baseline Pareto analysis demonstrates that there is an observed tradeoff between an increase in a mixture’s CO₂ emissions and its compressive strength. It demonstrates this by highlighting the Pareto candidates with the highest levels of CO₂ also subsequently having the highest level of compressive strength. The Pareto candidates for the cost proxy do not show a similar relationship, with similar compressive strength mixtures existing at different magnitudes of material costs. Although an upward trend between compressive strength and cost exists to some extent, lower-cost mixture alternatives exist around concrete compressive strengths of 40-55 MPa.

*RCA:*

<ins>target_distribution_rca.png<ins>

The target distribution graph shows a heavy amount of clustering between 30-50 MPa. This communicates that model predictions within these compressive strength ranges should be interpreted more carefully. Adding a higher number of mixtures in the dataset for low- and high-strength mixtures may reduce uncertainty, but error analysis should still be performed to verify model performance.

<ins>recycled_aggregate_fraction_distribution_rca.png<ins>

Mixtures with 40-50% recycled aggregate replacement seem to be the most prevalent, alongside a noticeable spike near 20% recycled aggregate replacement. This communicates that the trained models may have less error within these recycled aggregate ranges due to the larger sample size relative to other ranges. It also demonstrates that mixtures with a high recycled aggregate content should be interpreted with caution, as the models have minimal training data.

<ins>strength_vs_recycled_fraction_rca.png<ins>

The scatterplot shows a similar result to the recycled aggregate and target distribution histograms, with a high frequency of mixtures between 30-50 MPa and 40-50% recycled aggregate replacement. Sparsely represented ranges, such as between 60-80 MPa and 0-40% recycled aggregate replacement, indicate areas that require more cautious interpretation.

<ins>correlation_heatmap_rca.png<ins>

The purpose of this graph is to analyze the exploratory relationships between variables in the present dataset. Notable relationships include the positive correlation between cement and compressive strength, which is present in the UCI dataset in previous notebooks. A negative correlation can be seen between compressive strength and water-cement ratio, indicating its importance in predicting concrete compressive strength. However, it only provides exploratory context for the present data and should not be interpreted as causal evidence or as a replacement for model-based feature importance.

<ins>pred_vs_actual_RandomForest_tuned_rca.png<ins>

Most predictions follow the one-to-one line, but larger errors at lower- and higher-strength mixtures. This is consistent with the target and recycled aggregate distribution histograms, as less data exists at those ranges to train the models.

<ins>residual_plot_RandomForest_tuned_rca.png<ins>

The figure shows a large range for the residual values. Significant overpredictions and underpredictions exist at low and high predicted compressive strengths. More detailed conclusions cannot be reached due to the small test set.

<ins>feature_importance_RandomForest_tuned_rca.png<ins>

The water-cement ratio and water content of the mixtures are the strongest predictive variables within this fitted model. However, it is also important to note that the permutation importance is calculated on a small held-out test set of 21 observations. This means that this importance is exploratory/model-specific and should not be considered direct physical or causal effects. Other features seem to be significantly less important in model predictions based on the permutation importance, the most notable of which are fine aggregates and aggregate-cement ratio.

<ins>repeated_group_validation_r2_rca.png + repeated_group_validation_mae_rca.png<ins>

The results represented in these graphs are significant, as they differ from the hyperparameter tuning and model selection process in Section 10. Specifically, the primary hold-out result is not representative of every split. Additionally, the repeated-validation metrics act as a quantifiable measure of robustness outside of training data.

<ins>measured_vs_predicted_stable_pareto_frontiers_rca.png<ins>

The figure plots stable Pareto candidates based on measured and OOF-predicted compressive strength. Notably, limited overlap between stable candidate sets across both frontiers indicates that model-based candidate identification remains exploratory. Additionally, measured and predicted frontiers overlap for some candidate mixtures but diverge for others, indicating that model-based candidate selection is not identical to selection using measured strength. Therefore, due to the lack of overlap, model-based Pareto candidate identification should be treated as exploratory rather than as a direct reproduction of the measured frontier.

<ins>stable_pareto_residual_plot_rca.png<ins>

The predicted and measured frontiers share two stable candidates, while most stable candidates differ between the two frontiers. Specifically, these overlaps are reported as rows 28 and 58 of the RCA dataset in Section 16 of Notebook 3. Additionally, the residual plot serves only as a descriptive visualization of overlapping stable Pareto candidates. Therefore, model-based Pareto candidate identification should be treated as exploratory rather than as a direct reproduction of the measured frontier.
