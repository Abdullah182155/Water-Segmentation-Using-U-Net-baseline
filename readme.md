# Water Segmentation Using U-Net 

This project focuses on detecting water bodies in satellite imagery using a deep learning approach. The model used is a U-Net , trained on multispectral images with 12 bands.

## 📁 Dataset Structure

Your dataset should be organized as follows:

```
Water Segmentation/
├── data/
│   ├── images/      # .tif files with 12-band multispectral satellite images
│   └── labels/      # .png files with corresponding binary water masks
```

- Each image must have a matching label with the same base filename.
- Images: 12-channel GeoTIFFs
- Labels: single-channel (grayscale) binary masks

## 🚀 Model Architecture

- **Model**: U-Net with `segmentation_models_pytorch`
- **Input Channels**: 12
- **Output**: Binary segmentation mask

## 🧪 Training Pipeline

1. **Preprocessing**:

   - Resize to 128x128
   - Albumentations augmentations (flip, rotate)
   - Normalize to [0, 1]

2. **Dataset Splitting**:

   - 70% training, 15% validation, 15% testing

3. **Loss & Metrics**:

   - Loss: Binary Cross Entropy (BCE)
   - Metrics: Dice Score, IoU

4. **Training**:

   - Batch size: 4
   - Optimizer: Adam
   - Epochs: 50
   - Model checkpointing on best validation loss

## 📊 Output

- Training and validation loss curves
- Dice/IoU metrics over time
- Saved best model weights (`best_model.pth`)

## 🖼️ Visualization

- Display sample predictions against ground truth
- Support for visualizing individual spectral bands

## 🧰 Requirements

- Python 3.8+
- torch
- torchvision
- albumentations
- tifffile
- opencv-python
- segmentation-models-pytorch

Install all requirements:

```bash
pip install -r requirements.txt
```

## 📝 Notes

- Ensure image-mask dimensions match before training.
- This model assumes the input has exactly 12 spectral bands.
- MiT-B2 does **not** use pretrained weights (due to non-RGB input).

---

Made with ❤️ for geospatial deep learning.

