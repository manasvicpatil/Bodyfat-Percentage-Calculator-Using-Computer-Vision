# Bodyfat Percentage Calculator Using Computer Vision

Measure your body fat percentage with just a single picture!
# Installation
# Using a virtual environment
This code has been tested on Ubuntu, PyTorch 1.2, Python 3.6, and Nvidia GTX 940MX. It is recommended to set up a python virtual environment and install the following packages.
1. Clone the repo

2. Install the below:
apt-get install tk-dev python-tk

3. Activate the virutal Install the required Python packages in a virtual environment
```(pytorch)$ pip3 install torch torchvision``` 
```(pytorch)$ pip3 install scikit-image opencv-python pandas h5py```
```(pytorch)$ pip3 install cffi```
```(pytorch)$ pip3 install cython```
```(pytorch)$ pip3 install requests```
```(pytorch)$ pip3 install future```

4. Build the NMS extension
```cd lib/```
```python3 setup3.py build_ext --inplace```

the comparison of NMS in speed
method 1:
```thresh=0.7, time wastes:0.0287```
```thresh=0.8, time wastes:0.1057```
```thresh=0.9, time wastes:0.4204```

method 2:
```thresh=0.7, time wastes:0.0272```
```thresh=0.8, time wastes:0.1038```
```thresh=0.9, time wastes:0.4184```

method 3:
```thresh=0.7, time wastes:0.0019```
```thresh=0.8, time wastes:0.0028```
```thresh=0.9, time wastes:0.0036```

method 4:
```thresh=0.7, time wastes:0.0120```
```thresh=0.8, time wastes:0.0063```
```thresh=0.9, time wastes:0.0071```

Reference:
```py-faster-rcnn: https://github.com/rbgirshick/py-faster-rcnn/tree/master/lib/nms```

# Usage
# Run a demo
```python3 measure_body.py```
This takes a sample picture from data/inputs and predicts the body fat percentage.
Estimate your own body fat percentage!
Instructions for taking pictures
The model will estimate your neck and waist circumference to predict your body fat percentage. So your neck and waist area needs to be visible in the picture. Also, the model works best when you are standing at least 1 m away from the camera. Some examples:


Paste your picture in data/inputs/

```Run python3 measure_body.py --image_name <name_of_your_image>.jpg```
Your results will be shown on the screen.

# Working
It uses a monocular depth estimating network to produce a pixel-level depth map. This was based on the CVPR 2019 paper 'Learning the depths of moving people by watching frozen people'. At the same time, the RetinaNet object detection model was finetuned to estimate the location of your body parts. PyTorch was used for both networks. This information is combined to calculate your body measurements and body fat percentage. Some camera intrinsics from the EXIF data is also used for estimation. It uses the Navy body fat formula for calculation.


# Acknowledgments
Depth estimation code has been borrowed & modified from this repo (implementation of this awesome google AI paper).
Retinanet code has been borrowed & modified from this PyTorch implementation.
NMS code from {https://github.com/huaifeng1993/NMS}.






