# PoI Detection in the Enron Email Corpus - Feature Set Comparison

**Author:** Maren Tevasvold

## Contents

| File | Description |
|------|-------------|
| `Enron_PoI_Detection.ipynb` | The full experiment: data preparation, feature extraction, the three models, evaluation and graphs |
| `README.md` | This file |

The datasets are not included in this repository due to upload limits. The method to download them is explained in this file. 

## Requirements

- Python 3.12 (the notebook was run with Python 3.12.10)
- Jupyter with a Python 3.12 kernel
- Packages: `pandas`, `numpy`, `scikit-learn`, `matplotlib`
- A Kaggle account to download the datasets

## Setup

1. Download and install Python 3.12 from the official Python website:

https://www.python.org/downloads/

The notebook was tested with Python 3.12.10.

2. Download the Jupyter notebook  `Enron_PoI_Detection.ipynb`.
   
3. Create a Python 3.12 environment
   ```bash
   python3.12 -m venv .venv
   .venv\Scripts\activate   #macOS: source .venv/bin/activate
   ```
4. Install the required packages using pip:

```bash
pip install pandas numpy scikit-learn matplotlib
```
5. Register the environment as a Jupyter kernel
   ```bash
   python -m ipykernel install --user --name enron-poi --display-name "Python 3.12"
   ```

## Datasets

Both datasets are downloaded from Kaggle. The datasets need to be renamed for the notebook to find them, and they need to be accessible in the same folder as the notebook. 

| Dataset | Used for | Link |  Downloaded file | Rename to |
|---------|----------|------|-----------------|-----------|
| The Enron Email Dataset Parsed (acsariyildiz) | Email headers and bodies | https://www.kaggle.com/datasets/acsariyildiz/the-enron-email-dataset-parsed | `archive/enron_mails.csv` | `enron_mails.csv` |
| Enron Person of Interest Dataset (sagarnildass) | Email addresses and PoI labels | https://www.kaggle.com/datasets/sagarnildass/enron-person-of-interest-dataset/data?select=final_project_dataset.pkl | `final_project_dataset.pkl` | `poi_dataset.pkl` |

The folder should then look like this:

```
├── Enron_PoI_Detection.ipynb
├── enron_mails.csv
├── poi_dataset.pkl
```
## Running the experiment

1. Open the notebook and select the Python 3.12 kernel.
3. Run all cells from the top (Run All).

The notebook runs in this order: load and combine the datasets, build the metadata and text features, create the 10 train/evaluation splits, train and evaluate the three models and plot the results.

## Expected results

With the settings in the notebook, the mean over the 10 splits should be:

| Model | ROC-AUC | Average precision | Precision top 10 | Recall top 10 |
|-------|---------|-------------------|------------------|---------------|
| Combined | 0.514 | 0.427 | 0.41 | 0.273 |
| Metadata | 0.458 | 0.457 | 0.34 | 0.227 |
| Text | 0.545 | 0.440 | 0.34 | 0.227 |
