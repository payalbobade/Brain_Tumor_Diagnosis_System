# Dataset Documentation

## Source

- **Primary:** [Brain Tumor MRI Dataset (Kaggle)](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset) — ~7,000 MRI images across 4 classes
- **Alternative (2-class, smaller):** [Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection)

## Classes

| Class | Description |
|---|---|
| Glioma | Tumor arising from glial cells |
| Meningioma | Tumor arising from the meninges |
| Pituitary | Tumor in the pituitary gland |
| No Tumor | Healthy scan |

## Preprocessing Applied

- Resizing all images to **224×224** (standard input size for VGG16/ResNet50)
- Pixel normalization
- Data augmentation: rotation, width/height shift, zoom, horizontal flip, brightness adjustment
- Train / validation / test split (see notebook for exact ratios used)

## Known Limitations

- Single-source dataset — a production system should validate against scans from multiple institutions/scanner types before clinical use
- Class balance across the 4 categories should be checked in the notebook's EDA cell; document the actual distribution once run
