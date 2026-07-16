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
- residual_plot_baseline.png
  - This plot shows the residuals at different levels of concrete compressive strength based on the predictions of the gradient boosting model.
  - Demonstrates the model is accurate with an uncertainty of ±5 MPa for most predictions.
- pareto_candidates_baseline.png
  - Provides a highlighted graph with optimal mixtures to minimize CO₂ while maximizing the concrete compressive strength.
  - The graphical results stem from a proxy analysis and should not be considered fully accurate.


 **Figure Analysis** -> This section will go more in depth about the contents of each figure, specifically, any relationships, outliers, and behaviors the figure may contain.

<ins>feature_importance_GradientBoosting_tuned.png<ins>

The figure demonstrates that **age, cement, and water** seem to be the most important features when predicting concrete compressive strength, but do not indicate direct physical causation. This graph matches real-world observations to an extent, though correlated variables can distort the importance. It's also important to note that low-importance variables, such as fly ash, do not reflect their significance in practical applications.

Notably, fly ash has a low permutation importance in the current baseline model. This does not mean fly ash is scientifically unimportant, nor does it mean it doesn't have a practical application. Rather, it highlights the limited predictive influence of the currently trained model. 

<ins>pred_vs_actual_GradientBoosting_tuned.png<ins>

The figure shows that the Gradient Boosting model has a high predictive accuracy, with the plotted points following the diagonal line. As the actual strength increases, outliers become more prevalent on the graph. However, this may be due to a lack of points in the CSV with higher concrete compressive strength values, and the graph may appear different for another dataset.

<ins>tradeoff_strength_vs_co2_proxy.png + tradeoff_strength_vs_cost_proxy.png<ins>

Both figures are considered a proxy analysis until further research has been conducted to confirm the cost and CO₂ values. Although a positive relationship exists between increasing cost/CO₂ and increasing concrete compressive strength, it is clear that a non-linear relationship exists between cost/CO₂ and predicted strength. This indicates that there are many different mixtures to optimize either factor based on the chosen features.

<ins>residual_plot_baseline.png<ins>

The figure demonstrates that the model tended to underpredict more frequently at lower magnitudes of concrete compressive strength and had an increased number of overpredictions as the magnitude increased. A different spread of data may change the current results, but the residuals lie in an acceptable range for the model's overall accuracy.

<ins>pareto_candidates_baseline.png<ins>

The graph demonstrates that there is an upper limit to the compressive strength of a concrete mixture as CO₂ increases. However, mixtures generally need to reach higher CO₂ levels before increasing in strength, matching previous graphs that highlighted cement as an important feature (for example, notice how the level of cement increases as predicted strength increases). Future development of the project will input values based on literature results rather than a proxy analysis.

Author's Note: age, cement, water, and blast furnace slag are the strongest features in the **current** baseline model, but are subject to change.
