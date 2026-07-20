**Figure Overview** -> This section will briefly describe the "figures" section of this GitHub (note that gradient boosting was considered the best and selected model, and thus is used in all the figures):

<ins>Baseline Figures:<ins>
- feature_importance_GradientBoosting_baseline.png + feature_importance_GradientBoosting_tuned_baseline.png
  - Provides a visualization for the given CSV file: "permutation_importance_GradientBoosting_tuned.csv".
  - Defines the importance assigned by the selected model to each feature in predicting concrete compressive strength.
  - The tuned feature importance graph had the selected model go through hyperparameter tuning before creating the figure.
- pred_vs_actual_GradientBoosting_baseline.png + pred_vs_actual_GradientBoosting_tuned_baseline.png
  - Provides a graph representing the prediction accuracy of the best model regarding concrete compressive strength.
  - Shows a reasonable level of accuracy for determining feature importance, determined by test set results.
  - The tuned scatterplot graph had the selected model go through hyperparameter tuning before creating the figure.
- tradeoff_strength_vs_co2_proxy_baseline.png + tradeoff_strength_vs_cost_proxy_baseline.png:
  - These figures provide the estimated CO₂ in kg CO₂e per m^3 of material or cost in USD per m^3 of material based on the predicted concrete compressive strength of concrete using SCMs (supplemental cementitious materials) and different aggregates.
  - Units are presented in predicted compressive strength in MPa on the y-axis
  - Labeled as a proxy analysis due to inconsistent, varying values across features and industries.
- residual_plot_GradientBoosting_baseline.png + residual_plot_GradientBoosting_tuned_baseline.png
  - This plot shows the residuals at different levels of concrete compressive strength based on the predictions of the gradient boosting model.
  - Demonstrates the model is accurate with an uncertainty of ±5 MPa for most predictions.
  - The tuned scatterplot graph had the selected model go through hyperparameter tuning before creating the figure.
- pareto_candidates_baseline.png + pareto_candidates_cost_baseline.png
  - Provides a highlighted graph with optimal mixtures to minimize CO₂ and cost while maximizing the concrete compressive strength, respectively.
  - The graphical results stem from a proxy analysis and should not be considered fully accurate.
  - Units are presented in CO₂ in kg CO₂e per m^3 of material or cost in USD per m^3 on the x-axis.
  - Units are presented in predicted compressive strength in MPa on the y-axis.
- target_distribution_baseline.png
  - Represents the distribution of concrete compressive strength between each row in the dataset.
  - Shows a right-skewed distribution of the data, indicating a larger amount of data between 0-40 MPa.
- correlation_heatmap_baseline.png
  - Demonstrates the exploratory relationships between target and feature columns in the dataset.
  - Shows a positive correlation between cement, age, and superplasticizer, and a weaker or negative correlation with water, fly ash, and aggregates with concrete compressive strength


 **Figure Analysis** -> This section will go more in depth about the contents of each figure, specifically, any relationships, outliers, and behaviors the figure may contain. Please refer to the tuned figures from 02_cv_tuning_and_outputs.ipynb as the authoritative source for final model performance.

<ins>feature_importance_GradientBoosting_baseline.png + feature_importance_GradientBoosting_tuned_baseline.png<ins>

The model depends on age, cement, and blast furnace slag when predicting concrete compressive strength. This does not indicate direct physical causation, just the model's dependence when making predictions. However, even though this graph matches real-world observations to an extent, it's also important to note that low-importance variables, such as fly ash, do not reflect their significance in practical applications. Additionally, correlated variables can distort the permutation importance values.

<ins>pred_vs_actual_GradientBoosting_baseline.png + pred_vs_actual_GradientBoosting_tuned_baseline.png<ins>

The figure shows that the Gradient Boosting model has a high predictive accuracy, with the plotted points following the diagonal line. As the actual strength increases, outliers become more prevalent on the graph. However, this may be due to a lack of points in the CSV with higher concrete compressive strength values, and the graph may appear different for another dataset.

<ins>tradeoff_strength_vs_co2_proxy.png + tradeoff_strength_vs_cost_proxy.png<ins>

Both figures are considered a proxy analysis due to the inconsistent values of cost and CO₂. The study attempts to find relevant values close to the present-day, but a mismatch will almost always persist. Although a positive relationship exists between increasing cost/CO₂ and increasing concrete compressive strength, it is clear that a non-linear relationship exists between cost/CO₂ and predicted strength. This indicates that there are many different mixtures to optimize either factor based on the chosen features.

<ins>residual_plot_GradientBoosting_baseline.png + residual_plot_GradientBoosting_tuned_baseline.png<ins>

Model accuracy is shown to be accurate, with most predicted values hovering within 5 MPa of the actual value. The model seems to underpredict at a lesser magnitude more frequently; however, it also overpredicts more often at a higher magnitude greater than 5 MPa of the actual value. A different spread of data may change the current results, but the residuals lie in an acceptable range for the model's overall accuracy.

<ins>pareto_candidates_baseline.png + pareto_candidates_cost_baseline.png<ins>

The graph demonstrates that there is an upper limit to the compressive strength of a concrete mixture as CO₂ increases. However, mixtures generally need to reach higher CO₂ levels before increasing in strength, matching previous graphs that highlighted cement as an important feature (for example, notice how the level of cement increases as predicted strength increases). Future development of the project will involve inputting values with a more accurate proxy analysis.

<ins>target_distribution_baseline.png<ins>

The target distribution graph shows a few peaks around 20-40 MPa, but generally follows a right-skewed distribution. This means that the machine-learning models trained from this data will most likely be more accurate for concrete compressive strength between 0 and 40 MPa. Note that this graph does not automatically assume that the target follows a normal distribution.

<ins>correlation_heatmap_baseline.png<ins>

The purpose of this graph is to analyze the exploratory relationships between variables in the UCI dataset. The heatmap demonstrates that age, cement, and superplasticizer have a positive correlation with concrete compressive strength, showing they're useful when making concrete compressive strength predictions. Other features seem to have a lesser or negative correlation, indicating that these features are less useful in making strength predictions. However, it only provides exploratory context for the present data and should not be interpreted as causal evidence or as a replacement for model-based feature importance.

Author's Note: age, cement, water, and blast furnace slag are the strongest features in the **current** baseline model, but are subject to change.
