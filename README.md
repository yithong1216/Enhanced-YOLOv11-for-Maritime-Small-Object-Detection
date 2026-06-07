# Enhanced YOLOv11 for Maritime Small Object Detection

This course project improves YOLOv11 for maritime small object detection while keeping the model suitable for real-time inference.

The main idea is to strengthen shallow feature extraction and add a high-resolution detection path so small maritime targets are easier to localize without making the detector unnecessarily heavy.

## Project Files

- `model.yaml`: YOLOv11 model configuration with the proposed small-object detection changes.
- `CAFM.py`: Attention-based feature module used by the enhanced model.
- Course project report PDF: detailed write-up for the model modification and experiments.

## Main Improvements

- Adds an attention-enhanced `C2f_AT` module to improve feature representation.
- Introduces an extra high-resolution feature fusion path for tiny and small objects.
- Keeps the YOLO-style multi-scale detection structure for real-time object detection.
- Configures the detector for 5 maritime object classes.

## Environment

Install the main dependencies:

```bash
pip install ultralytics torch einops
```

## Usage

Copy `CAFM.py` into the Ultralytics module path or register its classes in the YOLOv11 model parser so that `C2f_AT` can be used by `model.yaml`.

Train the enhanced model:

```bash
yolo detect train model=model.yaml data=your_dataset.yaml imgsz=640 epochs=100 batch=16
```

Run inference:

```bash
yolo detect predict model=runs/detect/train/weights/best.pt source=path/to/images
```

## Notes

This project is designed for maritime small object detection, where targets are often small, sparse, and affected by complex sea backgrounds. The enhanced model focuses on improving small target feature learning while preserving YOLOv11's efficient detection pipeline.
