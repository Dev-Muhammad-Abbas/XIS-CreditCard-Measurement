
# Dataset Description

## 1. Object Description

Object: Standard Credit Card

Nominal Dimensions:
- Width: 85.6 mm
- Height: 53.98 mm

The object was selected due to its standardized geometry and suitability for metric validation.

---

## 2. Data Collection

Total Images Captured: 73

Images were captured using the same calibrated camera under:

- Multiple background conditions
- Varied lighting environments
- Different orientations
- Slight perspective variations

The same resolution was maintained across all captures.

---

## 3. Dataset Split

- Training: 51 images
- Validation: 14 images
- Test: 8 images

Split ratio approximately 70 / 20 / 10.

---

## 4. Annotation Method

Manual polygon annotation performed using Roboflow.

Export Format: COCO segmentation.

Annotations were reviewed to ensure tight boundary alignment around the card.

---

## 5. Dataset Quality Considerations

- Foreground-to-background pixel ratio is highly imbalanced (~1% object area).
- Segmentation difficulty increases under low contrast conditions.
- Dataset size is moderate for deep learning segmentation tasks.
