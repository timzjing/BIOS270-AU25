# Project 2

**Name:** Tim Jing
**Student ID:** timjing
**Date:** 12/10/2025  

---

## Overview

This writeup covers Project 2.

---

## Content

#### Project 2

Title: PulmoRL: Reinforcement-Driven Computer Vision for Pulmonary CT Analysis

1. Project Overivew
- Overarching Goal: The goal of PulmoRL is to develop a reinforcement learning (RL) enhanced computer vision pipeline for analyzing lung CT scans. We aim to improve the detection and segmentation of pulmonary nodules beyond the accuracy of conventional, static models.

- Rationale: In clinical diagnostics, lung CT is crucial for the early detection of lung cancer. However, current deep learning models typically apply fixed processing to every scan. By allowing an RL agent to dynamically adapt image preprocessing (e.g., windowing, contrast) and spatial attention on a per-scan basis, we mimic an expert radiologist. This approach addresses the limitation of static models, which often fail to generalize across different scanners or data distributions.

- Aims:
    - Aim 1: Develop an RL agent for dynamic image preprocessing.
    - Aim 2: Integrate RL with a Vision Transformer for segmentation.

2. Data
- Dataset Description: We will use the public LIDC/IDRI dataset, which contains radiologist-annotated lung CT scans. The data consists of 3D volumetric images stored in DICOM or comparable medical imaging formats.

- Data Suitability The raw volumetric data requires transformation to be suitable for our pipeline. We will extract 3D sub-volumes that contain nodules (positive examples) as well as normal regions (for false-positive analysis).

- Storage and Data Management: Data will be stored on the compute cluster (i.e. farmshare). We will ensure that scans from the same patient are kept together to prevent data leakage during train/test splits. Sharing and backups can be done through the cluster.

3. Environment
- Coding Environment: The project will be developed using Python in a standard HPC environment (e.g., Farmshare). We will utilize a tmux or Jupyter workflow.

- Dependencies: PyTorch and Nibabel (for medical image handling)

- Reproducibility: We will maintain a Conda environment file to manage package versions. All code will be version-controlled on Git to ensure the analysis can be rerun by collaborators.

4. Pipeline
- Algorithms and Methods: There are two main components.
    - 1. RL Controller: An agent that views the current state (CT slice/sub-region + preprocessing settings) and takes actions (zoom, pan, adjust contrast, next slice).
    - 2. Vision Model: Upon the agent's decision to stop, the final focused view is passed to a Vision Transformer (ViT) for segmentation.

- Scalability and Efficiency: To ensure efficiency on the 3D dataset, the agent will view downsampled or slice-by-slice representations, only querying the Vision Model at the terminal step. This approach avoids processing the entire high-resolution volume uniformly.

5. Machine Learning
- Task Definition: The primary task is the supervised segmentation and detection of lung nodules. The RL component adds a sequential decision-making task to optimize the input for the segmentation model.

- Feature Representation: The current state is the visual pixels of the CT slide combined with metadata like the current image level. The action space are the discrete actions such as zooming, panning, etc. that the model might use.

- Model Selection: We will use a Vision Transformer (ViT) for the vision model to achieve SOTA performance and ascertain global context better than standard CNNs. We will use a Deep Q-Network (DQN) for RL, as it is optimized for discrete action spaces.

- Generalization Strategy: We will split data into train and test sets, ensuring that scans from the same patient do not leak. Data augmentation (rotations, intensity shifts) will be used during the training of the vision model.

- Evaluation Metrics: F1/Dice similarity for final segmentation masks. Sensitivity (recall) to measure cancer detection rates.


## Acknowledgement
Collaborator: N/A
