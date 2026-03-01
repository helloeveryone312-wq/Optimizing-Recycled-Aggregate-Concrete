cv_summary.csv:

This compares the three models' provided R^2 value and the mean absolute error (mae), showing the mean and standard deviation (std) of each.
By using this summary, the higher performance model of the three can be determined.


test_set_results.csv:

This presents the results of the three models using the test set, which is the data that was separated from the training set and used to train the models.
The CSV provides an R^2 value based on the test set, and compares it to the results of the training set, giving an MAE for each model.


permutation_importance_GradientBoosting_tuned.csv:

This represents the importance of each feature considered in evaluating recycled aggregate concrete, given the data of the best model (In this case, GradientBoosting)
These features are stored in a table with their respective means and standard deviations.
