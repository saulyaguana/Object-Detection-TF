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