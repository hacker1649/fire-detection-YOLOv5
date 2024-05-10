# Real Time Fire Detection Using YOLOv5

Fire detection task aims to identify fire or flame in an image or a video and put a bounding box around it. This repo includes a demo on how to build a fire detector using YOLOv5. 

## 🛠️ Installation
1. Clone this repo 
``` shell
# Clone
git clone https://github.com/hacker1649/fire-detection-YOLOv5.git
cd Fire-Detection-YOLOv5
```

2. Install [YOLOv5](https://github.com/ultralytics/yolov5). 
``` shell
git clone https://github.com/ultralytics/yolov5.git 
cd yolov5
pip install -r requirements.txt
```

## 🏋️ Training
I set up ```train.ipynb``` script for training the model from scratch. To train the model, download [Fire-Dataset](https://drive.google.com/file/d/1TQKA9nzo0BVwtmojmSusDt5j02KWzIu9/view?usp=sharing) and put it in ```datasets``` folder. This dataset contains samples from both [Fire & Smoke](https://www.kaggle.com/dataclusterlabs/fire-and-smoke-dataset) and [Fire & Guns](https://www.kaggle.com/atulyakumar98/fire-and-gun-dataset) datasets on Kaggle. I filtered out images and annotations that contain smokes & guns as well as images with low resolution, and then changed fire annotation's label in annotation files.

- YOLOv5
```
python train.py --img 640 --batch 16 --epochs 10 --data ../fire.yaml --weights yolov5s.pt --workers 0
```

## 🌱 Inference

- YOLOv5
  
If you train your own model, use the following command for detection:
``` shell
python detect.py --source ../input.mp4 --weights runs/train/exp/weights/best.pt --conf 0.2
```
Or you can use the pretrained model located in ```models``` folder for detection as follows:
``` shell
python detect.py --source ../input.mp4 --weights ../models/yolov5s_best.pt --conf 0.2
```
