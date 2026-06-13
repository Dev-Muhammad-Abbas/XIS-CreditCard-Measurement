
# Calibrated Credit Card Measurement System

## 1. Project Overview

This project presents an end-to-end computer vision pipeline for real-world dimensional measurement using intrinsic camera calibration and deep learning-based semantic segmentation.

The system demonstrates how pixel-level predictions can be converted into physically meaningful metric measurements (millimetres) within a calibrated camera setup.

The implemented pipeline simulates an industrial inspection workflow and includes:

- Intrinsic camera calibration using a checkerboard pattern
- Lens distortion correction via image undistortion
- Custom dataset collection and manual annotation
- U-Net based binary semantic segmentation
- Contour extraction and rotated minimum-area bounding box estimation
- Pixel-to-millimetre conversion using calibrated geometry
- Quantitative measurement validation and error analysis

---

## 2. Selected Object

Object: Standard Credit Card  
Nominal Dimensions:
- Width: 85.6 mm
- Height: 53.98 mm

The credit card was selected due to:
- Standardized and well-defined dimensions
- Planar geometry suitable for metric validation
- Ease of manual annotation and repeated measurement

---

## 3. System Architecture

Raw Image  
→ Intrinsic Undistortion  
→ U-Net Segmentation  
→ Probability Map  
→ Binary Mask  
→ Largest Connected Contour  
→ Rotated Bounding Box  
→ Pixel Measurement  
→ Pixel-to-mm Conversion  
→ Error Evaluation

---

## 4. Calibration Summary

- Calibration Images Used: 24
- Checkerboard Configuration: 6 × 9 inner corners
- Mean Reprojection Error: 0.324 pixels

All measurements are performed on undistorted images.
Intrinsic calibration ensures geometric consistency and prevents distortion-induced measurement bias.

---

## 5. Model Training Summary

- Architecture: Custom U-Net
- Loss Function: Binary Cross Entropy with Logits
- Optimizer: Adam (learning rate = 0.001)
- Epochs: 8 (GPU training)
- Final Validation Loss: ~0.026

The model successfully learns the spatial structure of the credit card despite significant foreground–background imbalance.

---

## 6. Measurement Validation

Measurement was performed on 10 independent validation/test samples.

Final Results:

- Mean Absolute Error (MAE): ~10.23 mm
- Mean Percentage Error (MPE): ~18.95 %

The system demonstrates correct pixel-to-metric conversion using intrinsic calibration.
Observed deviations are primarily caused by perspective distortion and partial segmentation coverage.

---

## 7. Limitations

- Perspective distortion not fully compensated (no homography rectification)
- Segmentation confidence varies under challenging lighting
- Limited dataset size (41 training images)
- Bounding box estimation sensitive to mask completeness

---

## 8. Future Improvements

- Homography-based planar rectification
- Increased dataset size and augmentation
- Advanced segmentation loss functions (e.g., focal or Dice-based refinement)
- Multi-view calibration for improved robustness
- Confidence-based filtering for unreliable predictions
