# CHFMSD - Atlantic City
(Coastal Hybrid Flood Mitigation System Dataset for Atlantic City, NJ, USA)

This repository contains a dataset derived from a multi-objective optimization study for hybrid vegetation-seawall coastal defense systems. The dataset is specifically curated for researchers and practitioners working on cost-effective, resilient, and sustainable coastal protection strategies.

---

## Dataset Overview

This dataset consists of **12,800 rows**, each representing a unique combination of wave conditions and hybrid vegetation-seawall design parameters. The primary goal of this dataset is to aid in the analysis and optimization of hybrid coastal defense systems.

---

## Variables Description

### Input Variables (Design Features and Wave Conditions)

| Variable       | Description                              | Unit               |
|----------------|------------------------------------------|--------------------|
| `Hs`           | Significant wave height                  | m                  |
| `Tp`           | Peak wave period                         | s                  |
| `s`            | Wave steepness (extra info)              | s                  |
| `Av`           | Vegetation area                          | m²                 |
| `Nv`           | Vegetation density                       | stems/m²           |
| `Hsw`          | Seawall height                           | m                  |

### Output Variables (Performance Metrics)

| Variable                | Description                                               | Unit               |
|-------------------------|-----------------------------------------------------------|--------------------|
| `Normalized wave Runup` | 98th-percentile wave runup/seawall height (Hsw)           | -                  |
| `Overtopping Volume`    | Volume of water overtopping the seawall                   | m³/m               |
| `Robustness`            | System’s ability to control the wave runup                | %                  |
| `Flood Serviceability`  | Effectiveness in mitigating flooding during overtopping   | %                  |

---

## Data Format

The dataset is provided as a `.mat` file. Each row corresponds to a unique scenario, with the columns representing the variables as described above.

### Example Row (Data Values)
```plaintext
Hs: 4.4 m  Tp: 12.5 s  Steepness(Hs/wavelength): 120.2   Hsw: 0.45   Av: 5.2   Nv: 24.7  Normalized wave Runup: 1.0   Overtopping Volume: 125.1 m³/m  System's Robustness (runup control): 40.7%  Flood Serviceability: 85.8%  
```

---

## Methodology

The dataset was generated through a comprehensive modeling and optimization pipeline involving the following steps:

1. **Dynamic Wave Modeling**:
   - Simulations were performed using the XBeach Non-Hydrostatic (XBNH) model to compute wave runup and overtopping under diverse storm wave conditions.
   - Wave scenarios are based on synthetic hurricane datasets tailored for the New Jersey coast, including peak wave periods (`Tp`) ranging from 4 to 14.7 seconds and significant wave heights (`Hs`) up to 4.6 meters.

2. **Data-Driven Model**:
   - A symbolic regression-based surrogate model (Gene Expression Programming, GEP) was trained on XBNH outputs.
   - The model captures complex relationships between wave parameters, design features, and performance metrics.

3. **Optimization**:
   - Multi-objective optimization using the Non-Dominated Sorting Genetic Algorithm II (NSGA-II).
   - Objectives:
     - Minimize project total cost.
     - Maximize wave robustness and flood serviceability.
   - Constraints:
     - Maximum seawall height: 1.29 m
     - Vegetation area: Up to 36 m²
     - Vegetation density: Up to 500 stems/m²

---

## Use Cases

This dataset is ideal for:
- **Model Validation**: Benchmarking predictive models for coastal defense system performance.
- **Optimization Studies**: Evaluating trade-offs in design variables for hybrid coastal protection.
- **Policy and Decision-Making**: Informing risk-tolerant coastal infrastructure planning and investments.

---

## File Structure

| File Name            | Description                                       |
|----------------------|---------------------------------------------------|
| `hybrid_systems.mat` | The dataset containing all variables and metrics. |
| `example_plot`       | Visualization example                             |
| `cost_function.m`    | MATLAB file containing the cost calculation function. |

---

## Citation

If you use this dataset, please cite the following publication:

> Amini, E., Marsooli, R., et al. (2024). "Hybrid Vegetation-Seawall Coastal Systems for Wave Hazard Reduction: Analytics for Cost-effective Design from Optimized Features." _npj Natural Hazards_.

---

## Contact

For questions or further information about the dataset, please contact:

**Erfan Amini**  
[Email: eamini@stevens.edu](mailto:eamini@stevens.edu)

---

## Acknowledgments

This dataset was developed as part of a study supported by the Department of Civil, Environmental, and Ocean Engineering at Stevens Institute of Technology. Special thanks to collaborators and supporting institutions for their contributions. This project is funded, in part, by the US Coastal Research Program (USCRP) as administered by the US Army Corps of Engineers® (USACE), Department of Defense (Contract No. W912HZ22C0010). The content of the information provided in this publication does not necessarily reflect the position or the policy of the government, and no official endorsement should be inferred. The authors acknowledge the USACE and USCRP’s support of their effort to strengthen coastal academic programs and address coastal community needs in the United States.

---

## License

This dataset is shared under the [MIT License](LICENSE). Please ensure appropriate citation and attribution when using this dataset.
