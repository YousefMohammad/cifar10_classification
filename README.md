# Cifar10 Classification

## Introduction
The CIFAR-10 small photo classification problem is a standard dataset used in computer vision and deep learning.
Although the dataset is effectively solved, it can be used as the basis for learning and practicing how to develop, evaluate, and use convolutional deep-learning neural networks for image classification from scratch.
This includes how to develop a robust test harness for estimating the model's performance, how to explore improvements to the model, and how to save the model and later load it to make predictions on new data.

<img src="https://github.com/YousefMohamedSalah/cifar10_classification/assets/99505074/ea380263-4790-4a8b-929b-90a266c59056" align="right"/><br clear="left"/>

## Dataset
The CIFAR-10 dataset consists of 60000 32x32 color images in 10 classes, with 6000 images per class. There are 50000 training images and 10000 test images.

The dataset is divided into five training batches and one test batch, each with 10000 images. The test batch contains exactly 1000 randomly selected images from each class. The training batches contain the remaining images in random order, but some training batches may contain more images from one class than another. Between them, the training batches contain exactly 5000 images from each class. 

<br/><br/><br/>

## Data Wrangling
the images all have the same square size of 32×32 pixels. Therefore, we can load the images and use them for modeling almost immediately.

We also know that there are 10 classes and that classes are represented as unique integers.

We can, therefore, use a one-hot encoding for the class element of each sample, transforming the integer into a 10-element binary vector with a 1 for the index of the class value. We can achieve this with the to_categorical() utility function.


## Data Preparation
We know that the pixel values for each image in the dataset are unsigned integers in the range between no color and full color, or 0 and 255.

We do not know the best way to scale the pixel values for modeling, but we know that some scaling will be required.

A good starting point is to normalize the pixel values, e.g. rescale them to the range [0,1]. This involves first converting the data type from unsigned integers to floats, and then dividing the pixel values by the maximum value.


## Model Evaluation
The design of the test harness is modular, and we can develop a separate function for each piece. This allows a given aspect of the test harness to be modified or interchanged, if we desire, separately from the rest.

We can develop this test harness with five key elements. They are the dataset's loading, the dataset's preparation, the model's definition, the model, the evaluation of the model, and the presentation of results.
The design of the test harness is modular, and we can develop a separate function for each piece. This allows a given aspect of the test harness to be modified or interchanged, if we desire, separately from the rest.

We can develop this test harness with five key elements. They are the dataset's loading, the dataset's preparation, the model's definition, the model, the evaluation of the model, and the presentation of results.

## Baseline Results
A figure is created and saved to a file showing the learning curves of the model during training on the train and test dataset, both concerning the loss and accuracy.

In this case, we can see that the model rapidly overfits the test dataset. This is clear if we look at the plot of loss (top plot), we can see that the model’s performance on the training dataset (blue) continues to improve whereas the performance on the test dataset (orange) improves, then starts to get worse at around 15 epochs.

## Improved Model Results
In this case, we can see that we achieved a further lift in model performance to about 84% accuracy.
Reviewing the learning curves, we can see the training of the model shows continued improvement for nearly the duration of 100 epochs.
The model is now learning well, and we have good control over the rate of learning without overfitting.

## Final Results
Once the model has been evaluated, we can present the results.
There are two key aspects to present: the diagnostics of the learning behavior of the model during training and the estimation of the model performance.
First, the diagnostics involve creating a line plot showing model performance on the train and test set during training. 
These plots are valuable for getting an idea of whether a model is overfitting, underfitting, or has a good fit for the dataset.
We will create a single figure with two subplots, one for loss and one for accuracy. 
The blue lines will indicate model performance on the training dataset and the orange lines will indicate performance on the hold-out test dataset. 
the plot given the collected training histories. The plot is saved to a file, specifically a file with the same name as the script with a ‘png‘ extension.
A figure is created and saved to a file showing the learning curves of the model during training on the train and test dataset, both concerning the loss and accuracy.

