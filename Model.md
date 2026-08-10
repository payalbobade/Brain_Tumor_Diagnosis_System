# Model Documentation

## Models Compared

| Model | Type | Notes |
|---|---|---|
| Custom CNN | Trained from scratch | 4-block Conv→BatchNorm→ReLU→MaxPool baseline |
| VGG16 | Transfer learning | ImageNet-pretrained, last few conv blocks fine-tuned |
| ResNet50 | Transfer learning | ImageNet-pretrained, fine-tuned; tests residual depth benefit |

## Input / Output

- **Input:** 224×224×3 RGB MRI image
- **Output:** 4-class softmax (glioma / meningioma / pituitary / no tumor)

## Evaluation Metrics Used

Accuracy, Precision, Recall, F1-Score, Confusion Matrix — computed per model on a held-out test set, with an auto-generated comparison table in the notebook.

## Explainability: Grad-CAM

Grad-CAM generates a class-activation heatmap showing which regions of the MRI the model weighted most heavily for its prediction. This is layered on top of the trained CNN-based models without requiring architecture changes, and is the primary tool used here to move the project from "black box classifier" to "interpretable clinical aid."

## Key Learnings

- Transfer learning (VGG16/ResNet50) typically outperforms a from-scratch CNN on limited medical imaging data, since ImageNet features transfer well to texture/edge-heavy scans.
- Explainability tools like Grad-CAM are essential for any medical AI system to build clinical trust.
- Class imbalance and image quality variability are the main real-world challenges for this task.

## Fill In After Running

| Metric | Custom CNN | VGG16 | ResNet50 |
|---|---|---|---|
| Accuracy |89.60% – 97.55%|95.23% – 98.50%|90.20% – 98.44%|
| Precision |90.00% – 96.43%|93.27% – 99.00%|88.76% – 98.40%|
| Recall |92.00% – 100.0%|93.72% – 99.38%|92.00% – 98.40%|
| F1-Score |90.00% – 98.18%|94.22% – 99.00%|90.00% – 98.40%|

Record your actual final numbers here once training completes — they'll vary by run and dataset variant.
