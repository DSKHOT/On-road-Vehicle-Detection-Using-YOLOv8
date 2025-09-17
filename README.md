# On-road-Vehicle-Detection-Using-YOLOv8
# **On road Vehicle Detection : Using YOLOv8 for Object Detection on Traffic videos on YouTube** using minimum resources

## **Context:**

A compact pipeline to run a custom-trained YOLOv8 model on YouTube videos/streams using minimum resources. 

This repository provides a bunch of scripts to train and deploy an object detector using trained yolov8n model.

Follow the step by step guide to train, validate and deploy your own object detector.

**Requires:**

- MiniConda / Windows PowerShell (CLI)
- Python 3.11+
- Ultralytics YOLOv8, PyTorch

## Kaggle Dataset used:

[**Road Vehicle Images Dataset**](https://www.kaggle.com/datasets/ashfakyeafi/road-vehicle-images-dataset/data)

## 🚀 Training Commands

## To Train Your Own Dataset

Steps:

1. Prepare dataset in **YOLO format** (images + labels in `.txt` files).
    
    ```
    dataset/
    ├── train/
    │   ├── images/
    │   └── labels/
    └── valid/
        ├── images/
        └── labels/
    ```
    
2. Create `data.yaml`:
    
    ```yaml
    train: images/train
    val: images/val
    nc: 21   # number of classes
    names: ['ambulance', 'army vehicle', 'auto rickshaw', 'bicycle', 'bus', 'car', 'garbagevan', 'human hauler', 'minibus', 'minivan', 'motorbike', 'pickup', 'policecar', 'rickshaw', 'scooter', 'suv', 'taxi', 'three wheelers -CNG-', 'truck', 'van', 'wheelbarrow']
    ```
    
3. Train:
    
    ```bash
    yolo detect train data=data.yaml model=yolov8n.pt epochs=20 imgsz=640
    
    ```
    
4. Evaluate & Inference:

    After training successfully, 
    
    ```bash
    # Evaluate model
    yolo val model=runs/detect/train/weights/best.pt data=data.yaml
    ```

5. Predict on a YouTube video (default show/save):
    
    ```bash
    yolo predict task=detect model=runs/detect/train/weights/best.pt source='https://youtu.be/VIDEO_ID'
    ```
![output](https://github.com/user-attachments/assets/11bd2611-e3e2-449e-b521-b0757a1bcc8d)

![output](https://github.com/user-attachments/assets/e462826b-97a6-4876-aef9-7f586063a08d)

Performed these steps on some of the traffic YouTube videos

output videos are stored [here](https://drive.google.com/drive/folders/1NX8nJA103o93LuH2EZuBW1qzkjnIpvHZ?usp=sharing).
