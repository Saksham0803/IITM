# Datasheet — Iris (with synthetic 'location')
## Composition
- Features: sepal_length, sepal_width, petal_length, petal_width; Label: species; Sensitive attribute: location in {0,1} (random).
## Collection
- Iris from scikit-learn or local iris.csv. location assigned at random with seed 42.
## Recommended Uses
- Fairness, explainability, drift demos.