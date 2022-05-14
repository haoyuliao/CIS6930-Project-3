# CIS6930-Project-3
* This project tries to do image semantic segmentation for each component of the hard drive device. Then, train pre-trained networks such as GoogLeNet and ResNet-50 to identify each component.
* The Hrad Drive Device has five components including hard disk, disk, reader, y part, and chip.
## Environmental setting recommendation
* Recommend to use Anaconda 64-bit to build the environment for applying CUDA to run GPU and used the Jupyter notebook from Anaconda to build Pytorch programs.
* Recommend to use Anaconda with the Jupyter notebook to run our programs with the same environmental setting.
* Below are folders containing each file are expressed (Folder-> Each file).

## Dataset (Unavailable in github)
 1. UB-Data: The dataset of HDD from by Meng-Lun Lee at the University of Buffalo.
 2. InputImgs: HDD images as input for the program of DatasetPreprocessV2.ipynb
 3. Mask4Classification: The mask images of HDD components as input for the program of Resnet50.ipynb and GoogLeNet.ipynb.
 4. AllMask: Mask images include background.
 5. DatasetArrV2.npy: The dataset for training and testing for program of SegmentationHDDv2.ipynb. The shape of array is [B, C, H, W] = [75, 9, 224, 224]. B is number of images, C[0:3] is the InputImgs, C[3] is the mask of hard_disk,
   C[4] is the mask of diskC[5] is the mask of the chip, C[6] is the mask of the reader, C[7] is the mask of y_part, C[8] is the mask of background. H and W is 224 by 244 of each array or the size of each image. C[0:3] is the input image, and 
   C[3:-1] is the output or target mask image.
 6. ImgsNameV2.npy: The name of the image file from the InputImgs folder. This file is the reference of DatasetArrV2.npy.
#Please DM me for dataset query.

## Programs
 1. DatasetPreprocessSaveMask.ipynb: To process the UB-Data into mask images.
 2. DatasetPreprocessV2.ipynb: To process the Inputimgs and mask images into DatasetArrV2.npy and ImgsNameV2.npy.
 3. Resnet50.ipynb: The Resnet50 classification model to classify each HDD component. Input is the mask from the Mask4Classification folder, and output is classification.
 4. GoogLeNet.ipynb: The GoogLeNet classification model to classify each HDD component, and will compare with Resnet50. Input is the mask from the Mask4Classification folder, and output is classification.
 5. PlotconfusionMatrix.ipynb: Plot the confusion matrix results of Resnet50 and GoogLeNet.
 6. SegmentationHDDv2.ipynb: The semantic segmentation model. Input is the image like InputImgs folder, and output is each component mask from the AllMask folder. 
   Also, the trained parameters of Resnet50 and GoogLeNet will be used in the SegmentationHDDv2.ipynb. The output mask from SegmentationHDDv2.ipynb will become input to both classification models to predict the probability 
   confidence of each component. With under 50% means the classification models cannot identify the component, and vice versa.
 
## TrainedModel:
 1. Resnet50EP100.pth: The Resnet50's trained parameters with 100 epoches from program of Resnet50.ipynb.
 2. GoogLeNetEP100.pth: The GoogLeNet's trained parameters with 100 epoches from program of GoogLeNet.ipynb.
 3. SegModelEP10000.pth: The semantic segmentation model's trained parameters with 10000 epoches from program of SegmentationHDDv2.ipynb.

## TrainTestImagesRes: 
 1. Segmentation: Randomly pick 2 images results of training and testing from the program of SegmentationHDDv2.ipynb.
 2. ConfusionMatrix: Classification confusion matrix results of ResNet50 and GoogLeNet.

## TrainTestLog: Training and testing records.
 1. GoogLeNetEP100.txt
 2. Resnet50EP100.txt
 3. SegmentationHDDv2EP10000.txt:
