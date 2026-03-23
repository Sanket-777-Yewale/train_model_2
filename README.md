# Train the Model on Custom Dataset using YOLOv8

## 📌 Project Overview

This project demonstrates how to train an object detection model using the Ultralytics YOLOv8 architecture on a custom dataset. The dataset is structured into training and validation subsets containing images and corresponding annotation labels.

The project is executed inside a Python virtual environment to ensure dependency isolation and reproducibility.

---

## 📁 Project Structure

```
C:.
├── dataset/
│   ├── images/
│   │   ├── train/
│   │   └── val/
│   └── labels/
│       ├── train/
│       └── val/
├── dataset 2/
│   ├── images/
│   │   ├── train/
│   │   └── val/
│   └── labels/
│       ├── train/
│       └── val/
├── runs/
│   └── detect/
│       ├── train*/
│           └── weights/
├── venv/   ← Virtual Environment
└── train.py
```

---

## ⚙️ Environment Setup (Virtual Environment)

### Step 1: Create Virtual Environment

```
python -m venv venv
```

### Step 2: Activate Environment

#### Windows:

```
venv\Scripts\activate
```

#### Linux / macOS:

```
source venv/bin/activate
```

---

## 📦 Install Dependencies

```
pip install ultralytics
```

(Optional: freeze dependencies)

```
pip freeze > requirements.txt
```

---

## 📊 Dataset Format

* Images: `.jpg` / `.png`
* Labels: YOLO format (`.txt`)

Each label file contains:

```
<class_id> <x_center> <y_center> <width> <height>
```

---

## 🧠 Model Training

### Basic Training

```
from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="data.yaml",
    epochs=50,
    imgsz=640
)
```

### Training with Batch Size

```
from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="data.yaml",
    epochs=50,
    imgsz=640,
    batch=8
)
```

---

## 📄 data.yaml Example

```
train: dataset/images/train
val: dataset/images/val

nc: 1
names: ["object"]
```

---

## 📈 Output

Training results are stored in:

```
runs/detect/train*/
```

Each run contains:

* `weights/best.pt` → Best model
* `weights/last.pt` → Last epoch model
* Training metrics and plots

---

## 🚀 How to Run

1. Activate virtual environment
2. Open VS Code terminal
3. Navigate to project folder
4. Execute:

```
python train.py
```

---

## 📌 Notes

* Virtual environment ensures dependency isolation
* Multiple runs are automatically saved (`train`, `train2`, etc.)
* Use `best.pt` for inference
* Modify `data.yaml` to switch datasets

---

## 📎 Future Improvements

* Hyperparameter tuning
* Model comparison (YOLOv8 variants)
* Deployment using Flask / FastAPI
