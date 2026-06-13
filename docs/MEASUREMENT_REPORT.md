
# Measurement Report

## 1. Objective

The objective of this stage is to convert segmentation-derived pixel measurements into real-world metric dimensions (millimetres) using intrinsic camera calibration.

---

## 2. Measurement Pipeline

1. Undistort input image using intrinsic calibration parameters.
2. Perform semantic segmentation using trained U-Net.
3. Generate probability map.
4. Apply threshold to obtain binary mask.
5. Extract largest connected contour.
6. Compute rotated minimum-area bounding box.
7. Calculate pixel width and height.
8. Convert pixel measurements to millimetres using reference dimension.

---

## 3. Pixel-to-Millimetre Conversion

Let:

P_long = measured pixel length of the longer side  
R_long = known real-world length of the longer side (85.6 mm)

Pixel-to-mm conversion factor:

pixels_per_mm = P_long / R_long

For any pixel measurement P:

Length_mm = P / pixels_per_mm

Rotated bounding box ensures orientation-invariant measurement.

---

## 4. Validation Strategy

Measurements were computed for 10 independent validation/test samples.

Ground Truth Dimensions:
- Long Side: 85.6 mm
- Short Side: 53.98 mm

---

## 5. Results

Mean Absolute Error (MAE): ~10.23 mm  
Mean Percentage Error (MPE): ~18.95 %

The long side measurement remains stable due to direct reference-based scaling.
Short side variation is influenced by segmentation completeness and perspective effects.

---

## 6. Error Analysis

Primary sources of error:

- Perspective distortion (object not perfectly parallel to camera plane)
- Partial segmentation coverage
- Bounding box sensitivity to contour completeness
- Limited dataset size
- Single-reference scaling assumption

---

## 7. Recommendations for Improvement

- Homography-based planar rectification
- Increased dataset size
- Advanced segmentation loss functions
- Confidence-based mask filtering
- Multi-view calibration for enhanced geometric robustness
