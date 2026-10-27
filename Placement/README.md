# Student Placement Prediction

This project explores whether a student is placed using their CGPA and IQ. It
uses a small dataset and a logistic regression classifier, with the workflow
documented in the Jupyter notebook.

## Project files

- `Placement.ipynb` — data inspection, preprocessing, visualization, model
  training, and evaluation.
- `placement-dataset.xls` — the dataset. Despite the extension, this file
  contains comma-separated (CSV) text.
- `model.pkl` — a pickle of the trained logistic regression classifier.

## Dataset

The dataset contains 100 student records with these columns:

| Column | Description |
| --- | --- |
| `city` | Student's city; removed before training |
| `cgpa` | Student's CGPA |
| `iq` | Student's IQ score |
| `placement` | Target label: `1` for placed, `0` for not placed |

Missing `cgpa` and `iq` values are filled with their respective medians. The
model uses `cgpa` and `iq` as input features.

## Run the notebook

1. Install Python and Jupyter, then install the notebook dependencies:

   ```bash
   python -m pip install numpy pandas scikit-learn matplotlib mlxtend jupyter
   ```

2. Open this folder as the working directory in Jupyter:

   ```bash
   jupyter notebook Placement.ipynb
   ```

3. Before running the notebook, make the dataset filename match the path in
   its loading cell. The notebook reads `placement-dataset.csv`, while the
   checked-in file is named `placement-dataset.xls`. Since the file is CSV
   text, either rename it to `placement-dataset.csv` or update the notebook
   to read `placement-dataset.xls` with `pandas.read_csv`.

4. Run the cells from top to bottom. The notebook splits the data into
   training and test sets, scales the features, fits logistic regression,
   evaluates accuracy, and saves `model.pkl` in the working directory.

## Notes on results and the saved model

The notebook currently displays an accuracy of `0.90` for one 90/10
train/test split. The split has no fixed random seed, so results may vary.
Also, the notebook fits a separate scaler on the test data rather than
reusing the scaler fitted on the training data; treat the displayed score as
an exploratory result, not a reliable estimate of model performance.

`model.pkl` contains only the classifier, not the fitted `StandardScaler`.
The notebook's classifier expects scaled inputs, so the pickle alone is not
sufficient for consistent predictions on new raw CGPA and IQ values. For
reliable inference, save and reuse the training scaler (or save a
scikit-learn pipeline) along with the classifier.