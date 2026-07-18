# Project Workflow

```
1. Dataset Download (Kaggle)
      ↓
2. Preprocessing (resize, normalize, augment)
      ↓
3. Train Custom CNN (baseline)
      ↓
4. Train VGG16 (transfer learning, fine-tuned)
      ↓
5. Train ResNet50 (transfer learning, fine-tuned)
      ↓
6. Evaluate all 3 models (accuracy/precision/recall/F1/confusion matrix)
      ↓
7. Generate comparison table
      ↓
8. Grad-CAM explainability on best model
      ↓
9. Save final model
```

## Reproducing This Workflow

```bash
# Open in Google Colab or Kaggle Notebooks (GPU recommended)
# Then simply run all cells — the notebook handles:
#  - dataset download
#  - preprocessing
#  - training all 3 models
#  - evaluation and comparison
#  - Grad-CAM generation
#  - model saving
```

No separate script setup is required — this project is intentionally notebook-first for reproducibility and ease of review.
