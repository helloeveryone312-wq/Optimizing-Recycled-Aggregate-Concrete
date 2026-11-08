Mechanical Properties of Recycled Aggregate Concrete Dataset

1. CSV name: rca_awoyera_2025_mechanical_properties
2. Where is the CSV from: Mendeley Data Repository
3. DOI: https://doi.org/10.17632/2pxdbh6vx7.1
4. Included in REPO: Yes
5. Number of rows: 112
6. Number of input features: 8
7. Target: concrete compressive, split tensile, and flexural strength in MPa; modulus of elasticity in MPa.
8. Units: kg/m³ for mixture ingredients, MPa for target values.
9. What the CSV contains: w/c, a/c, water, cement, natural fine aggregate, natural coarse aggregate, recycled coarse aggregate, recycled fine 
aggregate, compressive strength, split tensile strength, flexural strength, and modulus of elasticity.
10. Where is this used and how: the CSV is used in 03_rca_dataset_modeling.ipynb. The data is used to train a model on the effect of recycled 
aggregates on concrete compressive strength. It is utilized in almost all model-related figures and outputs, alongside model robustness checks. 
One row is edited for an impossible value, then kept. The correction is recorded on rca_data_corrections.csv and applied in 
03_rca_dataset_modeling_and_pareto_analysis.ipynb, Section 4 of the code.
11. Notebook outputs of the CSV: the current outputs consist of tuned and untuned model metrics, Pareto-optimal mixtures, permutation importance 
values, and model prediction inconsistencies across different feature ranges. The CSV is also used to graph all relevant figures in the present 
repo.
12. Limitation: the CSV has limited information on calculating input variables, such as a/c and w/c.
