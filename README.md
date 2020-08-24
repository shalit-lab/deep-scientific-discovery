![](https://img.shields.io/github/license/tom-beer/deep-scientific-discovery?color=magenta&style=plastic)

<img src="ECG/logo.png" width=125 height=125 align="right">

# Deep Scientific Discovery
This repository contains code for the paper [Using Deep Networks for Scientific Discovery in Physiological Signals](https://www.mlforhc.org/accepted-papers)

*Tom Beer, Bar Eini-Porat, Sebastian Goodfellow, Danny Eytan and Uri Shalit*

**Proceedings of Machine Learning for Healthcare, 2020**

Deep neural networks (DNN) have shown remarkable success in the classification of physiological signals. In this study we propose a novel method of “removing” known, hand-engineered features from the network’s hypothesis space, thus forcing it to try learn representations which are different from known ones, as a method of scientific exploration. We then build on existing work in the field of interpretability, specifically class activation maps, to try infer what new features the network has learned.

By adding domain knowledge based feature sets to CNN’s latent representation layer, and imposing independence between the two, the network is encouraged to learn an orthogonal representation to the known domain knowledge. We do this by optimizing an objective that trades off classification performance with the statistical independence, as measured by the Hilbert Schmidt Independence Criterion (HSIC).

In order to test this approach two domains were selected : Arrhythmia detection in ECG signals, and REM-NREM classification in EEG signal. Both have been well studied, making good them benchmarks to test our framework.

Full paper is avilable [Here](https://static1.squarespace.com/static/59d5ac1780bd5ef9c396eda6/t/5f22cc45a1025d04faaf5b7c/1596116059099/126_CameraReadySubmission_Deep_networks_for_scientific_discovery_in_physiological_signals+%281%29.pdf)

### To apply the method on your task
Integrate `HSICClassifier` from `networks.py` and `HSICLoss` from `hsic.py` in your classification task

### ❤️ To run the ECG experiments
1. Download and preprocess the PhysioNet 2017 data by running
    ```python
    python -m ECG.prepare_dataset
    ```
2. Train the main task
    ```python
    python -m ECG.train_main_task
    ```
    
3. To evaluate model validity, you may want to run
    ```python
    python -m ECG.train_independence
    python -m ECG.train_rep2label
    ```
4. To visualize the obtained activations:
    ```python
    python -m ECG.visualize_cam
    ```
    
### 🧠 To run the EEG experiments
Follow the same steps as in the ECG experiment above, replacing `ECG` with `EEG`

----

**logo created by [Atif Arshad](https://thenounproject.com/search/?q=ecg&i=1295489) from the Noun Project
