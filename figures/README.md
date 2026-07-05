**Figure Overview** -> This section will briefly describe the "figures" section of this GitHub (note that gradient boosting was considered the best model, and thus is used in all the figures):

- feature_importance_GradientBoosting_tuned.png
  - Provides a visualization for the given CSV file: "permutation_importance_GradientBoosting_tuned.csv".
  - Defines the importance of each feature in determining concrete compressive strength based on the best model.
- pred_vs_actual_GradientBoosting_tuned.png
  - Provides a graph representing the prediction accuracy of the best model regarding concrete compressive strength.
  - Shows a reasonable level of accuracy for determining feature importance, determined by test set results.
- tradeoff_strength_vs_co2_proxy.png + tradeoff_strength_vs_cost_proxy.png:
  - These figures provide the estimated CO₂ in kg CO₂e per kg of material or cost in USD per kg of material based on the predicted concrete compressive strength of concrete using SCMs and different aggregates (supplemental cementitious materials).
  - Labeled as a proxy analysis due to improper current values.
