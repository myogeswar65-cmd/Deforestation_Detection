### Deforestation Detection from Satellite Images

An AI-based forest monitoring system that uses Sentinel-2 satellite imagery to map forest cover and detect potential clearing, helping environmental researchers and forest-monitoring teams investigate land-cover changes.

## Results: Baseline vs. U-Net

Evaluated on the same held-out test tiles against Google Dynamic World reference labels.

Metric| NDVI Baseline| U-Net (ResNet-34)
IoU| 0.9048| 0.8830
F1-score| 0.9500| 0.9379

## Finding: The NDVI baseline performed better on this evaluation. These scores measure agreement with reference labels, not independently verified forest cover.

Before-and-After Forest Change Map

Study area: Near Novo Progresso, Pará, Brazil
Comparison: July 2023 vs July 2024

"Forest cover and potential clearing map"
<img width="2910" height="3930" alt="forest_change_map" src="https://github.com/user-attachments/assets/30633cb2-76c0-4089-b34a-f4c546d130af" />


Red regions indicate potential forest clearing, not confirmed deforestation.


## Limitations

- Google Dynamic World labels are model-generated and are not verified ground truth.
- Evaluation covers a limited study area and time period.
- Clouds, missing observations, and classification errors can affect results.
- NDVI can confuse dense vegetation with forest.
- Detected changes require independent verification before being treated as confirmed deforestation.
- Area estimates depend on the actual raster resolution, projection, and valid observation coverage.

## How It Works

1. Retrieve Sentinel-2 Level-2A imagery through Google Earth Engine.
2. Prepare forest labels using Google Dynamic World.
3. Train a U-Net model with a pretrained ResNet-34 encoder and six spectral bands.
4. Compare U-Net predictions against an NDVI threshold baseline.
5. Compare predicted forest masks from July 2023 and July 2024.
6. Filter small connected regions and estimate potential clearing area.

## Technology Stack

Python · Google Colab · Google Earth Engine · Sentinel-2 · Google Dynamic World · PyTorch · U-Net · ResNet-34 · NumPy · SciPy · Matplotlib

## Project Status

Core training, evaluation, and potential forest-change detection completed. Independent validation and live demo deployment remain future work.
