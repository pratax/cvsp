# CVSP: Object Detection via Smartphone

## Detection of Forbidden and Dangerous Objects
This repository contains the work for the lecture Computer Vision Systems Programming (CVSP) 2023.
We detect twelve categories of dangerous and forbidden objects by using the following methodology as basis:
- [YOLOv5](https://github.com/WongKinYiu/yolov7/blob/main/README.md)

## Installation
This project was created and tested with python version 3.7.0, torch version 1.7.0 and cuda version 10.1.
In order to run it, first of all create a new python virtual environment by using:
```
python -m venv cvsp
cvsp/Scripts/activate
```
then, to install all the required packages, run the following command:
```
pip install -r requirements.txt
```

## Training
To run the training procedure execute the following command while inside the yolov7 directory:
```
python train.py --workers 8 --device 0 --batch-size 32 --data data/cvsp.yaml --img 640 640 --cfg cfg/training/cvsp.yaml --weights '' --name yolov7 --hyp data/hyp.scratch.p5.yaml
```

## Testing
To run the testing procedure execute the following command while inside the yolov7 directory:
```
python test.py --data data/cvsp.yaml --img 640 --batch 32 --conf 0.001 --iou 0.65 --device 0 --weights runs/train/yolov73/weights/best.pt --name ../cvsp/yolo/images/test
```

## Inference
To run inference execute the following command while inside the yolov7 directory:
```
python detect.py --weights runs/train/yolov73/weights/best.pt --conf 0.25 --img-size 640 --source ../cvsp/yolo/images/test/IMG_9791.png
```

## References
We built our project on the following repository:

[YOLOv7](https://github.com/WongKinYiu/yolov7)
```
@misc{wang2022yolov7,
      title={YOLOv7: Trainable bag-of-freebies sets new state-of-the-art for real-time object detectors}, 
      author={Chien-Yao Wang and Alexey Bochkovskiy and Hong-Yuan Mark Liao},
      year={2022},
      eprint={2207.02696},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```