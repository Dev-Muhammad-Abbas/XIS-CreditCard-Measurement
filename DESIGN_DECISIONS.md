
# Design Decisions

## 1. Choice of Object

A standard credit card was selected due to:
- Known standardized dimensions
- Planar geometry
- Ease of segmentation
- Availability for repeated validation

---

## 2. Camera Calibration Approach

Intrinsic calibration using a checkerboard pattern was chosen because:
- It provides robust estimation of focal length and distortion coefficients.
- It corrects radial and tangential distortion.
- It ensures pixel geometry consistency for metric conversion.

ChArUco boards were considered but a standard checkerboard provided sufficient accuracy.

---

## 3. Model Selection

A custom U-Net architecture was selected instead of YOLO-based detection models because:

- The task requires pixel-level segmentation.
- Segmentation provides more accurate contour extraction than bounding-box detection.
- U-Net is lightweight and effective for small datasets.
- It avoids reliance on external pre-trained detection frameworks.

---

## 4. Training Strategy

- Binary Cross Entropy with Logits was used due to binary segmentation setup.
- Adam optimizer selected for stable convergence.
- Dataset split: 70% train, 20% validation, 10% test.

---

## 5. Measurement Strategy

- Largest connected contour extraction was used for robustness.
- Rotated minimum-area bounding box ensures orientation invariance.
- Pixel-to-mm conversion derived from known reference dimension.

---

## 6. Trade-offs

- Small dataset limits generalization.
- Axis-aligned bounding boxes were replaced with rotated bounding boxes for better accuracy.
- Homography-based correction was not implemented due to time constraints.

