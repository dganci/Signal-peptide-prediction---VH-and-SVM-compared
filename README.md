# Protein Motif Analysis and Classification #

## Overview ##
This repository contains Python code for analyzing protein sequences using bioinformatics 
techniques. The primary focus is on the analysis of signal peptide cleavage sites, amino acid 
frequency distributions, and the classification of proteins based on these features using 
machine learning algorithms, such as Support Vector Machine (SVM). The project explores both 
unsupervised and supervised learning approaches, including clustering techniques, sequence 
motif identification, and evaluation of classification performance.

## Table of Contents ##
Dependencies
Data Description
Analysis and Methods
Feature extraction
Motif analysis
Classification
Evaluation
Results

### Dependencies ###
The following Python libraries are used in this project:
```python
warnings
sys
requests
requests.adapters.HTTPAdapter
requests.adapters.Retry
json
re
pandas
numpy
seaborn
matplotlib.pyplot
itertools
collections.Counter
sklearn.svm
sklearn.preprocessing
sklearn.metrics.precision_recall_curve
sklearn.metrics.matthews_corrcoef
sklearn.metrics.accuracy_score
sklearn.metrics.f1_score
Bio.SeqUtils.ProtParam.ProteinAnalysis
Bio.SeqUtils.ProtParamData
```
### Data Description ###
The dataset consists of protein sequences and associated labels. The primary file 
pos+neg.fasta contains sequences for both positive and negative samples, where the goal is 
to predict the presence of a signal peptide cleavage site based on sequence features.

ID: Unique identifier for each protein sequence.
Sequence: The amino acid sequence of the protein.
Label: Class label (1 for positive, 0 for negative).

The sequence data is processed and analyzed to extract amino acid frequencies and other 
features relevant to signal peptide cleavage site prediction.

### Analysis and Methods ###
- Data Import: The data is loaded into a pandas DataFrame for manipulation and analysis. 
Proteins are classified into positive and negative categories.
- Sequence Processing: Each sequence is parsed to extract relevant features such as the first 90 amino acids, which are of particular interest in the context of signal peptide cleavage site prediction.

### Feature Extraction ###
The following features are extracted from the sequences:

  - Amino acid frequencies: the frequency of each amino acid in the first 90 residues of
    the sequence is calculated for different datasets.
  - Signal peptide cleavage sites: identification of regions that represent potential
    cleavage sites, with a focus on amino acid patterns and positions.
  
### Motif Analysis ### 
The von Heijne expected motif is computed and visualized in a motif logo.
This motif helps to identify conserved regions within the signal peptide sequences and
serves as a key feature for classification.

### Classification ###
The project utilizes a Support Vector Machine (SVM) to classify the
sequences based on the extracted features. Cross-validation and grid search are employed
to optimize the SVM hyperparameters (C and gamma).

### Evaluation ###
Model performance is evaluated using several metrics, including:

True positives (TP): Correctly predicted positive samples.
False positives (FP): Negative samples incorrectly predicted as positive.
True negatives (TN): Correctly predicted negative samples.
False negatives (FN): Positive samples incorrectly predicted as negative.
Additionally, false positive rates (FPR) are calculated for the SVM model and the von Heijne method, with a focus on sequences that contain helix motifs.

### Results ###
The results are presented through various visualizations:

- Amino acid frequency distributions: Bar plots comparing the frequency of each amino acid in 
the positive training set, SVM true positive (TP), and false negative (FN) sets.
- Box plots of feature distributions: Comparison of the distribution of features such as
- Max, Mean, and SignalPeptideCleavageSite across different datasets.
- False positive analysis: The false positive rates (FPR) are analyzed for both the von Heijne
  and SVM methods, with a focus on sequences containing helix regions.
