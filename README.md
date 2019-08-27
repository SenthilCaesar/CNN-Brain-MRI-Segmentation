# CompNet - Keras Implementation

## Tool:CompNet: Segmenting diffusion brain MRI

The code for training, as well as the Trained Models are provided here

> Model Architecture: https://drive.google.com/open?id=1XlNhAjX0eg6Omz61nWfx090oGCfepw7l

> Trained Model Weights: https://drive.google.com/open?id=1FRsDkVzQDjrR3kM3hGZ6iAlSyQuKrvOs

Let us know if you face any problems running the code by posting in Issues.

If you use this code please cite:

Raunak Dey, Yi Hong, C.2018 CompNet: Complementary Segmentation Network for Brain MRI Extraction . Accepted to MICCAI 2018 https://arxiv.org/abs/1804.00521

Guha Roy, A., Conjeti, S., Navab, N., and Wachinger, C. 2018. QuickNAT: A Fully Convolutional Network for Quick and Accurate Segmentation of Neuroanatomy. Accepted for publication at NeuroImage, https://arxiv.org/abs/1801.04161

## Getting Started

### Pre-requisites

You need to have following in order for this library to work as expected

1)  python 2.7
2)  pip >= 19.0
3)  numpy >= 1.14.0
4)  nibabel >= 2.2.1
5)  nilearn >= 0.5.0
6)  opencv-python >= 3.4.1.15
7)  pandas >= 0.23.0
8)  scikit-image >= 0.13.1
9)  scikit-learn >= 0.20.0
10) tensorflow >= 1.8.0
11) tensorflow-gpu >= 1.8.0
12) keras >= 2.1.6
13) cudatoolkit = 9.0
14) cudnn = 7.0.5

### Code Author
* Raunak Dey - [raun1](https://github.com/raun1)
### Model Architecture
The proposed networks are designed in the framework of encoder-decoder networks and have three pathways.
> 1) Segmentation Branch - learns what is the brain tissue and to generate a brain mask 
> 2) Complementary Branch - learns what is outside of the brain and to help the other
branch generate a better brain mask
> 3) Reconstruction Branch - It provides direct feedback to the segmentation and
complementary branche and expects reasonable predictions from them as input to reconstruct the original input image.
![Screenshot](https://github.com/SenthilCaesar/CNN-Brain-MRI-Segmentation/blob/master/CompNet%20Arch.png)


### Multi View Aggregation step:
> The approach is to train 3 separate networks for three principal axes ( Sagittal, Coronal and axial ) and 
to perform multi-view aggregation step that combines segmentations from models trained on 2D slices along three principal axes: coronal, sagittal and axial. The final segmentation would be obtained by combining the probability maps from all three segmentation.
![Screenshot](https://github.com/SenthilCaesar/CNN-Brain-MRI-Segmentation/blob/master/Multiview.png)
