
# Setup Instructions

## 1. Dependencies

pip install torch torchvision opencv-python pycocotools matplotlib pandas

## 2. Dataset

Place COCO-format dataset under:
project/coco_dataset/

## 3. Model

Load the trained model:
final_unet_model.pth

## 4. Execution

Run notebook sequentially to:
- Load dataset
- Load model
- Perform inference
- Compute measurement
- Generate evaluation metrics
