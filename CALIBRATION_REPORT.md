
# Camera Calibration Report

## 1. Objective

The objective of camera calibration is to estimate intrinsic parameters that correct geometric distortion and enable accurate metric measurement.

All dimensional measurements in this project depend on accurate intrinsic calibration.

---

## 2. Calibration Method

Calibration was performed using OpenCV’s chessboard-based intrinsic calibration pipeline.

Configuration:
- Checkerboard inner corners: 6 × 9
- Total calibration images: 24
- Images captured from varied orientations and distances
- Subpixel corner refinement applied

---

## 3. Estimated Parameters

Intrinsic matrix and distortion coefficients are included in the calibration folder.

Mean Reprojection Error: 0.324 pixels

A reprojection error below 0.5 pixels is considered acceptable.  
A value of 0.324 px indicates strong geometric consistency.

---

## 4. Importance for Measurement

Radial and tangential distortion introduce non-linear pixel displacement.

If measurements are performed on distorted images:

- Pixel lengths do not represent true geometric distances.
- Pixel-to-millimetre conversion becomes inconsistent.

Therefore, all images are undistorted using cv2.undistort() prior to segmentation and measurement.

---

## 5. Calibration Dependency

The measurement pipeline is directly dependent on intrinsic calibration.  
Without undistortion, measurement error would increase significantly.

Future improvement may include extrinsic calibration and planar homography correction for perspective compensation.
