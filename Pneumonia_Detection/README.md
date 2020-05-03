# Pneumonia Detection

Medical applications are amongst the fastest growing areas of application of deep learning today. Clinical screening offers a particularly exciting field of use as automated, or semi-automated, systems could massively increase the numbers of people who can be screened. In this assignment we will build machine learning models to detect pneumonia from chest x-ray images.

![image](https://user-images.githubusercontent.com/26432753/80917859-7dc6ae80-8d59-11ea-8427-938a7def574f.png)

To classify the images I have used 4 major models. Comparing each models accuracy and other important aspetcs:


![image](https://user-images.githubusercontent.com/26432753/80918096-08f47400-8d5b-11ea-933e-47c81bd0f046.png)



| Model | Accuracy on Train Data| Accuracy on Test Data
|------|------|------|
| Logestic Regression | 100 | 81.45 |
| LeNet5 CNN | 95.02 | 74.19 |
| LeNet5 CNN with Aug | 85.52 | 76.61 |
| VGG16 | 98.92 | 72.58 | 


__1. LogReg__:

* As a base model, we used Logistic Regression model to determine whether or not a given X-ray has pneumonia or not. It is relatively an easy model to implement as we treat each pixel as distinct feature.

* We have also converted the images to grayscale as color images have 3 channels which increases the model complexity (Number of features) and doesn't improve the predictive power. Also the images were reshaped to the desired size of (162, 128). Here is how the gray scale images look like:

![image](https://user-images.githubusercontent.com/26432753/80918152-54a71d80-8d5b-11ea-9c06-fd7be0fbc95e.png)


* The Logistic Regression classifier gives 100% accuracy on training data set while it could only give 81.45% on the testing dataset. Since the dataset is highly imbalanced and majority class is of pnueumonia we are getting higher accuracy. The model got overfitted.

__2. LeNet5 CNN:__

Architecture:

![image](https://user-images.githubusercontent.com/26432753/80918178-88824300-8d5b-11ea-9089-dc4c5ac42a56.png)

* LeNet-5 is one of the simplest architectures. It has 2 convolutional and 3 fully-connected layers.

* We selected 'adam' as the optimizer with learning rate of 0.0001. The sub-sampling layer used is average-pooling with trainable weights.

* __Unbalanced Dataset:__
    
    * Initially we trained the model on the unbalanced dataset. The model has an accuracy of 95.02% on training data set and 74.19% on testing dataset.
    * Even though the overall accuracy is lower than that of the Logistic Regression, it was capable of classifying the patients more accurately based on their chest X-ray images. True Negatives are also clearly visible through the confusion matrix to a certain extent.
    
* __Balanced Dataset:__
    
    * The class_weights are set to 'balanced' in order to sample the data. Here, the model accuracy decreases to 64% in case of test dataset. This was an unsual behaviour, because mostly after balancing the dataset we should intuitively get more accurates results due to low bias.
    
    * This model performed well in comparison to Logistic Regression model but not as good as LeNet 5 model which when trained on unbalanced dataset. However there was a significant difference of 10% in accuracy in terms of performance on test dataset.
    
__3. LeNet5 Augmentation:__

Images after data augmentation:

![image](https://user-images.githubusercontent.com/26432753/80918188-a51e7b00-8d5b-11ea-91e2-164e3286dd32.png)


* This model performs best in terms of accuracy when tested on test dataset. The target classes are clearly distinguished, clearly visible from Confusion Matrix.

* In order to increase the size of the training dataset, number of Augmentation transformations are applied on the dataset.

* The ModelCheckpoints helped us to save the model by monitoring a specific parameter (val_loss, accuracy) of the model.

* Initially the model was converging to a certain value (74.29). But after introducing the learning rate and dense layer, the accuracy got boosted. The following transformations have been applied on the dataset.
    * Rotation: A rotation augmentation randomly rotates the image clockwise by a given number of degrees(15). 
    
    * Width shift: Moving pixel horizontally while keeping the image dimension same. 
    
    * Height shift: Moving pixel vertically while keeping the image dimension same. 
    
    * Zoom: A zoom augmentation randomly zooms the image in and either adds new pixel values around the image or interpolates pixel values respectively.
    
    * Fill mode: Points outside the boundaries of the input are filled according to the given mode. 
    
* We even tried with Brightness but it degraded the accuracy badly, as X-ray images are very sensitive to saturation level.

* The overall accuracy on the training dataset comes out to be 85.52% and 76.61% on testing data with Augmented data. 

* The most useful thing about ImageDatagenerator class is i,t doesn’t affect the data stored on the disk. It simply alters the data on the go while passing it to the model.

* Data augumentation enhances the training of CNN model. The model gets multiple variant of a single training data due to which it learns the main features. Networks trained with just data augmentation more easily adapt to different architectures and amount of training data, as opposed to weight decay and dropout, which require specific fine-tuning of their hyperparameters.

__4. VGG16:__

![image](https://user-images.githubusercontent.com/26432753/80918240-e4e56280-8d5b-11ea-888d-b234a7ee1dbe.png)


* The most unique aspect about VGG16 is that instead of making a huge number of hyper-parameters, it concentrated on providing 3x3 convolution layers with a stride 1 filter and only using the same padding and maxpool layer with a 2x2 stride 2 filter.

* Since we have less data available with us to train the model, we used VGG as a transfer learning platform. This allow us to just add the final fully connected layers and test the model on the testing data.

* Here, We achieved the accuracy of 72.58% on testing and 98.89% on training dataset. The model was capable of finding few of True Negatives as well.

* VGG has very high memory consumption and takes maximum time to train the model but since we are only using the last few layers of VGG16, It proves to be less computationally expensive.


## References

[1] Cs229.stanford.edu. 2020. [online] Available at: <http://cs229.stanford.edu/proj2017/final-reports/5231221.pdf> [Accessed 1 May 2020].
        
[2] Ieeexplore.ieee.org. 2020. Pneumonia Detection Using CNN Based Feature Extraction - IEEE Conference Publication. [online] Available at: <https://ieeexplore.ieee.org/document/8869364> [Accessed 1 May 2020].
