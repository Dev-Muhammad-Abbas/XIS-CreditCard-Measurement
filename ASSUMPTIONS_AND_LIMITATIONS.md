
# Assumptions and Limitations

## 1. Assumptions

- The object is approximately planar.
- The object is fully visible in the frame.
- Intrinsic calibration remains valid across measurements.
- Camera-object distance does not vary significantly between calibration and measurement.
- Lighting conditions are within training distribution.

---

## 2. Limitations

- Perspective distortion is not fully corrected via homography.
- Segmentation may partially miss object edges in difficult lighting.
- Small dataset size limits model generalization.
- Pixel-to-mm conversion uses single reference dimension.
- Measurement accuracy depends on segmentation completeness.

---

## 3. Future Work

- Implement homography-based planar rectification.
- Increase dataset size and augmentation.
- Apply advanced segmentation loss functions.
- Introduce multiple reference objects for scaling validation.
- Use confidence-based filtering of unreliable predictions.

