# System Architecture

## Pipeline Overview

```
[MRI Image Input] → [Preprocessing: resize 224×224, normalize, augment]
      → [Model: Custom CNN | VGG16 | ResNet50 (parallel comparison)]
      → [Prediction: glioma / meningioma / pituitary / no tumor]
      → [Grad-CAM: heatmap overlay on original scan]
```

## Components

| Component | Responsibility |
|---|---|
| Data Loader | Downloads and loads the Kaggle MRI dataset |
| Preprocessing | Resize, normalize, augment (rotation/shift/zoom/flip/brightness) |
| Custom CNN | 4-block Conv→BatchNorm→ReLU→MaxPool baseline |
| VGG16 Branch | ImageNet-pretrained, fine-tuned on MRI data |
| ResNet50 Branch | ImageNet-pretrained, fine-tuned, tests deeper residual architecture |
| Evaluation | Accuracy, precision, recall, F1, confusion matrix, model comparison table |
| Grad-CAM | Generates heatmap overlays for explainability |

## Design Decisions

- **Why compare three models instead of picking one upfront:** establishes whether transfer learning provides a measurable benefit over a from-scratch baseline on this specific limited dataset, rather than assuming it.
- **Why Grad-CAM specifically:** it requires no architecture changes and works post-hoc on any CNN-based model, making it practical to apply across all three models for a fair comparison.
- **Why heavy augmentation:** medical imaging datasets are typically small; augmentation is the primary lever for improving generalization without collecting more data.

## Future Architecture Extensions

- Add a U-Net segmentation branch parallel to the classification branch for tumor boundary localization
- Wrap the best-performing model in a Flask/Streamlit inference API for deployment
