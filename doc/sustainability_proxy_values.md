**Sustainability Factors Description** -> One CSV is created in 02_cv_tuning_and_outputs.ipynb, where literature values and relevant information are stored and exported as a CSV by the notebook to conduct Pareto exploration. Each cost and emission factor for the features, alongside the relevance, source, and geography, is listed within the CSV. Three main sources exist:

- Mixture Optimization of Sustainable Concrete with Silica Fume Considering CO2 Emissions and Cost (Wang et al.)
- A Comprehensive Review on the Ground Granulated Blast Furnace Slag (GGBS) in Concrete Production (Ahmad et al.)
- Optimizing calcium efficiency for sustainable cement with GGBFS-fly ash systems (Wattanachai et al.)

Another CSV is used for 03_rca_dataset_modeling_and_pareto_analysis.ipynb with a much larger range of sources for different emission factor scenarios. Scenario, material, source, emissions value, DOI, original value, conversion method, and geography/context are all included in the CSV. A list of the relevant sources is below:

- Menegatti, L. C., Castrillon Fernandez, L. I., Caldas, L. R., Pepe, M., Pittau, F., Zani, G., Rampini, M. C., Michels, J., Toledo Filho, R. D., & Martinelli, E. (2022). Environmental Performance of Deconstructable Concrete Beams Made with Recycled Aggregates. Sustainability, 14(18), 11457. https://doi.org/10.3390/su141811457
- Suescum-Morales, D., Fernández-Ledesma, E., González-Caro, Á., Merino-Lechuga, A. M., Fernández-Rodríguez, J. M., & Jiménez, J. R. (2023). Carbon Emission Evaluation of CO2 Curing in Vibro-Compacted Precast Concrete Made with Recycled Aggregates. Materials, 16(6), 2436. https://doi.org/10.3390/ma16062436
- Wang, Y.-S., Cho, H.-K., & Wang, X.-Y. (2022). Mixture Optimization of Sustainable Concrete with Silica Fume Considering CO2 Emissions and Cost. Buildings, 12(10), 1580. https://doi.org/10.3390/buildings12101580
- Newton-Hoare, L., Jamieson, S., & White, G. (2025). Review of the Use of Waste Materials in Rigid Airport Pavements: Opportunities, Benefits and Implementation. Sustainability, 17(15), 6959. https://doi.org/10.3390/su17156959
- Climatiq. (2019). Portland Cement [Emission Factor]. https://www.climatiq.io/data/emission-factor/a7a8ae36-66d5-41ff-a4d6-03a1e993b97a
- Climatiq. (2021). Water supply [Emission factor]. https://www.climatiq.io/data/emission-factor/cfc5219c-b9e9-47ed-b59d-24de5036be75
- Roh, S., Kim, R., Park, W.-J., & Ban, H. (2020). Environmental Evaluation of Concrete Containing Recycled and By-Product Aggregates Based on Life Cycle Assessment. Applied Sciences, 10(21), 7503. https://doi.org/10.3390/app10217503
- Kachouh, N., El-Maaddawy, T., El-Hassan, H., & El-Ariss, B. (2022). Shear Response of Recycled Aggregates Concrete Deep Beams Containing Steel Fibers and Web Openings. Sustainability, 14(2), 945. https://doi.org/10.3390/su14020945
- Park, W.-J., Kim, T., Roh, S., & Kim, R. (2019). Analysis of Life Cycle Environmental Impact of Recycled Aggregate. Applied Sciences, 9(5), 1021. https://doi.org/10.3390/app9051021

Source publications vary from 2019 to 2026 in both sustainability factor CSVs. US price notes and other values without DOIs refer to the most recent estimations available (Ex., fly ash and ground granulated blast furnace slag in sustainability_factor.csv). This presents a notable difference that could affect the Pareto analysis, as price and emissions values could have fluctuated noticeably. Additionally, the geographical locations are not the same throughout all sources, and an attempt is made to keep source values focused in the US. Generally, these comments only apply to the material costs, as global emissions shouldn't be affected by geography, but may be affected in 2022 by COVID-19 and other related events.
