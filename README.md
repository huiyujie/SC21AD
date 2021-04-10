To run the experiments that in the paper, three parts are included. 
##Experiments on NovuTesnor
./complex_yolo --model *novu_model* --base *folder_of_datasets* --split *split_file_of_data_selected* --mode *running_mode*

The Novutensor model needs to be built from NovuMind's comipler and NovuSDK is required to run the inference tasks on NovuTensor. The base folder is the KITTI dataset base directory. Each line of the split file is the name input data. The mode parameter can be 0 or 1, which indicates the pipeline mode or sequencial mode.

##Experiments on Nvidia Xavier
./xavier-yolo --split *split_file_of_data_selected* --precision *INT8/FP16/FP32* --deviceType *kGPU* --batch_size *batch* 

To evaluate the performance of Nvidia Xavier, TensorRT is required. TensorRT is a runtime library for efficient inference tasks on Nvidia's devices. 

##Preprocessing Experiments

./bev *base_folder* *split_file*

To evaluate the preprocessing latency, there is no specific hardware requirement for this program. The latency of preprocessing with different optimizations and different encoded resolutions will be displayed.