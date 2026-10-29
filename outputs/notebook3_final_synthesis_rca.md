# Notebook 3 RCA final synthesis

Dataset: Paul Awoyera (2025), Mechanical Properties of Recycled Aggregate Concrete, DOI 10.17632/2pxdbh6vx7.1.

Data audit:
- Raw rows: 112
- Documented rows removed: 1
- Rows removed for missing, nonnumeric, or impossible values: 0
- Physically implausible rows excluded after being saved for review: 0
- Exact duplicate rows removed: 7
- Cleaned rows modeled: 104
- Aggregate-cement ratio consistency rate: 0.163

Modeling:
- Selected feature set from training-only grouped CV: verified_original
- Selected model: RandomForest_tuned
- Primary grouped hold-out R²: 0.675
- Primary grouped hold-out MAE: 4.463 MPa
- Primary grouped hold-out RMSE: 6.945 MPa

Nested grouped out-of-fold prediction:
- OOF R²: 0.767
- OOF MAE: 4.569 MPa
- OOF RMSE: 5.972 MPa

Repeated nested grouped validation:
- Median R²: 0.806
- R² range across outer splits: 0.624–0.928
- Median MAE: 4.093 MPa
- MAE range across outer splits: 2.325–7.259 MPa
- Median RMSE: 5.565 MPa
- RMSE range across outer splits: 3.124–8.932 MPa

Held-out test-set error analysis:
- Highest-strength quartile (Q4) count: 5
- Highest-strength quartile (Q4) mean absolute error: 3.192 MPa
Sustainability and Pareto analysis:
- Pareto candidates by emission scenario (measured / OOF predicted): low = 17 / 19; central = 19 / 16; high = 18 / 13
- Total unique Pareto candidates across all three scenarios: 41
- Stable Pareto candidates across all three scenarios: 10 OOF predicted and 10 measured.
- Stable candidates appearing in both measured and OOF predicted frontiers: 2
- The proxy is not a complete life-cycle assessment due to a wide geographical and temporal span in the source data.
- Candidate mixtures are observed nondominated examples, not globally optimized recipes.

Recommended conclusion:
The RCA dataset extends the baseline SCM modeling architecture by adding recycled coarse and fine aggregate variables. The strongest conclusions are the reproducible group-aware prediction results and the sensitivity-tested identification of observed strength-emissions tradeoffs. Claims about universal RCA effects, exact life-cycle emissions, or optimal mixture design are not supported without independent external validation and experimentally controlled data.