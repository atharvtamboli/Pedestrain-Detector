# 🚶 Pedestrian Detection using YOLOv8

A computer vision project for **pedestrian detection in self-driving car imagery** using a pretrained **YOLOv8 object detection model**.

The project uses labeled road-scene images from a self-driving car dataset, filters the annotations for pedestrians, visualizes the ground-truth bounding boxes, and applies YOLOv8 to detect pedestrians in the same images.

It also supports uploading custom images and running pedestrian detection on them.

---

## 📌 Overview

Pedestrian detection is an important computer vision task in autonomous driving systems.

In this project, a self-driving car dataset is used to identify images containing pedestrians. The dataset annotations are filtered for **class ID 3**, which represents pedestrians in the selected dataset.

A pretrained **YOLOv8 Medium (`yolov8m.pt`)** model is then used to detect people in the images.

The project demonstrates the complete workflow:

```text
Dataset
   ↓
Load Annotations
   ↓
Filter Pedestrian Class
   ↓
Visualize Ground Truth
   ↓
Load Pretrained YOLOv8
   ↓
Run Object Detection
   ↓
Draw Predicted Bounding Boxes
   ↓
Test on Custom Images
```

---

## 🎯 Objectives

* Load and explore a self-driving car image dataset.
* Identify pedestrian annotations from the dataset.
* Visualize ground-truth pedestrian bounding boxes.
* Use a pretrained YOLOv8 model for pedestrian detection.
* Compare the model's detections visually with the labeled images.
* Run pedestrian detection on custom uploaded images.

---

## 🗂️ Dataset

The project uses the **Self Driving Cars** dataset available through Kaggle.

The dataset contains road-scene images and corresponding object annotations.

The notebook loads:

```text
labels_train.csv
```

and filters the annotations using:

```python
df[df['class_id'] == 3]
```

This extracts the records corresponding to pedestrians.

---

## 🧠 Model

The project uses:

**YOLOv8 Medium (`yolov8m.pt`)**

The model is loaded using the Ultralytics framework:

```python
from ultralytics import YOLO

model = YOLO("yolov8m.pt")
```

### Important

The YOLOv8 model used in this project is **pretrained**.

This project does **not train or fine-tune YOLOv8** on the pedestrian dataset. Instead, it uses the pretrained model to perform object detection on the selected images.

---

## 🔍 Detection Process

For each image:

1. The image is passed to YOLOv8.
2. YOLO generates object detections.
3. Only detections belonging to the **person class** are retained.
4. Bounding boxes are drawn around detected pedestrians.
5. The confidence score is displayed alongside each detection.

Detection settings:

```python
conf = 0.2
iou = 0.5
```

The model's COCO class ID `0` is used to identify the `person` class.

---

## 🏷️ Ground Truth Visualization

The dataset provides bounding-box coordinates:

```text
xmin
ymin
xmax
ymax
```

These coordinates are used to draw the ground-truth pedestrian bounding boxes on the original images.

Example workflow:

```text
Dataset Annotation
       ↓
xmin, ymin, xmax, ymax
       ↓
Bounding Box
       ↓
Ground Truth: Pedestrian
```

This provides a visual reference when examining YOLO's predictions.

---

## 📊 Results

The notebook demonstrates pedestrian detection on multiple labeled road-scene images.

For each prediction, the detected pedestrian is displayed with:

* Bounding box
* `person` label
* Detection confidence

Example:

```text
person 0.87
```

The project also tests the detector on custom images uploaded through Google Colab.

---

## 📸 Screenshots

Recommended screenshots for the repository:

### Ground Truth

![Ground Truth](screenshots/ground_truth.png)

### YOLOv8 Detection

![YOLO Detection](screenshots/yolo_detection.png)

### Custom Image Detection

![Custom Detection](screenshots/custom_detection.png)

> Update the filenames if your screenshot names are different.

---

## 🛠️ Technologies Used

| Technology   | Purpose                 |
| ------------ | ----------------------- |
| Python       | Programming language    |
| YOLOv8       | Object detection        |
| Ultralytics  | YOLO implementation     |
| OpenCV       | Image processing        |
| Pandas       | Dataset/CSV processing  |
| NumPy        | Numerical operations    |
| Matplotlib   | Visualization           |
| PIL          | Image handling          |
| KaggleHub    | Dataset download        |
| Google Colab | Development environment |

---

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone https://github.com/atharvtamboli/Pedestrian-Detection-YOLOv8.git
cd Pedestrian-Detection-YOLOv8
```

### 2. Open the notebook

Open:

```text
pedestrian_detection.ipynb
```

The project is designed to run in **Google Colab**.

### 3. Install dependencies

The notebook installs Ultralytics automatically:

```python
!pip install ultralytics
```

### 4. Run the notebook

The notebook will:

* Download the dataset
* Load annotations
* Filter pedestrian records
* Display ground-truth boxes
* Load YOLOv8
* Detect pedestrians
* Display predictions
* Allow custom image uploads

---

## 📁 Repository Structure

```text
Pedestrian-Detection-YOLOv8/
│
├── pedestrian_detection.ipynb
├── README.md
│
├── screenshots/
│   ├── ground_truth.png
│   ├── yolo_detection.png
│   └── custom_detection.png
│
└── report/
    └── Project_Report.pdf
```

---

## ⚠️ Limitations

* The project uses a **pretrained YOLOv8 model** rather than a model specifically trained on this dataset.
* Detection results depend on the pretrained model's learned classes and the quality of the input images.
* The project primarily demonstrates pedestrian detection and visual comparison rather than a complete autonomous-driving perception system.
* No formal model retraining or fine-tuning is performed.

---

## 🚀 Future Improvements

Possible extensions include:

* Fine-tuning YOLOv8 on the pedestrian dataset.
* Calculating precision, recall, and mAP against the dataset annotations.
* Adding real-time detection from video.
* Tracking pedestrians across video frames.
* Integrating the detector with an autonomous-driving perception pipeline.

---

## 👨‍💻 Author

**Atharv Tamboli**

B.Tech Computer Science
SRM Institute of Science and Technology

---

⭐ If you found this project useful, consider giving the repository a star.
