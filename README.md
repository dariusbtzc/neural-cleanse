# Neural Cleanse Overview
This repository contains the implementation of the Neural Cleanse algorithm, a method for detecting and mitigating backdoor attacks in neural networks. 

Backdoor attacks are a form of cyber threat where a malicious trigger is inserted into a neural network, causing it to produce incorrect outputs when the trigger is present. Neural Cleanse aims to identify these triggers and assess the vulnerability of neural networks to such attacks. 

This implementation identifies the presence of backdoors using an outlier detection method and reverse engineers the backdoor triggers.


# Implementation Steps
1. **Reverse Engineer the Trigger** (for each label in the dataset):
	1. Initialise a random trigger pattern and mask.
	2. Perform optimisation to find the most effective trigger to misclassify an image to the target label, while minimising the mask to obtain a concise trigger.
	3. Repeat steps (i) – (ii) for a specified number of trials for each label.
2. **Measure the Attack Success Rate (ASR)**: Calculate the ASR of each reverse-engineered trigger using a test set and select the best trigger with the highest ASR for each label.
3. **Identify the Outliers**: For each reverse-engineered trigger, calculate the mask’s L1 norm and perform outlier detection using Median Absolute Deviation (MAD).


# Files
- `neural cleanse_pt.ipynb`: Jupyter notebook with PyTorch implementation.
- `neural cleanse_tf.ipynb`: Jupyter notebook with TensorFlow implementation.


# Dependencies
- Python 3.x
- PyTorch
- TensorFlow


# Usage
1. Clone the repository and open the Jupyter notebooks in an environment that supports PyTorch / TensorFlow.
2. Insert the backdoored model with the required model architecture / weights. 
3. Insert the appropriate dataset the backdoored model was trained on and update the image dimensions accordingly.
4. Update the file paths for logging purposes, if needed.


# Outputs
1. Images of the reverse-engineered backdoor triggers.
2. Log file containing the parameters used and the ASR and MAD outlier detection results for each backdoor trigger.


# Reference
This implementation is based on the original Neural Cleanse article: [Neural Cleanse: Identifying and Mitigating Backdoor Attacks in Neural Networks](https://ieeexplore.ieee.org/document/8835365)
