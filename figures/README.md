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


 **Figure Analysis** -> This section will go more in depth about the contents of each figure, specifically, any relationships, outliers, and behaviors the figure may contain.

<ins>feature_importance_GradientBoosting_tuned.png<ins>

The figure demonstrates that **age, cement, water, and blast furnace slag** have the highest permutation importance value when determining a concrete mixture's compressive strength. This graph matches real-world observations but does not show the relationship between the feature and the compressive strength of a mixture. Thus, graphs such as the correlation heatmap in 01_baseline_strength_model.ipynb can be used alongside feature importance to better understand these variables.

Notably, fly ash has a low permutation importance in the current baseline model. This does not mean fly ash is scientifically unimportant, nor does it mean it doesn't have a practical application. Rather, it highlights the limited predictive influence of the currently trained model. 

<ins>pred_vs_actual_GradientBoosting_tuned.png<ins>

The figure shows that the Gradient Boosting model has a high predictive accuracy, with the plotted points following the diagonal line. As the actual strength increases, outliers become more prevalent on the graph. However, this may be due to a lack of points in the CSV with higher concrete compressive strength values, and the graph may appear different for another dataset.

<ins>tradeoff_strength_vs_co2_proxy.png + tradeoff_strength_vs_cost_proxy.png<ins>

Both figures are considered a proxy analysis until further research has been conducted to confirm the cost and CO₂ values. Although a positive relationship exists between increasing cost/CO₂ and increasing concrete compressive strength, it is clear that a non-linear relationship exists between cost/CO₂ and predicted strength. This indicates that there are many different mixtures to optimize either factor based on the chosen features.

Author's Note: age, cement, water, and blast furnace slag are the strongest features in the **current** baseline model, but are subject to change.
