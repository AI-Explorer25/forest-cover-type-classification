# Forest Cover Type Classification

## Project Overview

This project builds a machine learning model to classify forest cover types using environmental and geographic data. The goal is to predict the correct cover type based on terrain, hydrology, and soil characteristics.

The dataset contains 581,012 observations and 54 features, including:

- Elevation, slope, and hillshade measurements  
- Distance to hydrology, roads, and fire points  
- One-hot encoded wilderness areas and soil types  

The target variable is **class**, representing one of seven forest cover types.

This project demonstrates the full machine learning workflow: data exploration, preprocessing, model development, experimentation with different architectures, evaluation, and interpretation.

---

## Dataset

The dataset used is the **Forest Cover Type dataset**, originally collected by the U.S. Forest Service from the Roosevelt National Forest in Colorado.

Key characteristics:

- **581,012 samples**
- **54 input features**
- **7 target classes**
- **Imbalanced class distribution**, with two dominant classes and several minority classes

This imbalance adds additional complexity to the classification task.

---

## Methodology

### 1. Data Preparation

- Train/validation/test split  
- Feature preprocessing  
- One-hot encoding for target labels  
- Stratified sampling to preserve class distribution  

### 2. Model Development

Several neural network architectures were tested using TensorFlow/Keras.

**Baseline model**
- Dense layers: 128 → 64 → 7  
- Adam optimizer  
- Early stopping  

**Final model (best performing)**
- Dense layers: 128 → 80 → 7  
- Dropout regularisation  
- Reduced learning rate  
- Learning rate scheduling and early stopping  

**Experimental models**
- Larger networks (256 → 128 → 64)  
- Wider GELU networks (512 → 256 → 128)  
- Different dropout rates and batch sizes  

---

## Model Performance

Final evaluation on the held-out test set:

- **Test Accuracy:** 0.8962  
- **Test Loss:** 0.2582  
- **Weighted F1 Score:** ~0.90  

**Performance observations:**

- Classes **1, 2, 3, and 7** were predicted very reliably.  
- Classes **4, 5, and 6** were more difficult due to overlapping environmental characteristics.  
- Less frequent classes showed lower recall due to dataset imbalance.

---

## Model Comparison Insights

Key findings from experimentation:

- **Simpler architectures performed best.**  
  Moderate network depth with careful tuning produced stronger results than very large networks.

- **Increasing complexity did not improve generalisation.**  
  Larger models added parameters without meaningful performance gains.

- **Regularisation and learning rate tuning were important.**  
  Small dropout layers and a reduced learning rate improved training stability and generalisation.

---

## Visualisations

The notebook includes several visualisations to analyse model behaviour:

**Per-Class F1 Score Chart**  
Shows the relative performance across all classes.

**Normalized Confusion Matrix**  
Highlights which classes are most commonly confused.

**Training vs Validation Curves**  
Illustrate model convergence and confirm that major overfitting is not present.

---

## Potential Improvements

Future work could include:

- Feature engineering or interaction features  
- Class balancing techniques or weighted loss functions  
- Ensemble methods combining neural networks and tree-based models  
- Further hyperparameter optimisation  

---

## Conclusion

The final model achieves approximately **89.6% accuracy** on a challenging multi-class classification problem. Results show that moderate model complexity with careful tuning can outperform larger architectures. The project highlights the importance of iterative experimentation, proper evaluation, and understanding how dataset characteristics such as class imbalance influence model performance.

Overall, this project provides a practical example of an end-to-end machine learning workflow, from data preparation to model analysis and interpretation.

### Project Structure
```text
├── data/  
│   └── cover_data_raw.csv  # Raw dataset  
├── notebook/  
│   └── 01_forest_cover_classification.ipynb  # Main analysis notebook  
├── .gitignore  # Ignored files (e.g., checkpoints)  
├── README.md  # Project documentation
