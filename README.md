# Global Air Quality Analytics

An end-to-end data engineering and machine-learning project built for the DEPI graduation project. It processes the WAQI Q4 2023 air-quality dataset through a Bronze → Silver → Gold pipeline, supports exploratory analysis and Power BI reporting, and trains a LightGBM regression model for a project-specific composite air-quality score.

## Workflow

```text
WAQI raw CSV
    ↓
Bronze ingestion → Silver cleaning and feature engineering
    ↓
Gold star schema (dimensions + fact table)
    ├── EDA and Power BI reporting
    └── ML training → prediction dashboard
```

> The project calls the target `AQI` for continuity with the original submission. It is a composite score derived from normalized pollutant measurements, not an official regulatory AQI unless the calculation is separately mapped to a recognized standard.

## Repository layout

```text
.
├── Medilian&EDA/
│   ├── bronze_layer.py
│   ├── silver_layer.py
│   ├── gold_layer.py
│   ├── EDA.py
│   ├── waqi-covid19-airqualitydata-2023Q4-1.csv
│   ├── bronze_output.csv
│   ├── silver_layer.csv
│   └── gold_layer/                 # generated Gold outputs
├── Ai model/
│   ├── model_training.py
│   ├── predict.py
│   ├── data/silver_layer.csv
│   ├── models/                     # committed model artifacts
│   ├── outputs/                    # charts and dashboard artifacts
│   └── src/dashboard.py
├── Power bi/                       # Power BI report and screenshots
├── Presentation & Documentation/   # project deliverables
├── Figma/                          # design references
├── requirements.txt
└── .gitignore
```

## Setup

Python 3.10 or newer is recommended.

```bash
git clone https://github.com/OmarFathy2024/DEPI-final-project-Global-Air-Quality.git
cd DEPI-final-project-Global-Air-Quality
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Run the pipeline

All scripts resolve their files relative to their own locations, so these commands work from the repository root or from another current directory.

```bash
python "Medilian&EDA/bronze_layer.py"
python "Medilian&EDA/silver_layer.py"
python "Medilian&EDA/gold_layer.py"
python "Medilian&EDA/EDA.py"
```

The Gold script writes the canonical star-schema files to `Medilian&EDA/gold_layer/`:

- `dim_location.csv`
- `dim_date.csv`
- `fact_airquality_weather.csv`

`EDA.py` reads those exact files. The generated Gold directory is ignored by Git because it is reproducible from the Silver layer.

## Train and run the model

The model uses the committed Silver dataset at `Ai model/data/silver_layer.csv` and writes artifacts to `Ai model/models/` and `Ai model/outputs/`.

```bash
python "Ai model/model_training.py"
python "Ai model/predict.py" --no-dashboard
```

For a custom input CSV:

```bash
python "Ai model/predict.py" --input path/to/input.csv --no-dashboard
```

Predictions are saved to `Ai model/outputs/predictions.csv`. Omit `--no-dashboard` to generate the HTML dashboard as well.

## Reported model results

The committed model metadata reports the following historical holdout results:

- Model: tuned LightGBM regressor
- MAE: 0.233
- RMSE: 0.418
- R²: 0.885

These metrics were produced from the model artifact currently committed to the repository. Retraining may produce different values when dependencies or input data change. The project currently uses a random train/test split; a chronological and location-aware evaluation is a planned improvement.

## Data and portfolio notes

The repository includes the original project deliverables, dashboard screenshots, model artifacts, and generated visualizations for portfolio review. Large binary deliverables are retained because they are part of the graduation-project presentation. Do not add credentials, `.env` files, local caches, or untrusted pickle/joblib files.

For the original project context and visual deliverables, see `Ai model/README.md`, `Power bi/`, and `Presentation & Documentation/`.

## Future improvements

- Add schema and data-quality tests.
- Add chronological and location-aware model validation.
- Document the data source, license, and composite AQI formula.
- Add lightweight GitHub Actions checks.
- Separate source code, notebooks, data, models, and reports in a later reviewed refactor.

## License

This project is intended for educational and portfolio use. Add an explicit license before redistributing the code or data.