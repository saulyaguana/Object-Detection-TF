# Image Classification VS Object Detection
## Image Classification

An image classification network always outputs a fixed number of output labels. For an image classification network
the output is always the same length vector. The result of an image classification network is a single class label.

+ Image classification predicts which objects is in the image

## Object Detection

In image classfication, for the intire image we have a single class label, in object detection we want to localize
our object of interest, we put a bounding box around the object of interest.

### How do we represent a bounding box?

We represent a bounding box using four numbers:

| class | Xmin | Ymin | Xmax | Ymax |
| :---: | :---: | :---: | :---: | :---: |
| 2: Panda | 50 | 10 | 220 | 290 |

Where Xmin adn Ymin represents the upper left corner and Xmax and Ymax represents the lower right corner.
These two points there could be many different representations like the following:

| class | Xmin | Ymin | w | h |
| :---: | :---: | :---: | :---: | :---: |
| 2: Panda | 50 | 10 | 170 | 280 |

There is another representation that are used in YOLO models:

| class | Xc | Yc | w | h |
| :---: | :---: | :---: | :---: | :---: |
| 2: Panda | 135 | 150 | 170 | 280 |

+ Object detection predicts where the object is in the image

# Classification and Regression with a Single Neural Network

The output in object detection consists of a collection of bounding boxes and for each bounding box we have
a class label.

Finding bounding box coordinates is a regression problem while assigning a label is a classification problem.

For solving an object detection problem we first extarct features using a bank of colvolutional layers and then
use these features to solve two problems:

1. Image classification problem to assign labels
2. Bounding box coordinate regression problem

# Encoding bounding box

We will consider a detector capable of finding four objects:

1. Elephant (class 1)
2. Tiger (class 2)
3. Dog (class 3)
4. Zebra (class 4)
5. Background (class 0)

When building an object detector you need to have an extra class to capture the background in our case the
background is anything that is not an elephant, tiger, dog or zebra.

A naive and straightforward way to create bounding boxes is to divide the entire image into a three by three grid,
so we can only detect nine objects at these fixed location, that's not perfect but it's a start.

The object detector needs to perform two tasks:

1. For every grid location we need to identify the object inside it. We need to perform image classification
for every grid location.
2. Fix the size of the bounding boxes

If we do these two things we will at least get an object detector that can detect a maximum of nine objects
that are not overlapping, still not perfect, but better than before.

## Obtaining the Feature Map

We can build a bank of convolutional layers that can shrink the size of 3x600x600 tensor to 64x3x3 tensor.

In this case, the last convolutional layer will be 64x3x3, a single pixel in this 3x3 image comes from a 200x200
region in the original image. For every pixel in the 3x3 image we have 64 numbers.

This 64 element feature vector can be used for calssifying the 200x200 region of the image, we will know
which object is in a single cell.

Now, we need to convert the 64 channel 3x3 image to a 5 channel 3x3 image where each channel will encode the
probability of the five classes. Recall whenever we want to change the depth of the tensor we don't want to
change the width and height of the tensor, in that case we use only 1x1 convolution filters.

Whenever you want to change the depth of a tensor without changing its width and height you can use 1x1
convolution filters and the number of convolution filters you use is equal to the new depth you want