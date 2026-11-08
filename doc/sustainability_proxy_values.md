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

Source publications vary from 2019 to 2026 in both sustainability factor CSVs. US price notes and other values without DOIs refer to the most recent estimations available (Ex., fly ash and ground granulated blast furnace slag in sustainability_factor.csv). This presents a notable difference that could affect the Pareto analysis, as price and emissions values could have fluctuated noticeably. Additionally, the geographic locations are not consistent across all sources, and an attempt is made to keep source values focused on the US. Generally, these comments only apply to the material costs, as global emissions shouldn't be affected by geography, but may be affected in 2022 by COVID-19 and other related events.

**Sustainability Proxy Values** -> The proxy values used in the notebooks are available in sustainability_factors.csv and rca_sustainability_factor_scenario.csv. The original value and the converted value are listed under their respective CSV file. Conversion information can be found within the specific CSVs.

<ins>sustainability_factors.csv<ins>
- Cement
  - Original Emissions Value: 0.83 kg CO₂e/kg
  - Converted Emissions Value: 0.83 kg CO₂e/kg
  - Original Cost Value: 2.25 TWD/kg
  - Converted Cost Value: 0.072 USD/kg
- Blast Furnace Slag
  - Original Emissions Value: 0.143 tonne CO₂e/tonne
  - Converted Emissions Value: 0.143 kg CO₂e/kg
  - Original Cost Value: 54 USD/tonne
  - Converted Cost Value: 0.054 USD/kg
- Fly Ash
  - Original Emissions Value: 0.1 kg CO₂e/tonne
  - Converted Emissions Value: 0.0001 kg CO₂e/kg
  - Original Cost Value: 126 USD/tonne
  - Converted Cost Value: 0.126 USD/kg
- Water
  - Original Emissions Value: 0.000196 kg CO₂e/kg
  - Converted Emissions Value: 0.000196 kg CO₂e/kg
  - Original Cost Value: 0.01 TWD/kg
  - Converted Cost Value: 0.00032 USD/kg
- Superplasticizer
  - Original Emissions Value: 0.25 kg CO₂e/kg
  - Converted Emissions Value: 0.25 kg CO₂e/kg
  - Original Cost Value: 25.1 TWD/kg
  - Converted Cost Value: 0.8032 USD/kg
- Coarse Aggregate
  - Original Emissions Value: 0.0075 kg CO₂e/kg
  - Converted Emissions Value: 0.0075 kg CO₂e/kg
  - Original Cost Value: 0.30 TWD/kg
  - Converted Cost Value: 0.0096 USD/kg
- Fine Aggregate
  - Original Emissions Value: 0.0026 kg CO₂e/kg
  - Converted Emissions Value: 0.0026 kg CO₂e/kg
  - Original Cost Value: 0.25 TWD/kg
  - Converted Cost Value: 0.008 USD/kg

<ins>rca_sustainability_factor_scenario.csv<ins>
- Emissions Factor Scenario
  - Low
    - Cement
      - Original Emissions Value: 0.8726 kg CO₂e/kg
      - Converted Emissions Value: 0.8726 kg CO₂e/kg
    - Water
      - Original Emissions Value: 0.149 kg CO₂e/m³
      - Converted Emissions Value: 0.000149 kg CO₂e/kg
    - Natural Fine Aggregate
      - Original Emissions Value: 0.00221 kg CO₂e/kg
      - Converted Emissions Value: 0.00221 kg CO₂e/kg
    - Natural Coarse Aggregate
      - Original Emissions Value: 0.0041 kg CO₂e/kg
      - Converted Emissions Value: 0.0041 kg CO₂e/kg
    - Recycled Fine Aggregate
      - Original Emissions Value: 0.0014 kg CO₂e/kg
      - Converted Emissions Value: 0.0014 kg CO₂e/kg
    - Recycled Coarse Aggregate
      - Original Emissions Value: 0.0014 kg CO₂e/kg
      - Converted Emissions Value: 0.0014 kg CO₂e/kg
  - Central
    - Cement
      - Original Emissions Value: 0.912 kg CO₂e/kg
      - Converted Emissions Value: 0.912 kg CO₂e/kg
    - Water
      - Original Emissions Value: 0.196 kg CO₂e/m³
      - Converted Emissions Value: 0.000196 kg CO₂e/kg
    - Natural Fine Aggregate
      - Original Emissions Value: 0.0055 kg CO₂e/kg
      - Converted Emissions Value: 0.0055 kg CO₂e/kg
    - Natural Coarse Aggregate
      - Original Emissions Value: 0.0143 kg CO₂e/kg
      - Converted Emissions Value: 0.0143 kg CO₂e/kg
    - Recycled Fine Aggregate
      - Original Emissions Value: 0.0149 kg CO₂e/kg
      - Converted Emissions Value: 0.0149 kg CO₂e/kg
    - Recycled Coarse Aggregate
      - Original Emissions Value: 0.0149 kg CO₂e/kg
      - Converted Emissions Value: 0.0149 kg CO₂e/kg
  - High
    - Cement
      - Original Emissions Value: 1.002 kg CO₂e/kg
      - Converted Emissions Value: 1.002 kg CO₂e/kg
    - Water
      - Original Emissions Value: 0.00041 kg CO₂e/kg
      - Converted Emissions Value: 0.00041 kg CO₂e/kg
    - Natural Fine Aggregate
      - Original Emissions Value: 0.0314 kg CO₂e/kg
      - Converted Emissions Value: 0.0314 kg CO₂e/kg
    - Natural Coarse Aggregate
      - Original Emissions Value: 0.0314 kg CO₂e/kg
      - Converted Emissions Value: 0.0314 kg CO₂e/kg
    - Recycled Fine Aggregate
      - Original Emissions Value: 0.0381 kg CO₂e/kg
      - Converted Emissions Value: 0.0381 kg CO₂e/kg
    - Recycled Coarse Aggregate
      - Original Emissions Value: 0.0381 kg CO₂e/kg
      - Converted Emissions Value: 0.0381 kg CO₂e/kg
