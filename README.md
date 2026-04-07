# KNN Sport Classifier — Machine Learning Session

A beginner-friendly machine learning project built for a teaching session on **K-Nearest Neighbors (KNN)** classification using Python and scikit-learn. The dataset classifies athletes into sport categories based on their height and weight.

---

## Project structure

```
├── knn_sport_dataset.xlsx      # Generated dataset (200 samples, 5 sports)
├── knn_200_simple.py           # Simple KNN model on the 200-sample dataset
├── knn_sport_classifier.py     # Full KNN pipeline with elbow method & plots
├── knn_plots.py                # Matplotlib visualisations (boundary, neighbors)
├── knn_sport_results.png       # Output plot from the full classifier
└── README.md
```

---

## Dataset

The dataset contains **200 athletes** across **5 sports**, generated with realistic physical profiles:

| Sport         | Avg Height | Avg Weight | Samples |
|---------------|-----------|-----------|---------|
| Basketball    | ~185 cm   | ~88 kg    | 40      |
| Gymnastics    | ~158 cm   | ~52 kg    | 40      |
| Rugby         | ~182 cm   | ~98 kg    | 40      |
| Swimming      | ~178 cm   | ~74 kg    | 40      |
| Weightlifting | ~170 cm   | ~105 kg   | 40      |

Features: `height_cm`, `weight_kg`  
Target: `sport` (5 classes)

---

## Quickstart

### 1. Install dependencies

```bash
pip install pandas scikit-learn matplotlib openpyxl
```

### 2. Run the simple model

```bash
python knn_200_simple.py
```

### 3. Run the full pipeline with plots

```bash
python knn_sport_classifier.py
```

---

## How KNN works

KNN is a **lazy learner** — it stores all training data and makes predictions at runtime by:

1. Computing the distance from the new point to every training point
2. Selecting the **K nearest neighbors**
3. Taking a **majority vote** of their labels
4. Assigning the winning label to the new point

```
distance(A, B) = sqrt((x1-x2)² + (y1-y2)²)
```

### Choosing K

- **Small K** (e.g. K=1) → low bias, high variance → tends to overfit
- **Large K** (e.g. K=N) → high bias, low variance → tends to underfit
- Good starting point: `K = sqrt(n_samples)`
- Use **cross-validation** to find the optimal K (see `knn_sport_classifier.py`)

> **Note:** K has nothing to do with the number of classes. With 5 sports, you do *not* automatically set K=5.

---

## Key concepts covered

- Train/test split with `train_test_split`
- Feature scaling with `StandardScaler` and why it matters for KNN
- Evaluating a model with `accuracy_score` and `classification_report`
- Visualising decision boundaries with `matplotlib`
- Finding the best K using the elbow method and cross-validation
- Predicting new data points

---

## Results (no scaling)

Without `StandardScaler`, the 200-sample model achieves ~65–75% accuracy depending on K. Gymnastics consistently reaches 100% precision because small + light athletes are uniquely separable. Basketball and Rugby overlap the most in raw height/weight space.

---

## Requirements

- Python 3.8+
- pandas
- scikit-learn
- matplotlib
- openpyxl

---

## Session notes

This project was built as a teaching resource for an introductory ML session covering:
- Linear Regression
- K-Nearest Neighbors Classifier

The simple 8-sample example (`knn_200_simple.py`) is intentionally kept to 7 lines of logic so students can follow along line by line. The full pipeline (`knn_sport_classifier.py`) shows a production-style workflow with hyperparameter tuning and visualisations.
