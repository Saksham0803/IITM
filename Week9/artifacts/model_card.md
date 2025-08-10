# Model Card — Iris Classifier

## Overview
- Task: Multiclass classification (setosa, versicolor, virginica)
- Data: Iris dataset with synthetic sensitive attribute 'location' in {0,1} added at random for fairness auditing.
- Models compared: baseline (excludes location), with_location (includes location).

## Metrics (test split)
```
{
  "baseline": {
    "accuracy": 0.8947368421052632,
    "fairness": {
      "by_group": {
        "selection_rate": {
          "0": 0.3333333333333333,
          "1": 0.25
        },
        "tpr": {
          "0": 0.75,
          "1": 0.8
        },
        "fpr": {
          "0": 0.0,
          "1": 0.06666666666666667
        }
      },
      "dp_diff": 0.08333333333333331,
      "eo_diff": 0.06666666666666667
    }
  },
  "with_location": {
    "accuracy": 0.9473684210526315,
    "fairness": {
      "by_group": {
        "selection_rate": {
          "0": 0.4444444444444444,
          "1": 0.25
        },
        "tpr": {
          "0": 1.0,
          "1": 0.8
        },
        "fpr": {
          "0": 0.0,
          "1": 0.06666666666666667
        }
      },
      "dp_diff": 0.19444444444444442,
      "eo_diff": 0.19999999999999996
    }
  }
}
```

## Fairness
- Sensitive attribute: location (synthetic). Reported for class 'virginica' via one-vs-rest: selection rate, TPR, FPR, demographic parity difference, equalized odds difference.

## Explainability
- Global: SHAP beeswarm and mean |SHAP| plots for 'virginica'. Local: LIME example (if installed).

## Drift
- Simple PSI and K-S checks between train and test; in production compare train vs recent production windows and alert on thresholds (e.g., PSI > 0.25).

## Limitations
- Small dataset; fairness gaps may be unstable. 'location' is random; threshold=0.5 chosen for demo.