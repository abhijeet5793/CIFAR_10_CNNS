# Using Convolutional Neural Netowrks and Data Augmentation on CIFAR-10

## Background

As part of a data science bootcamp, we (Abhijeet Kamble and Anmol Srivats) decided to do a project where we used deep learning via Convolutional Neural Networks (CNNs), to classify images in the CIFAR-10 dataset. In the description of the dataset, it said that a paper got to 82% accuracy without data augmentation, and 89% with data augmentation, so we were chasing these two targets. 

## Data

The CIFAR-10 dataset contains 60,000 32x32 images in 10 different categories. The training set contains 50,000 images, and the testing set contains 10,000. Both the training and testing set have an equal number of images in each of the categories. We first split the training set into a training and validation set, to test our model, but run our final model using the full training set, and verifying it on the testing set. 

## Inital Model Architecture

After experimentation with many different architectures in Keras, we used a convolutional neural net with 8 3x3 filter convolutional layers, followed by two dense layers, and finally the softmax activation on the output layer. For regularisation, we used both drop out and L2 regularisation. We used the RELU activation function, and binary categorical crossentropy loss. With this model, we achieved around 83% accuracy on the validation set after 200 epochs, 1% better than the paper!

## Data Augmentation

We read that the model tends to overfit to certain orientations in the training set. For example, it is generally used to a particular object being in the centre of the image. To solve this problem, people use data augmentation- randomly moving the image up or down, or shifting it left or right, or rotating/reflecting it, so that your model learn to generalise better on the training set. 

## Final Results 

We used our earlier architecture on the augmented dataset, but were still at only around 83% accuracy after 100 epochs. This was not an improvement form our earlier model. However, when we passed the original training data through our model- the accuracy immediately jumped to 85% after one epoch. This suggests that after learning the general rules of how to identify certain images, the model received an immediate accuracy boost when seeing 'clean' data. 

Furthermore, we realised that regularisation is not required in this architecture, as the random shifts/rotations provide a regularising effect. We then made our model do 10 epochs on augmented data - 1 epoch on the original data, and repeated this process 20 times. This gave us a final accuracy of 87.5%, only 1.5% worse than the paper. 

1

234
