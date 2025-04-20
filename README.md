# Real-Time Pedestrian Detection

This repository contains the implementation and analysis of feature extraction methods and classification algorithms for real-time pedestrian detection, as described in the thesis *A Comparative Analysis of Feature Extraction Methods and Classification Algorithms for Real-Time Pedestrian Detection* by Hung Dao Nguyen.

## Overview

The project focuses on comparing the performance of various feature extraction techniques and classification algorithms for detecting pedestrians in real-time video streams. The goal is to balance detection accuracy and computational latency, crucial for applications like autonomous driving and intelligent surveillance.

### Feature Extraction Methods

- **Histogram of Oriented Gradients (HOG)**: Captures edge and shape information through gradient magnitude and orientation histograms.
- **Speeded-Up Robust Features (SURF)**: Detects scale- and rotation-invariant keypoints using Hessian matrix-based detection and integral images.
- **eXtended Center-Symmetric Local Binary Patterns (XCS-LBP)**: Combines LBP and CS-LBP strengths for robust texture description with short histograms.
- **Local Binary Patterns (LBP)**: Encodes texture by comparing pixel intensities with neighbors, generating binary patterns.

### Classification Algorithms

- **Support Vector Machine (SVM)**: Maps features to a high-dimensional space to find an optimal separating hyperplane.
- **Random Forest (RF)**: Builds multiple decision trees on random data subsets for robust classification.

### Dataset

- **INRIA Person Dataset**: Contains 902 images split into train (632), validation (180), and test (90) sets, with manually annotated bounding boxes for pedestrians and negative samples (e.g., trees, cars).
- **Free Stock Video**: A 640x360 resolution video at 30 fps used to evaluate real-time processing speed.

## Installation

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/Anthony-D11/realtime-pedestrian-detection.git
   cd pedestrian-detection
   ```

2. **Set Up a Virtual Environment** (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install Dependencies**:
   
   - `scikit-image`
   - `opencv-contrib-python` ver. 3.4.20-dev
   - `scikit-learn`
   - `numpy`
   - `matplotlib`

## Key Findings

- **Accuracy**:

  - SVM outperforms RF across all feature extraction methods, with accuracies ranging from 91.28% to 96.26%.
  - HOG with 16x16 cell size and SVM achieves the highest accuracy (96.16%).
  - LBP with SVM at 16x16 cell size also performs strongly (96.26%).
  - SURF accuracy fluctuates (75.6%–80.17%) with no clear trend as cluster size increases.

- **Processing Speed**:

  - HOG with SVM at 24x24 cell size offers a good balance (93.77% accuracy, 0.2s/frame or 5 fps).
  - LBP with SVM at 32x32 cell size is promising (95.74% accuracy, 0.54s/frame).
  - RF is generally too slow for real-time applications (1.96–8.58s/frame).
  - SURF processing time increases with cluster size, ranging from 0.6s to 6.12s.

- **Real-Time Potential**:

  - The combination of HOG (24x24) and SVM is recommended for real-time pedestrian detection due to its acceptable accuracy and speed.
  - Future work could optimize LBP with larger cell sizes or use a stronger processor to achieve 30 fps.

## Requirements

- Python 3.12.1
- Hardware: Tested on AMD Ryzen 7 5800Hs with 16GB RAM. A stronger processor may improve real-time performance.

## Acknowledgments

- INRIA Person Dataset for providing a robust dataset for pedestrian detection.
- Open-source libraries: scikit-image, OpenCV, scikit-learn.
- Thesis advisors and peers at the University of New Brunswick for guidance and feedback.
