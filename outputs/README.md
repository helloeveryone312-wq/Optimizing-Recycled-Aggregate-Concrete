cv_summary.csv:

This compares the three models' provided R^2 values and the mean absolute error (MAE), showing the mean and standard deviation (std) of each.
Using this summary, the higher-performing model among the three can be determined.


test_set_results.csv:

This presents the results of the three models using the test set, which was held out from training and used only for final model evaluation.
The CSV provides an R^2 value on the test set and compares it to the training set results, yielding an MAE for each model.


permutation_importance_GradientBoosting_tuned.csv:

This represents the importance of each feature considered in evaluating recycled aggregate concrete, given the data of the best model (In this case, GradientBoosting)
These features are stored in a table with their respective means and standard deviations.
