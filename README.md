# 🧠 Helmet Detection with YOLOv5

## 📌 Description

This project uses the YOLOv5 object detection model to identify helmets in images. The dataset was sourced from [Roboflow](https://roboflow.com), and the YOLOv5 model was customized and trained in a Google Colab environment.

## 🧰 Tools & Technologies

- Python
- YOLOv5
- Roboflow
- PyTorch
- Google Colab
- OpenCV (optional for inference)

## 🚀 Setup Instructions

1. **Clone YOLOv5 repository:**

   ```bash
   git clone https://github.com/ultralytics/yolov5
   cd yolov5
   git reset --hard 064365d8683fd002e9ad789c1e91fa3d021b44f0
   ```

2. **Install Dependencies:**

   ```bash
   pip install -qr requirements.txt
   pip install roboflow
   ```

3. **Download Dataset via Roboflow:**

   ```python
   from roboflow import Roboflow
   rf = Roboflow(api_key="YOUR_API_KEY")
   project = rf.workspace("YOUR_WORKSPACE").project("YOUR_PROJECT")
   dataset = project.version(1).download("yolov5")
   ```

4. **Model Configuration:**

   A custom `custom_yolov5s.yaml` file was created to match the number of helmet classes.

5. **Training:**

   ```bash
   python train.py --img 640 --batch 16 --epochs 50 --data {dataset.location}/data.yaml --cfg ./models/custom_yolov5s.yaml --weights yolov5s.pt --name helmet-detect
   ```

## 📊 Results

- The model was trained for 50 epochs and then 150.
- Evaluation was done using YOLOv5 built-in validation.

## 📁 Folder Structure

- `models/`: Custom model config
- `runs/train/`: YOLOv5 training output (metrics, images, etc.)
- `data.yaml`: Roboflow-generated dataset configuration


