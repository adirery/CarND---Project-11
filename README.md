# CarND Semantic Segmentation Project

## Introduction
In this project the goal was to implement semantic segmentatation of an image classifying each pixel into road - non-road. The basis for this project was Long / Shelhamer / Darrell's paper on Fully Convolutional Networks (https://people.eecs.berkeley.edu/~jonlong/long_shelhamer_fcn.pdf).
The paper describes an architecture that builds on top of VGG16 and extends it with 3 upsampling layers and feedforward structures. 
This project implements this architecture and consequently trains the model on the Kitti dataset. The network is shown below:
![FCN8](https://github.com/adirery/CarND---Project-11/blob/master/supporting_pictures/FCN8_Overview.PNG)

## Kitti Dataset
The dataset consists of 289 training and 290 test images. It contains three different categories of road scenes:
- uu - urban unmarked (98/100)
- um - urban marked (95/96)
- umm - urban multiple marked lanes (96/94)

## Tuning hyperparameters
|Parameter |Value  |Description|
|:---------|:------|:----------|
|Learning Rate|1e-4|The`Adam` optimizer was used and based on the low amount of pictures the lower learning rate of the normally suggested (1e-3 or 1e-4) was chosen.|
|Number of epochs|15|The training dataset is quite small, so in order to not overfit a moderate number of epochs was chosen.|
|Batch Size|8|Trial & error.|
|std-dev 1x1 conv|0.001|Trial & error.|
|std-dev upsample|0.01|Trial & error.|
|l2-regularization|0.001|Trial & error.|

## Results
Although with 300 training images the network already performs quite good, there's still a lot of room for improvement. Interestingly the L2-regularization & kernel initialization tunings led to the best results ultimately, i.e. prior to that the full image was classified whereas with regularization the results were much better. Below some sample images after inference

![sample_image_0](https://github.com/adirery/CarND---Project-11/blob/master/sample_pictures/uu_000094.png)
![sample_image_1](https://github.com/adirery/CarND---Project-11/blob/master/sample_pictures/um_000013.png)
![sample_image_2](https://github.com/adirery/CarND---Project-11/blob/master/sample_pictures/umm_000057.png)


## Outlook
The network is final, however the training can be optimized:
- Data Augmentation: https://datascience.stackexchange.com/questions/5224/how-to-prepare-augment-images-for-neural-network
- Larger dataset: https://www.cityscapes-dataset.com/
