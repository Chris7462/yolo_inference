# YOLO Inference C++ Library

The source code for this repository is copied from the Ultralytics examples: [YOLOv8-CPP-Inference](https://github.com/ultralytics/ultralytics/tree/main/examples/YOLOv8-CPP-Inference). I made some changes to convert the inference into a library so that the yolo_object_detection can directly call the API.

## Install Ultralytics
To install Ultralytics, the easiest way is to use `pip`. To avoid messing up the system, it's recommended to create a Python virtual environment to handle the package dependencies.
```bash
cd ~
python3 -m venv .ultralytics
source ~/.ultralytics/bin/activate
```
Pip install the ultralytics package including all requirements
```bash
pip3 install ultralytics
```

## Exporting YOLOv5 and YOLOv8 Models
First, download the YOLO models from the following links:
- [YOLOv5s](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5s.pt)
- [YOLOv8s](https://github.com/ultralytics/assets/releases/download/v8.2.0/yolov8s.pt)

Here, we use YOLOv5s and YOLOv8s as examples. In theory, this library should work for YOLOv6 and YOLOv7 as well, but they have not been tested.

Other YOLOv5 and YOLOv8 models can be found on Ultralytics' GitHub pages for [YOLOv5](https://github.com/ultralytics/yolov5?tab=readme-ov-file) and [YOLOv8](https://github.com/ultralytics/ultralytics?tab=readme-ov-file).

To export YOLOv5 models:
```
yolo export model=yolov5s.pt imgsz=480,640 format=onnx opset=12
```

To export YOLOv8 models:
```
yolo export model=yolov8s.pt imgsz=480,640 format=onnx opset=12
```
Note that the example networks are exported with rectangular (640x480) resolutions, but any exported resolution will work. A yolov5s.onnx and yolov8s.onnx file will be generated. Move them to the appropriate folder for your use case.

When you are finished with the virtual environment, you can simply deactivate it:
```bash
deactivate
```
