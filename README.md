# Bodyfat Percentage Calculator Using Computer Vision
Measure your body fat percentage with just a single picture!

## Installation
### Using virtual environment
This code has been tested on Ubuntu, PyTorch 1.2, Python 3.6 and Nvidia GTX 940MX. It is recommended to setup a python virtual environment 
and install the following packages.

1. Clone the repo
2. Install the below:
   ```
   apt-get install tk-dev python-tk
   ```

3. Activate the virutal Install the required python packages in a virtual environment

   ```
   (pytorch)$ pip3 install torch torchvision 
   (pytorch)$ pip3 install scikit-image opencv-python pandas h5py
   (pytorch)$ pip3 install cffi
   (pytorch)$ pip3 install cython
   (pytorch)$ pip3 install requests
   (pytorch)$ pip3 install future
   ```
3. Build the NMS extension

   ```
   cd lib/
   python3 setup3.py build_ext --inplace
   ```
## Usage
### Run a demo
## Body Fat Percentage Estimation via Python Script

This repository provides a Python script and related resources to estimate your body fat percentage based on a single image.

### Overview

1. **Model**: Uses a monocular depth estimation network and a RetinaNet object detection model to extract body measurements from an image.
2. **Calculation**: Applies the Navy body fat formula to measurements for estimating body fat percentage.
3. **Requirements**: Python 3 with PyTorch, OpenCV, and related libraries.

### Getting Started

1. **Prepare an image:** Take a photo with your neck and waist clearly visible, standing at least 1 meter from the camera (see example). Save the image in the `data/inputs` directory.
2. **Run the script:** Open a terminal in the repository directory and execute the following command, replacing `<name_of_your_image>.jpg` with your image filename:

```bash
python3 measure_body.py --image_name <name_of_your_image>.jpg
```

3. **View results:** The script will print your estimated body fat percentage and potentially visualize various stages of the process.

### Technical Details

The script leverages two models:

* **Monocular depth estimation network:** Based on the CVPR 2019 paper "Learning the depths of moving people by watching frozen people," it predicts pixel-level depth maps from the image.
* **RetinaNet object detection model:** Fine-tuned to identify and locate body parts (neck and waist) in the image.

Both networks are implemented using PyTorch. Additional data, including camera intrinsics from image metadata, is also used for accurate body measurement and fat percentage calculation.

### Acknowledgements

This project integrates code from several valuable sources:

* Depth estimation: [https://github.com/google/mannequinchallenge](https://github.com/google/mannequinchallenge) (paper: [https://github.com/google/mannequinchallenge](https://github.com/google/mannequinchallenge))
* RetinaNet: [https://github.com/yhenon/pytorch-retinanet](https://github.com/yhenon/pytorch-retinanet)
* NMS: [https://github.com/FrancescoSaverioZuppichini/non-max-suppression-in-pytorch](https://github.com/FrancescoSaverioZuppichini/non-max-suppression-in-pytorch)

### Contributing

Feel free to fork the repository, improve the script, or suggest features. Pull requests with detailed explanations and relevant tests are welcome!

### Disclaimer

This script provides an estimate of body fat percentage for informational purposes only. It is not a substitute for professional medical advice. 




