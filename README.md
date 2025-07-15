# 🚾 Wheel Detector using YOLOv8

A real-time object detection system built using [Ultralytics YOLOv8](https://docs.ultralytics.com) to identify wheels from images and videos. This project includes dataset preparation, training, and inference with a fine-tuned model.

---

## 📂 Project Structure

```
wheel-detector/
│
├── data/                   # Original images and labels
│   ├── images/
│   └── labels/
│
├── data_split/             # Auto-split train/val data
│   ├── train/
│   └── validate/
│
├── runs/                   # YOLO training/inference outputs
│
├── test/                   # Input video files
│   └── drive.mp4
│
├── yolov8n.pt              # Pretrained base model
├── config.yaml             # YOLO dataset config file
├── test_video.py           # Inference script
└── README.md
```

---

## 🧪 Demo

After training, run:

```bash
python test_video.py
```

✅ This will process `test/drive.mp4`, annotate detections, and save the output video to `runs/predict/`.

---

## 💠 How to Train Your Model

### 1. Split Your Dataset
Automatically split data from `data/images` and `data/labels`:

```python
# inside test_video.py
# PART 1: Dataset split script will run
```

### 2. Train YOLOv8

Edit `config.yaml`:

```yaml
train: data_split/train
val: data_split/validate
nc: 1
names: ['wheel']
```

Then run:

```python
# inside test_video.py
# PART 2: Training will start with yolov8n.pt
```

---

## 🔍 Inference Example

```python
from ultralytics import YOLO

model = YOLO('runs/detect/train2/weights/best.pt')
results = model.predict(
    source='test/drive.mp4',
    conf=0.25,
    save=True,
    show=False
)
```

---

## 🛆 Requirements

Install dependencies with:

```bash
pip install ultralytics
```

or use `requirements.txt`:

```txt
ultralytics
```

---

## 🧠 Model Info

- **Base Model**: YOLOv8n (nano)
- **Dataset**: Custom-labeled wheel images
- **Confidence Threshold**: 0.25
- **Image Size**: 512x512
- **Epochs**: 100

---

## 📜 License

This project is licensed under the MIT License. See `LICENSE` for more info.
