# Dataset Preparing

[KITTI](http://www.cvlibs.net/datasets/kitti/): Dataset for 3D object detection
[PASCAL-VOC](http://host.robots.ox.ac.uk/pascal/VOC/): Dataset for 2D object detection
[MSCOCO](https://cocodataset.org/#home): A large-scale object detection, segmentation, and captioning dataset.

# Application Introduction

3D object detection takes cloud points as the input. The input cloud points will be processed into a birds-eye-view(BEV) images and the images will be fed into trained neural networks. The objects on the processed images can be detected via the neural network, including cars, cyclists, and pedestrians. 

# Overview of Hardware

We deployed the 3D&2D object detection applications on NovuTensor and Nvidia Xavier, which are two Deep Learning acclerators. NovuTenosr is a PCIe-based acclerator, which needs cooperation with a host machine. Nvidia Xavier is an embedded module, which contains its own CPU, GPU, memory. 

# To run the experiments that in the paper, three parts are included. 

## Experiments on NovuTesnor
./complex_yolo --model *novu_model* --base *folder_of_datasets* --split *split_file_of_data_selected* --mode *running_mode*

The Novutensor model needs to be built from NovuMind's comipler and NovuSDK is required to run the inference tasks on NovuTensor. The base folder is the KITTI dataset base directory. Each line of the split file is the name of input data. The mode parameter can be 0 or 1, which indicates the pipeline mode or sequencial mode.

## Experiments on Nvidia Xavier
./xavier-yolo --split *split_file_of_data_selected* --precision *INT8/FP16/FP32* --deviceType *kGPU* --batch_size *batch* 

To evaluate the performance of Nvidia Xavier, TensorRT is required. TensorRT is a runtime library for efficient inference tasks on Nvidia's devices. 

## Preprocessing Experiments

./bev *base_folder* *split_file*

To evaluate the preprocessing latency, there is no specific hardware requirement for this program. The latency of preprocessing with different optimizations and different encoded resolutions will be displayed.
