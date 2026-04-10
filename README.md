# Project 1: Time-Series — ICU Mortality Prediction

Intensive Care Time Series Modeling for Mortality Predictions on the Physionet 2012 Challenge Dataset.

## Environment

### On the ETH Student Cluster

The data is already available on the cluster at `~/ml4h_data/p1/*`. No download needed.

The cluster provides a pre-configured Python environment. Open a terminal in Jupyter and activate it:

```bash
conda activate ml4h
```

Then launch Jupyter and open the notebooks directly.

### Local Setup

Python 3.12 is required. Install dependencies into a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Data

The Physionet 2012 Challenge dataset is split into three sets:
- **Set A** (`set-a/`) — training
- **Set B** (`set-b/`) — validation (hyperparameter tuning)
- **Set C** (`set-c/`) — test (final evaluation only)

Raw outcome labels are in `Outcomes-{a,b,c}.txt`.

## How to Run

Run the notebooks in order:

| Notebook | Content |
|---|---|
| `exercise_2.ipynb` | Data preprocessing, supervised learning (LR, GBT, LSTM, Transformer) |
| `exercise_3.ipynb` | Representation learning (LSTM autoencoder, linear probes, label scarcity, visualisation) |
| `exercise_4.ipynb` | Foundation models (LLM prompting, LLM embeddings, Chronos) |

Preprocessing (Q1) must be run first as it generates the `processed/` parquet files that all subsequent notebooks depend on.

## Processed Data

Preprocessed parquet files are stored in `processed/`:
- `set_a_processed.parquet` — training set (imputed, scaled, time-gridded)
- `set_b_processed.parquet` — validation set
- `set_c_processed.parquet` — test set

The raw sets (`set_a.parquet`, `set_b.parquet`, `set_c.parquet`) contain the data before imputation and scaling, used for computing standard deviation features.

## Saved Models

- `lstm_autoencoder.pt` — pretrained LSTM autoencoder weights (saved after Q3.1 pretraining)
