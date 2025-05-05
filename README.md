# Smartphone-Sensor-Based-Human-Activity-Recognition

## Human Activity Recognition with Feature Engineering and Deep Fusion

## 📌 Motivation

Human Activity Recognition (HAR) using wearable sensors is a critical component in various applications, from health monitoring to smart environments. While deep learning has gained attention for its representation power, classical machine learning pipelines—especially when powered by strong signal processing and feature engineering—can still outperform deep models on moderately sized datasets. This project investigates the performance trade-off between handcrafted feature pipelines and deep neural models using the UCI HAR dataset.

---

## 🗂️ Repository Contents

This repository includes three Jupyter notebooks:

1. 📘 **FeatureEngineering+model.ipynb**
   This notebook implements a complete feature engineering pipeline to reduce the original 561 features to a compact set of 100 features. The following 10 pipelines were trained and evaluated on these features:

   * ✅ Decision Tree – 100.0%
   * ✅ XGBoost (Full) – 100.0%
   * ✅ Linear SVC on PCA Features – 93.8%
   * ✅ Linear SVC on Time-Domain Only – 93.6%
   * ✅ Linear SVC on Frequency-Domain Only – 83.4%
   * ✅ LSTM Classifier – 99.86%
   * ✅ Physics-Informed LSTM (PINN) – 84.76%
   * ✅ Transformer Encoder – 93.72%
   * ✅ Autoregressive (AR) + SVM – 93.0%
   * ✅ Variational Autoencoder (VAE) + SVM – 66.0%

   Feature engineering steps include duplicate feature removal, variance thresholding, multicollinearity filtering using Pearson correlation, and selection of the top 100 features via ANOVA F-statistics.

2. 📘 **NOFeatureEngineering+model.ipynb**
   This notebook replicates the model training process using the complete unfiltered set of 561 features. It enables side-by-side comparisons to evaluate the benefit of feature selection and dimensionality reduction. Here’s a summary of test performance for the same 10 models:

   * Decision Tree – 100.0%
   * XGBoost – 100.0%
   * Linear SVC on PCA Features – 96.2%
   * Linear SVC on Time-Domain Only – 96.1%
   * Linear SVC on Frequency-Domain Only – 93.8%
   * LSTM – 99.23%
   * PINN – 88.12%
   * Transformer – 93.72%
   * AR + SVM – 95.0%
   * VAE + SVM – 78.0%

   This notebook reveals that while raw features can support strong classifiers, reduced features yield models that are lighter and potentially more robust to noise or overfitting.

3. 📘 **FFt+models\_(3).ipynb**
   This notebook works directly with the raw 3D accelerometer and gyroscope signals, applying FFT-based feature extraction. It investigates MLP-based models on these frequency-domain representations. While the results (\~95% with MLP) are promising, they were not included in the formal paper to avoid overcrowding the comparison. Nevertheless, they reinforce the viability of using raw-to-FFT pipelines for HAR tasks.

---
> Several modeling ideas were adapted or extended from public Kaggle notebooks that inspired our pipelines \[1]\[2]\[3]\[4]. Their thoughtful analyses, modeling strategies, and clean implementation were instrumental in shaping the final structure of our experiments.

## 📝 Project Summary

We benchmarked classical and deep models using both engineered and unfiltered feature sets. Our experiments show that:

* Handcrafted features with XGBoost achieved the highest overall test accuracy (100%) and macro-F1 score (0.992).
* LSTM models benefited from expert features, scoring up to 99.86% with engineering vs. 99.23% without.
* Models like Transformer and PINN performed decently (84–94%) but were sensitive to input dimensionality and training volume.
* VAE-based pipelines lagged significantly, suggesting that reconstruction-driven representations may not align well with HAR classification goals.
* Frequency-only models underperformed compared to time-only and full models, but retained moderate predictive power (\~83–94%).

These findings align with the broader literature: on small-to-medium HAR datasets, classical pipelines with well-chosen features remain extremely competitive—even compared to modern neural models.

---

## 📚 Citation

If you use this dataset or replicate our pipelines, please cite:

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


## 📚 References

\[1] Morris B. (n.d.). What does your smartphone know about you? Kaggle. [https://www.kaggle.com/code/morrisb/what-does-your-smartphone-know-about-you/notebook](https://www.kaggle.com/code/morrisb/what-does-your-smartphone-know-about-you/notebook)
\[2] Chunduru P. (n.d.). SVM for Multiclass Classification. Kaggle. [https://www.kaggle.com/code/pranathichunduru/svm-for-multiclass-classification](https://www.kaggle.com/code/pranathichunduru/svm-for-multiclass-classification)
\[3] Mohamed E. (n.d.). Human Activity Recognition: Scientific Perspective. Kaggle. [https://www.kaggle.com/code/essammohamed4320/human-activity-recognition-scientific-prespective#Time-Domain](https://www.kaggle.com/code/essammohamed4320/human-activity-recognition-scientific-prespective#Time-Domain)
\[4] Meesala P. (n.d.). Human Activity Recognition - LSTM. Kaggle. [https://www.kaggle.com/code/prasadmeesala/human-activity-recognition-lstm](https://www.kaggle.com/code/prasadmeesala/human-activity-recognition-lstm)


---



