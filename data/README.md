**Data Transparency** -> The data is from UC Irvine's Machine Learning Repository. The download links are as follows:
- https://archive.ics.uci.edu/dataset/165/concrete+compressive+strength (directly from the archive)
- https://www.kaggle.com/datasets/elikplim/concrete-compressive-strength-data-set/data (Kaggle download by Ahiale Darlington, stored in REPO)

**Dataset Description** -> This section will describe all the details regarding the dataset used.

<ins>Concrete Compressive Strength Dataset<ins>
1. CSV name: concrete_data
2. Where is the CSV from: UC Irvine Machine Learning Repository
3. DOI: https://doi.org/10.24432/C5PK67
4. Included in REPO: Yes
5. Number of rows: 1030
6. Number of input features: 8
7. Target: concrete compressive strength in MPa.
8. Units: kg/m³ for mixture ingredients, days for age, MPa for strength.
9. What the CSV contains: cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, fine aggregate, age, concrete compressive strength. Note that "blast furnace slag" refers to ground granulated blast furnace slag (GGBFS), and both aggregates are natural, not recycled.
10. Where is this used and how: the CSV is used in both 01_baseline_strength_model.ipynb and 02_cv_tuning_and_outputs.ipynb. The data is used to train baseline models and is utilized in model-related outputs/figures except the Pareto exploration (though a model trained on the data is used in this case).
11. Notebook outputs of the CSV: the current outputs consist of ranking the permutation importance of each feature using a Gradient Boosting model, test set results from a train-test split ranking the performance of 3 models based on R^2 and MAE, and a summary ranking the models on their R^2 value based on a 5-fold cross-validation on the training set. The CSV is also used to graph all relevant figures in the present repo.
12. Limitation: CSV does not contain any direct RCA feature or information for cost/CO₂ proxies.

<ins>Mechanical Properties of Recycled Aggregate Concrete Dataset<ins>
1. CSV name: rca_awoyera_2025_mechanical_properties
2. Where is the CSV from: Mendeley Data Repository
3. DOI: https://doi.org/10.17632/2pxdbh6vx7.1
4. Included in REPO: Yes
5. Number of rows: 112
6. Number of input features: 8
7. Target: concrete compressive, split tensile, and flexural strength in MPa; modulus of elasticity in MPa.
8. Units: kg/m³ for mixture ingredients, MPa for target values.
9. What the CSV contains: w/c, a/c, water, cement, natural fine aggregate, natural coarse aggregate, recycled coarse aggregate, recycled fine aggregate, compressive strength, split tensile strength, flexural strength, and modulus of elasticity.
10. Where is this used and how: the CSV is used in 03_rca_dataset_modeling.ipynb. The data is used to train a model on the effect of recycled aggregates on concrete compressive strength. It is utilized in almost all model-related figures and outputs, alongside model robustness checks. One row is edited for an impossible value, then kept. The correction is recorded on rca_data_corrections.csv and applied in 03_rca_dataset_modeling_and_pareto_analysis.ipynb, Section 4 of the code.
11. Notebook outputs of the CSV: the current outputs consist of tuned and untuned model metrics, Pareto-optimal mixtures, permutation importance values, and model prediction inconsistencies across different feature ranges. The CSV is also used to graph all relevant figures in the present repo.
12. Limitation: the CSV has limited information on calculating input variables, such as a/c and w/c.

**Sustainability Factors Description** -> One CSV is created in 02_cv_tuning_and_outputs.ipynb, where literature values and relevant information are stored and exported as a CSV by the notebook to conduct Pareto exploration. Each cost and emission factor for the features, alongside the relevance, source, and geography, is listed within the CSV. Three main sources exist:

- Mixture Optimization of Sustainable Concrete with Silica Fume Considering CO2 Emissions and Cost (Wang et al.)
- A Comprehensive Review on the Ground Granulated Blast Furnace Slag (GGBS) in Concrete Production (Ahmad et al.)
- Optimizing calcium efficiency for sustainable cement with GGBFS-fly ash systems (Wattanachai et al.)

Another CSV is used for 03_rca_dataset_modeling_and_pareto_analysis.ipynb with a much larger range of sources for different emission factor scenarios. Scenario, material, source, emissions value, DOI, original value, conversion method, and geography/context are all included in the CSV. A list of the relevant sources is below:

- Menegatti, L. C., Castrillon Fernandez, L. I., Caldas, L. R., Pepe, M., Pittau, F., Zani, G., Rampini, M. C., Michels, J., Toledo Filho, R. D., & Martinelli, E. (2022). Environmental Performance of Deconstructable Concrete Beams Made with Recycled Aggregates. Sustainability, 14(18), 11457. https://doi.org/10.3390/su141811457
- 

Source publications vary from 2019 to 2026 in both sustainability factor CSVs. US price notes and other values without DOIs refer to the most recent estimations available (Ex., fly ash and ground granulated blast furnace slag in sustainability_factor.csv). This presents a notable difference that could affect the Pareto analysis, as price and emissions values could have fluctuated noticeably. Additionally, the geographical locations are not the same throughout all sources, and an attempt is made to keep source values focused in the US. Generally, these comments only apply to the material costs, as global emissions shouldn't be affected by geography, but may be affected in 2022 by COVID-19 and other related events.
