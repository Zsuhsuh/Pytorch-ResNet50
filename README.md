# Pytorch-ResNet50

# Classification of fundus image lesions based on ResNet50 （Pytorch）

## Introduction to algorithm principle
> Address of thesis：https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/He_Deep_Residual_Learning_CVPR_2016_paper.pdf

### Residual net

The data output of one of the previous layers is directly introduced into the input part of the later data layer, skipping the previous layers.

This means that the content of the later feature layer will be partially linearly contributed by one of the previous layers.
<img width="941" alt="680851215c05f04d992430a5c2e8b7e" src="https://user-images.githubusercontent.com/95090256/208265995-688e5b34-d1a0-4fe4-b5a6-1860a46d06f4.png">

### Basic structure of ResNet50 model

ResNet50 has two basic blocks named Conv Block and Identity Block

The dimensions of input and output of Conv Block (number of channels and size) are different, so they cannot be continuously connected in series. Its function is to change the dimension of the network.

Identity Block Input dimension and output dimension (channel number and size) are the same, can be seriated, used to deepen the network.
![image](https://user-images.githubusercontent.com/95090256/208266022-da746080-3289-4493-ba9d-e8f565362352.png)


## Configuring the Environment

To create a python3.9 virtual environment, do the following on the command line:

```bash
conda create -n unet python==3.9
conda activate unet
```

### pytorch Installation

I have created a python3.9 environment and installed Pytorch version 1.8.0 with the following command:

```cmd
conda install pytorch==1.8.0 torchvision torchaudio cudatoolkit=10.2 # Note that this command specifies the Pytorch version and cuda version

```

### Install any other packages required for the ResNet program

The rest of the package required by the program I wrote in the 'requirements.txt' file, you just need to open the cmd in the project directory, and then execute the following command to install, ** before installation please make sure that you have activated the virtual environment **

```bash
pip install -r requirements.txt
```



## Processing of data

In order to facilitate the loading of data sets, the picture needs to be divided into training set, test set and verification set. Verification set is optional in general tasks. I have completed a section of data set division code logic, which can divide the data set according to the proportion and copy the data picture. To complete the partition of the data set. The training set accounts for 80% of the model training process, and the test set accounts for 20%.

![image](https://user-images.githubusercontent.com/95090256/208266257-de5ad365-1905-407b-a775-7df0163cd2e6.png)

![image](https://user-images.githubusercontent.com/95090256/208266261-52f19fbe-2668-47f9-8ca8-b991079270d8.png)


## Results of training

### Some predicted images with the proposed model

The ResNet50 architecture was applied to the classifier on the fundus image data set, and then the performance of the model was tested using the test images. We conducted the experiment by changing the weight of the pre-trained ResNet50 model. The proposed model has high convergence during training. In addition, the verification curve follows the training curve, indicating smooth convergence of the model. Therefore, the proposed model is fast and efficient in training, and can accurately predict the test image.

![image](https://user-images.githubusercontent.com/95090256/208266455-68ef4862-cfa5-4ac8-85a5-ad7dad236c80.png)

![image](https://user-images.githubusercontent.com/95090256/208266461-d862b192-6d51-47e9-8526-a16b890d83c4.png)


## Validation of model

After model training, we use some indicators to test the performance of the model

### Distribution of losses with the epoch number

After 200 epoch runs, the reason for the sudden increase of the 50th epoch loss is the linear probe in front, that is, the network trunk is not moving and only the linear layer is adjusted. Due to the small difference between the images and the strong professionalism of medical images, it is expected that the features cannot be captured during pre-training. The next 150 epochs mean that the whole network parameters are moving. Therefore, the loss is relatively high at the beginning and the movement is severe.

![image](https://user-images.githubusercontent.com/95090256/208266560-0b71655a-5b32-4fe1-8a3e-135a219e0e4d.png)

### Accuracy distribution in the training process

The model was instructed to begin training using a training data set consisting of actual and enhanced images. Validation is then performed to summarize the model. The following figure shows the good convergence of the proposed network during the training and validation phases. The verification accuracy reached 99.00% and the recall rate was 98.72%

![image](https://user-images.githubusercontent.com/95090256/208266567-626ec52a-cc7c-4c0a-8089-e1108d9dd6ae.png)

![image](https://user-images.githubusercontent.com/95090256/208266569-ce8f208a-7b91-4be2-bbb3-c62b8d1e007c.png)


