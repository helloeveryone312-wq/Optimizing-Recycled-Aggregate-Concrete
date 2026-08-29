# Notebook 3 RCA final synthesis

Dataset: Paul Awoyera (2025), Mechanical Properties of Recycled Aggregate Concrete, DOI 10.17632/2pxdbh6vx7.1.

Data audit:
- Raw rows: 112
- Documented corrections applied: 1
- Physically implausible rows excluded after being saved for review: 0
- Cleaned rows modeled: 105
- Aggregate-cement ratio consistency rate: 0.162
- Aggregate-cement ratio treated as a verified feature: False

Modeling:
- Selected feature set from training-only grouped CV: verified_original
- Selected model: RandomForest_tuned
- Primary grouped hold-out R²: 0.868
- Primary grouped hold-out MAE: 3.518 MPa
- Primary grouped hold-out RMSE: 4.597 MPa

Repeated nested grouped validation:
- Median R²: 0.778
- Median MAE: 4.104 MPa
- Median RMSE: 5.606 MPa

Held-out test-set error analysis:
- Highest-strength quartile (Q4) count: 5
- Highest-strength quartile (Q4) mean absolute error: 5.884 MPa
Sustainability and Pareto analysis:
- Stable predicted Pareto candidates across all three factor scenarios: 13
- The proxy is not a complete life-cycle assessment.
- Candidate mixtures are observed nondominated examples, not globally optimized recipes.

Recommended conclusion:
The RCA dataset extends the baseline SCM modeling architecture by adding recycled coarse and fine aggregate variables. The strongest conclusions are the reproducible group-aware prediction results and the sensitivity-tested identification of observed strength-emissions tradeoffs. Claims about universal RCA effects, exact life-cycle emissions, or optimal mixture design are not supported without independent external validation and experimentally controlled data.