# Spotter Assessment — Freight Rate Prediction

## How the setup has been done

1. Create a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Place the following data files in the project root the same folder as `Main.ipynb` and `Score.py`:
   - `train-test.csv`
   - `validation.csv`
   - `december-chart-inputs.csv`

## The run process

1. Open and run `Main.ipynb` top to bottom (Jupyter, JupyterLab, or Colab).
   This will:
   - Train a 5-fold LightGBM model on `train-test.csv`
   - Generate `validation_predictions.csv` the final prediction_rate from `validation.csv`
   - Fill in `december-chart-inputs.csv` with predicted rates
   - Call `Score.py` to validate both outputs and produce the December chart

2. Then after generating the two prediction CSVs from the notebook, run the scorer manually:
   ```
   python Score.py --predictions validation_predictions.csv --december-predictions december-chart-inputs.csv
   ```

## Outputs

- `validation_predictions.csv` — final predictions for the 12,000 validation loads (`load_id,predicted_rate`)
- `scorer_results/candidate_december.png` — December 2025 predicted rate chart
