
# Model Training Report

## 1. Model Architecture

The segmentation model is based on a custom U-Net architecture designed for binary semantic segmentation.

Key characteristics:
- Encoder–decoder structure
- Skip connections for spatial detail preservation
- Fully convolutional design
- Suitable for small-to-medium datasets

U-Net was selected instead of object detection frameworks (e.g., YOLO) because pixel-level segmentation is required for precise contour extraction and metric measurement.

---

## 2. Dataset Split

Total Images: 73

Split:
- Training: 51 images
- Validation: 14 images
- Test: 8 images

Dataset exported in COCO segmentation format.

---

## 3. Training Configuration

- Loss Function: Binary Cross Entropy with Logits
- Optimizer: Adam
- Learning Rate: 0.001
- Batch Size: 2–4 (depending on GPU availability)
- Epochs: 8 (GPU training)

---

## 4. Convergence Behavior

Training and validation loss decreased rapidly during early epochs.

Final Validation Loss: ~0.026

The model demonstrates stable convergence despite severe foreground–background imbalance (~1% object pixels).

---

## 5. Observations

- Segmentation quality is sufficient for contour extraction.
- Class imbalance affects segmentation confidence.
- Model generalization is limited by dataset size.
- Rotated bounding box improves orientation invariance.

---

## 6. Potential Improvements

- Data augmentation (rotation, brightness, contrast)
- Dice or Focal loss for imbalance handling
- Larger dataset
- Confidence-based mask refinement
