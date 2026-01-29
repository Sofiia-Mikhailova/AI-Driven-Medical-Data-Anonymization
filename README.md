# Privacy-Preserving Brain Tumor Segmentation

> A Deep Learning framework that reconciles High-Utility Medical AI with Strict Patient Privacy.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-1.12%2B-red)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Prototype-orange)

## Project Overview
Medical data sharing is hindered by the Privacy-Utility Paradox:
* Utility: AI models require high-resolution, unaltered MRI scans to accurately detect tumors.
* Privacy: High-resolution MRI scans act as biological fingerprints, allowing attackers to re-identify patients with 100% accuracy.

This project implements a Defense Mechanism using adversarial noise (PGD) that "blinds" unauthorized re-identification systems while allowing the "AI Doctor" to continue diagnosing tumors with high precision.

---

## System Architecture

The project consists of three distinct modules:

### 1. The Utility Model ("The AI Doctor")
* Architecture: U-Net with ResNet34 encoder.
* Task: Multi-class Brain Tumor Segmentation.
* Performance: Achieved Dice Score: 0.9396 (Clinical Grade).

### 2. The Threat Model ("The Attacker")
* Architecture: ResNet18 Classifier.
* Task: Patient Re-identification (predicting Patient ID from MRI slices).
* Audit Result: Raw data leaks identity with 100.00% Accuracy.

### 3. The Defense Mechanism ("The Noise")
* Technique: Projected Gradient Descent (PGD).
* Method: Generates optimization-based noise (epsilon = 0.05) that maximizes the Attacker's loss function.
* Result: Drops Attacker accuracy to 0.00% while maintaining segmentation utility.

---

## Results

| Metric | Raw Data (Unsafe) | Protected Data (Ours) |
| :--- | :---: | :---: |
| Attacker Accuracy (Privacy Risk) | 100.00% | 0.00% |
| Segmentation Dice Score (Utility) | 0.9412 | 0.9396 |
| Visual Quality | Original | Perceptually Identical |

> Conclusion: We successfully broke the trade-off. The patient is mathematically indistinguishable to the attacker, but the tumor is clearly visible to the doctor.

---

## Installation

1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/privacy-brain-segmentation.git](https://github.com/your-username/privacy-brain-segmentation.git)
   cd privacy-brain-segmentation
