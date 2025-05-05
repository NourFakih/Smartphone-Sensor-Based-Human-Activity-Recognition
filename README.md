# Smartphone-Sensor-Based-Human-Activity-Recognition
Here’s a complete and clear README.md draft for your GitHub repository based on your image and details:

---

# Human Activity Recognition with Feature Engineering and Deep Fusion

## 📌 Motivation

Human Activity Recognition (HAR) plays a crucial role in health monitoring, fitness tracking, and context-aware systems. While recent deep learning techniques offer powerful representation learning, traditional handcrafted features combined with classical ML models still dominate on small-to-moderate datasets. This project explores the performance gap between engineered features and deep end-to-end models on the popular UCI HAR dataset.

---

## 🗂️ Repository Structure

This repository contains three main notebooks:

1. **FeatureEngineering+model.ipynb**
   Applies a full feature engineering pipeline to compress the original 561 sensor-derived features down to a compact and highly informative 100-feature representation. The following 10 machine learning and deep learning pipelines were trained and evaluated on these features:

   * XGBoost (best overall performance: 99.2% accuracy)
   * Random Forest
   * K-Nearest Neighbors
   * Logistic Regression
   * Support Vector Machine (RBF kernel)
   * LSTM
   * Transformer (self-attention)
   * PINN (Physics-Informed Neural Network)
   * VAE (Variational Autoencoder + classifier)
   * MLP (Multilayer Perceptron)

   These pipelines cover traditional ensemble learning, classical baselines, and deep-learning-based representations. The feature engineering process included duplicate removal, variance thresholding, multicollinearity filtering, and ANOVA-based selection.

2. **NOFeatureEngineering+model.ipynb**
   Mirrors the structure of the above notebook but skips all feature engineering. Instead, all original 561 features are fed directly into the same 10 pipelines, allowing a direct comparison between full raw features vs. distilled ones.

3. **FFt+models\_(3).ipynb**
   Explores the use of FFT-transformed raw inertial signals as input for deep learning models, particularly MLPs. While results from this FFT pipeline (e.g., \~95% accuracy with MLP) were not included in the final paper to maintain clarity in comparison, they validate that frequency-domain features can still support strong model performance and reaffirm the trajectory of our analysis.

---

## 📝 Project Summary

We began with the UCI HAR dataset containing 561 precomputed time and frequency-domain features. After pruning and filtering via a multi-step feature engineering process, we obtained a compact 100-dimensional vector per instance. XGBoost applied to this vector achieved a test accuracy of 99.2% and macro-F1 score of 0.992—outperforming all deep-learning-based fusion models.

Though LSTM and MLPs trained on these same features approached high performance (e.g., LSTM at 98.9%), end-to-end architectures like Transformer, PINN, and VAE plateaued in the low- to mid-90% range. This suggests that for medium-sized datasets like UCI HAR, hand-crafted signal processing still offers superior generalization, especially in out-of-distribution settings, such as new-user testing.

The results and detailed analysis are discussed extensively in our accompanying report.

---

## 📚 Citation

If you use this repository or the dataset, please cite:

```bibtex
@misc{reyes2013har,
  author       = {Reyes-Ortiz, Jorge and Anguita, Davide and Ghio, Alessandro and Oneto, Luca and Parra, Xavier},
  title        = {Human Activity Recognition Using Smartphones [Dataset]},
  year         = {2013},
  publisher    = {UCI Machine Learning Repository},
  howpublished = {\url{https://doi.org/10.24432/C54S4K}},
  note         = {Accessed: 2025-05-04}
}
```

---

Let me know if you want a version with markdown formatting, or a shorter version for the GitHub preview.
