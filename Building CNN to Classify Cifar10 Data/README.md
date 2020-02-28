# CIFAR-10 Image Classification

## Comparing the accuracy of classification using simple Feed-forward network vs CNN

### Input: Cifar10

### Output:

__Note:__ As I have limited computing power I have run only few epochs. Later I will run these models on Google colab and add those accuarcy for comparision. But for now the difference could be easily seen.

* __FeedForward Network(Without Hyperparametr Tunning):__ 38.5% (Epoch = 10)
* __FeedForward Network(With Hyperparametr Tunning):__ 36.8% (Epoch = 10)
* __CNN(without Hyperparameter Tunning):__ 63.4 % (Only 3 Epochs!)
* __CNN(with Hyperparameter Tunning):__ 68.3 % (Again only 3 Epochs!)


__Dataset:__ CIFAR is an acronym that stands for the Canadian Institute For Advanced Research and the CIFAR-10 dataset was developed along with the CIFAR-100 dataset by researchers at the CIFAR institute.

The dataset is comprised of 60,000 32×32 pixel color photographs of objects from 10 classes, such as frogs, birds, cats, ships, etc. The class labels and their standard associated integer values are listed below.

![image](https://user-images.githubusercontent.com/26432753/75552611-96031000-5a2e-11ea-8a43-d4389f13239f.png)

* 0: airplane
* 1: automobile
* 2: bird
* 3: cat
* 4: deer
* 5: dog
* 6: frog
* 7: horse
* 8: ship
* 9: truck

These are very small images, much smaller than a typical photograph, and the dataset was intended for computer vision research.

CIFAR-10 is a well-understood dataset and widely used for benchmarking computer vision algorithms in the field of machine learning.

There are 50,000 examples in the training dataset and 10,000 in the test dataset and that images are indeed square with 32×32 pixels and color, with 3 channels

## Following Tasks are Performed on the Cifar10 Dataset:
1. Loading the dataset and examining some examples.
2. Building a simple feed-forward neural network by flattening the input image into 3072 input features.
3. Evaluating the performance of feed-forward neural network on training and test sets.
4. Experimenting different feed-forward model sizes and layers.
5. Building convolution network.
6. Evaluating the performance of CNN on training and test sets.
7. Experimenting different CNN model sizes and layers.

## Conclusion:

It is clear that a CNN outperforms simple feed-forward neural network. Even few epochs in CNN have more accuracy then that of feed-forward neural network. Hence CNN is a better way to handle images related classification.
