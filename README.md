# Development-of-Machine-Learning-Algorithms-for-Atrial-Fibrillation-Detection-
Development of Machine Learning Algorithms for Atrial Fibrillation Detection Using Heart Rate Variability Time Series

Atrial Fibrillation Detection Using Machine Learning and Heart Rate Variability
Bachelor's Thesis | Biomedical Signal Analysis · Heart Rate Variability · Machine Learning
Author: Biagio Chiarandà
Degree: Bachelor's Degree in Computer Science for Digital Communication
University: University of Milan (Università degli Studi di Milano)
Department: Department of Computer Science “Giovanni degli Antoni”
Academic Year: 2023–2024
Supervisor: Prof. Massimo Walter Rivolta
Co-supervisors: Prof. Roberto Sassi and Md Moklesur Rahman
Academic research disclaimer: This work explores automated atrial fibrillation detection for research and educational purposes. It is not a clinically validated diagnostic system and should not be used for medical decisions.

Overview
Atrial fibrillation (AF) is a common cardiac arrhythmia characterized by disorganized atrial electrical activity and irregular heartbeat intervals. Early identification is important because AF is associated with serious cardiovascular complications, including an increased risk of stroke.

This bachelor's thesis investigates the application of supervised machine learning to distinguish atrial fibrillation from normal sinus rhythm by analyzing electrocardiogram (ECG) recordings and extracting quantitative features from heart rate variability (HRV) time series.

The research combines biomedical signal processing, statistical feature extraction, and comparative model evaluation, with particular attention to the ability of classification models to generalize across independent ECG datasets.
Thesis and presentation
This repository is a documentation-focused archive of the graduation research, containing the full thesis and the accompanying presentation. It is intended to share the research questions, scientific methodology, experimental outcomes, and conclusions.
Document	Description
Bachelor's thesis	Complete dissertation in Italian, covering the literature review, datasets, methods, experiments, results, and future work.
Thesis presentation	Slide deck summarizing the research motivation, proposed approach, main findings, and conclusions.


Note: Document filenames and links can be added to this section once the thesis and presentation have been uploaded to the repository.

Research objectives
The main objective is to evaluate whether HRV characteristics derived from ECG signals can reliably support automated classification of atrial fibrillation.

Specifically, the work aims to:
- Analyze ECG signals from two publicly available biomedical datasets.
- Identify cardiac R-peaks and calculate successive RR intervals.
- Extract interpretable features describing rhythm variability and complexity.
- Compare four supervised machine learning classifiers.
- Evaluate performance both within individual datasets and across different datasets.
- Examine classification errors and the limitations of the experimental approach.
Datasets
Two open research datasets hosted on PhysioNet were used in the study.
Dataset	Description	Sampling frequency
PhysioNet / Computing in Cardiology Challenge 2017	Short, single-lead ECG recordings with labels including normal rhythm, atrial fibrillation, other rhythms, and noisy recordings.	300 Hz
MIT-BIH Atrial Fibrillation Database (AFDB)	Long-duration ECG recordings with rhythm and beat annotations, including episodes of atrial fibrillation and normal rhythm.	250 Hz


The thesis focuses on the binary classification of AF versus normal rhythm, rather than classifying every rhythm category available in the original datasets. The original recordings remain available from their respective PhysioNet sources.
Methodology
1. ECG signal preprocessing
ECG recordings were prepared using different steps to reduce noise and make recordings suitable for feature extraction:
- Min–max normalization to address differences in signal amplitude.
- Band-pass filtering from 0.5 to 40 Hz to attenuate baseline drift and high-frequency noise.
- QRS-focused filtering from 5 to 15 Hz to emphasize the signal components needed for beat detection.
- Signal segmentation, adapted to each dataset: approximately 10-second windows for Challenge 2017 and annotated rhythm episodes for AFDB.
2. R-peak detection and RR intervals
The analysis identifies R-peaks in the ECG recordings. The intervals between consecutive R-peaks are then used to characterize cardiac rhythm variability:

\(RR_i = t_{R_{i+1}} - t_{R_i}\)

These RR intervals form the basis of the HRV feature analysis.
3. Heart rate variability features
The thesis examines three families of descriptors:
Feature family	Measurements	Purpose
Time-domain features	Heart Rate (HR), Mean RR, STD RR, RMSSD	Describe heart rate and beat-to-beat variability.
Nonlinear features	Poincaré SD1, Sample Entropy, Approximate Entropy	Characterize rhythm irregularity and complexity.
PRSA-derived features	Acceleration Capacity (AC), Deceleration Capacity (DC), Deceleration Reserve (DR)	Describe acceleration and deceleration patterns in heart rhythm.


A particular focus is placed on Phase-Rectified Signal Averaging (PRSA), used to derive acceleration and deceleration measurements from RR interval sequences.
4. Classification models
Four supervised machine learning approaches were investigated:
1. Random Forest
2. Support Vector Machine (SVM)
3. Gradient Boosting Classifier
4. k-Nearest Neighbors (KNN)
The thesis compares their strengths and weaknesses using standard classification metrics, including accuracy, precision, recall, specificity, F1-score, and confusion matrices.
Experimental evaluation
The study considers three experimental scenarios:
Experiment	Evaluation setting	Research question
1 — Challenge 2017	Training and testing with samples from the Challenge 2017 dataset.	How well do the models classify held-out ECG samples from the same dataset?
2 — MIT-BIH AFDB	Training and testing with samples from AFDB.	How do the models perform with longer, annotated recordings?
3 — Cross-dataset evaluation	Training on Challenge 2017 and evaluation on AFDB.	How effectively do the learned patterns generalize to an independent ECG dataset?


The cross-dataset experiment is especially relevant because the datasets differ in recording length, sampling frequency, and acquisition characteristics.
Key findings
Model performance
The thesis reports the following outcomes for Random Forest:
Experimental setting	Reported accuracy
Challenge 2017	Approximately 79%
MIT-BIH AFDB	Approximately 96%
Cross-dataset evaluation	79.09%


The cross-dataset Random Forest result also includes a reported F1-score of 78.1%.

Random Forest was identified as a strong and comparatively consistent approach in the overall analysis, although KNN achieved the highest accuracy in the smaller within-AFDB experiment. These outcomes depend on the evaluation setting and should not be interpreted as clinical performance guarantees.
Feature relevance
The analysis highlights the relevance of Deceleration Capacity (DC), STD RR, and Sample Entropy for distinguishing irregular rhythm patterns. These findings illustrate the potential of combining conventional HRV descriptors with nonlinear and PRSA-derived metrics.
Generalization and errors
The results show why testing on an independent dataset is important. Differences in ECG recording characteristics, rhythm episode duration, and feature distributions can affect classification accuracy. In particular, false negatives deserve careful attention when interpreting AF detection results.
Limitations
As discussed in the thesis, the study has several limitations:
- The classification problem focuses on AF and normal rhythm, not all arrhythmias.
- The two datasets differ in acquisition settings, recording duration, and annotation structure.
- Noise or errors in R-peak identification may affect the extracted HRV features.
- Some experimental subsets are relatively small, limiting the strength of performance conclusions.
- Good results on these datasets do not establish reliability on new patients, devices, or clinical environments.
- Independent clinical validation is necessary before any practical diagnostic application.
Future research directions
The thesis identifies several possible extensions:
- Multiclass classification of additional cardiac rhythms and arrhythmias.
- Deep learning models, including architectures capable of learning patterns directly from ECG recordings.
- Explainable AI (XAI) techniques for improved interpretation of model predictions.
- External and clinical validation on additional populations and datasets.
- Further investigation of normalization and signal segment length.
- Exploration of real-time applications on wearable devices.
Original thesis title
Italian: Sviluppo di algoritmi di Machine Learning per l'identificazione della fibrillazione atriale a partire da serie temporali di variabilità cardiaca

English: Development of Machine Learning Algorithms for Atrial Fibrillation Detection Using Heart Rate Variability Time Series

Bachelor's thesis, University of Milan, Academic Year 2023–2024.
References and acknowledgments
- PhysioNet
- PhysioNet / Computing in Cardiology Challenge 2017
- MIT-BIH Atrial Fibrillation Database
I would like to acknowledge Prof. Massimo Walter Rivolta, Prof. Roberto Sassi, and Md Moklesur Rahman for their academic supervision and guidance.

For additional scientific references and methodological details, please consult the bibliography and full discussion in the thesis.
Citation and usage
If this research is relevant to your academic work, please cite the thesis and acknowledge the original PhysioNet datasets and their contributors. Third-party materials and figures may have separate terms of use; consult their original sources before reuse.
Medical disclaimer: This repository presents a university research project, not a medical product. The reported models and findings must not be used to diagnose, screen, or treat patients.

Biagio Chiarandà · University of Milan · Bachelor's Thesis, 2023–2024
