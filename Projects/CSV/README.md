# CSV

This folder contains a Jupyter notebook demonstrating how to load tabular data with pandas, along with two datasets used by its examples.

## Contents

- `working_with_csv.ipynb` — demonstrates reading a local CSV, reading CSV data from a URL, setting a file separator and column names, choosing an index column, and selecting columns.
- `aug_train.csv` — candidate training data with columns for enrollee ID, city, experience, education, company details, training hours, and a target label.
- `movie_titles_metadata.tsv` — tab-separated movie metadata. This file has no header row; its columns are movie ID, title, release year, rating, vote count, and genres.

## Run the notebook

Install the notebook dependencies:

```bash
python -m pip install pandas requests jupyter
```

Start Jupyter from this folder so the notebook can find the local data files:

```bash
jupyter notebook working_with_csv.ipynb
```

The notebook's URL example also requests a sample countries CSV from the web, so an internet connection is needed to run that cell.
