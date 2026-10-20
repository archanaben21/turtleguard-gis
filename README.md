# TurtleGuard GIS 🐢

**Geospatial Data Science | Biodiversity Mapping | Machine Learning**

TurtleGuard GIS is a Python-based geospatial data science project that explores turtle and tortoise occurrence records from China. It combines data cleaning, exploratory analysis, interactive mapping, spatial observation-hotspot analysis, and a Random Forest classification baseline.

The project demonstrates how GIS and machine learning techniques can be applied to biodiversity datasets while accounting for the limitations of observational data.

## Project Objectives

- Clean and validate species occurrence records and geographic coordinates.
- Explore recorded species, taxonomic families, provinces, and observation years.
- Visualise occurrence locations using interactive maps.
- Identify geographic grid cells with high concentrations of recorded observations.
- Train and evaluate a Random Forest classifier for taxonomic family classification.
- Export reproducible analysis outputs for further geospatial research.

## Dataset

**Source:** [China Testudines GIS Dataset — Clean and Curated](https://www.kaggle.com/datasets/aegoliusfunereus/china-testudines-gis-dataset-clean-and-curated)

The dataset contains cleaned occurrence records for turtles and tortoises, with fields including:

- `ScientificName` — recorded scientific species name
- `Family` — taxonomic family
- `Genus` — genus, where available
- `Province` — geographic administrative region
- `Latitude` and `Longitude` — geographic coordinates
- `Year` — observation year, where available

The dataset creator reports a strong concentration of observations in Taiwan. This sampling imbalance is an important limitation when interpreting spatial patterns.

**Data licence:** The source dataset is identified as CC BY-NC-SA 4.0. Consult the original dataset page and licence before redistributing data or derived datasets.

The original dataset is not included in this repository by default.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data cleaning and tabular analysis |
| NumPy | Numerical and grid calculations |
| Matplotlib and Seaborn | Statistical visualisation |
| Folium | Interactive geographic maps |
| Scikit-learn | Random Forest model and evaluation |
| Joblib | Saving the trained model |
| KaggleHub | Programmatic dataset download |
| Jupyter / Kaggle Notebooks | Interactive experimentation |

## Data Workflow

1. **Data acquisition:** Download the dataset using KaggleHub.
2. **Data validation:** Inspect the dataset schema, missing values, and coordinate ranges.
3. **Data cleaning:** Remove invalid coordinates, missing essential taxonomic fields, and duplicate records.
4. **Exploratory data analysis:** Summarise recorded species, families, provinces, and observation years.
5. **Spatial aggregation:** Group occurrence records into approximately 0.5-degree latitude-longitude grid cells.
6. **Geospatial visualisation:** Generate interactive occurrence and observation-hotspot maps.
7. **Model training:** Train a Random Forest classifier using latitude, longitude, and observation year to classify recorded taxonomic family.
8. **Evaluation:** Calculate accuracy, balanced accuracy, and per-class precision, recall, and F1-score.
9. **Export:** Save cleaned records, summary tables, maps, evaluation metrics, and the fitted model.

## Installation

Create a Python environment and install the dependencies:

```bash
pip install -r requirements.txt
```

## Running the Project

The recommended starting point is the Jupyter notebook:

```text
notebooks/turtleguard_analysis.ipynb
```

Alternatively, run the pipeline script if it has been assembled:

```bash
python src/pipeline.py
```

The notebook downloads the dataset using KaggleHub, processes the records, creates maps and summary tables, trains the baseline classifier, and exports the outputs.

Depending on your environment, Kaggle authentication or dataset-access permissions may be required.

## Outputs

The pipeline is designed to generate the following artefacts:

| Output | Description |
|---|---|
| `cleaned_turtles.csv` | Cleaned occurrence records |
| `observation_hotspots.csv` | Grid-level observation counts |
| `species_occurrence_map.html` | Interactive occurrence map |
| `observation_hotspot_map.html` | Interactive observation-hotspot map |
| `province_summary.csv` | Provincial occurrence and species summaries |
| `yearly_summary.csv` | Annual observation-record summaries |
| `family_classifier.joblib` | Saved Random Forest classifier |
| `model_metrics.txt` | Model evaluation report |

Actual files and metrics depend on the successful execution of the pipeline and availability of the corresponding dataset fields.

## Results

The analysis examines:

- The distribution of recorded turtle and tortoise species.
- The representation of taxonomic families in the dataset.
- Geographic concentrations of occurrence records.
- Differences in recorded observations across provinces and years.
- Baseline performance of the taxonomic family classifier.

**Quantitative results:** Accuracy, balanced accuracy, and per-family classification metrics should be reported after running the notebook. No performance values are assumed in advance.

Observation hotspots represent concentrations of available records, not confirmed areas of high turtle abundance or ecological importance.

## Scientific Limitations

- **Sampling bias:** Uneven reporting effort may strongly influence mapped patterns.
- **Observation counts:** Occurrence records are not population counts.
- **Taxonomic classification:** The model predicts recorded family labels from geographic and temporal features; it does not predict population size, extinction risk, or species conservation status.
- **Spatial leakage:** Random train-test splitting can place geographically nearby observations in both sets, potentially overstating generalisation performance.
- **Environmental variables:** The current baseline does not include habitat suitability, climate, elevation, or land-cover predictors.
- **Validation:** Spatially separated evaluation and independent validation data are needed before drawing stronger ecological conclusions.

## Future Improvements

- Introduce QGIS and GeoPandas for boundary-based spatial analysis.
- Evaluate the model using spatially separated cross-validation.
- Investigate sampling bias and geographic coverage.
- Integrate climate, vegetation, elevation, and land-cover data.
- Explore species distribution modelling where appropriate occurrence and background data are available.
- Develop an interactive Streamlit dashboard for exploring the results.

## Reproducibility

The project uses Python-based data processing and machine learning workflows. Record the dataset version, package versions, random seeds, and evaluation methodology when publishing experimental results.

## Author

**Archana Prajapati**

Research interests: Artificial Intelligence, Machine Learning, Geospatial Data Science, and Trustworthy AI.

## Disclaimer

This is an exploratory geospatial data science and machine-learning project. Its outputs are not validated conservation assessments and should not be used as a substitute for ecological field surveys or expert conservation decisions.
