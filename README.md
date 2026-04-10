# Project 1: Time-Series — ICU Mortality Prediction

Intensive Care Time Series Modeling for Mortality Predictions on the Physionet 2012 Challenge Dataset.

## Environment

### Local Setup

Python 3.12 is required. Install dependencies into a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## How to Run

Run the notebooks in order:

| Notebook | Question | Content |
|---|---|---|
| `exercise_1.ipynb` | Q1 | Data loading and preprocessing |
| `exercise_2.ipynb` | Q2 | Supervised learning (LR, GBT, LSTM, Transformer) |
| `exercise_3.ipynb` | Q3 | Representation learning (LSTM autoencoder, linear probes, label scarcity, visualisation) |
| `exercise_4.1.ipynb` | Q4.1 | Foundation models — part 1 |
| `exercise_4.2_and_4.3.ipynb` | Q4.2 & Q4.3 | Foundation models — parts 2 and 3 |

`exercise_1.ipynb` (Q1) must be run first as it generates the `processed/` parquet files that all subsequent notebooks depend on.

## Processed Data

Preprocessed parquet files are stored in `processed/`:
- `set_a_processed.parquet` — training set (imputed, scaled, time-gridded)
- `set_b_processed.parquet` — validation set
- `set_c_processed.parquet` — test set

The raw sets (`set_a.parquet`, `set_b.parquet`, `set_c.parquet`) contain the data before imputation and scaling, used for computing standard deviation features.

## Saved Models

- `lstm_autoencoder.pt` — pretrained LSTM autoencoder weights (saved after Q3.1 pretraining)
- `lstm_contrastive.pt` — pretrained LSTM contrastive model weights (saved after Q3 contrastive pretraining)
