# PioReactor OD Calculator & Corrector

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JoeVPhD/pioreactor-od-calculator/blob/main/PioReactior_OD-Calculator-and-Corrector.ipynb)

A Jupyter notebook for loading, plotting, normalizing, and correcting **optical density (OD) readings** from [PioReactor](https://pioreactor.com/) fermentation experiments.

---

## Features

- 📂 **Load CSV data** from PioReactor readings (auto-detects local vs. Google Colab environment)
- 📊 **Plot OD vs. time** — individual unit subplots and all-units overlay
- 🔧 **Optional SMoothing** to remove sawtooth Pioractor sampling
- 📐 **Multiple normalization methods**:
  - `od_norm_t0` — divide by first OD value
  - `od_delta_t0` — subtract first OD value
  - `od_minmax` — rescale between 0 and 1
- 📈 **OD Doubling Time and Growth Rate calculator** — robust smoothing + sliding window linear regression on log-transformed OD, reporting growth rate *r* (h⁻¹), doubling time *T*d (h), and *R*²
- 💾 **Auto-saves all figures** next to the source CSV file

---

## Quick Start

### Option 1: Google Colab (no install needed)

Click the **Open in Colab** badge above. When prompted, upload your PioReactor CSV file.  
You can use the example datasets in `example_data/` to try it immediately.

### Option 2: Local Jupyter

```bash
git clone https://github.com/JoeVPhD/pioreactor-od-calculator.git
cd pioreactor-od-calculator
pip install -r requirements.txt
jupyter notebook PioReactior_OD-Calculator-and-Corrector.ipynb
```

---

## Example Data

Two real datasets are included in `example_data/` (downsampled to every 10th point for size):

| File | Experiment | Rows |
|------|------------|------|
| `od_readings-JUNE262026-all_units-20260424233439.csv` | JUNE262026 | ~40k |
| `od_readings-JUNE172026-all_units-20251004012028.csv` | JUNE172026 | ~47k |

These are standard PioReactor exports and work as drop-in test files.

---

## Input Format

The notebook expects a CSV with at least these columns (standard PioReactor export format):

| Column | Description |
|--------|-------------|
| `experiment` | Experiment name/ID |
| `pioreactor_unit` | Unit name (e.g., `pioreactor01`) |
| `timestamp` | UTC timestamp of the reading |
| `od_reading` | Raw OD value |
| `angle` | Measurement angle |
| `channel` | Measurement channel |
| `timestamp_localtime` | Local timestamp |
| `hours_since_experiment_created` | Time since experiment start (h) |

---

## Requirements

See `requirements.txt`. Key dependencies:
- `pandas`
- `matplotlib`
- `seaborn`
- `scipy`
- `numpy`

---

## License

MIT License — free to use and modify for your experiments.
