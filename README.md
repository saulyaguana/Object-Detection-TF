# Object Detection

Object detection is one of the most importat topics in computer vision with thousands of researchers workinf on it.

We will start with the object detection problem and its challenges, we will see history and evolution
of object detection models over the years, we will also see popular datasets for object detection.

We will see how to use off-the-shelf mdoels available on _tensorflow hub_ which is a popular repository of many
different types of pre-trained models.

Like semantic segmentation, object detection is more involved than image classification because we need to provide
__location information__ for the detected objects in an image.

We will gradually introduce the the building blocks of object detection pipeline and explain concepts such as
_bounding boxes_, _anchor boxes_, _IoU metric_, _non-maximum supression_ and _performance evaluation_.

Much like image classification we don't always want to train a model from scratch, we will learn how to build a
custom object detector for using a state-of-the-art model like efficient debt from the _tfod API_

---

# Introduction to Object Detection

Image classification answers the question, _what is in this image?_, we are able to classify an image as an
image of a cat.

In certain cases when an image depicts a single object classification is enough to answer the question. There are
a lot of scenarios when we cannot say what's in the image with a single word.

## What are the challenges associated with object detection?

We can think of object detection as a two-step process:

1. Bounding boxes around objects
2. Classes or names of objects | Classify these bounding boxes into different classes

Because of this, object detection suffers from all problems associated with image classification. In addition it has
its own challenges pertaining to localization and speed execution.

## Challenges: Intra Class Variance

The objects of the same class can can look very different, and a good object detection algorithm should be able
to understand all the variations despite the differences

## Challenges: Pose Variation

The same object can be look very different in different images because of pose. It's common in computer vision
to separate possible transformations into rigid and no-rigid transformations, this separation naturally comes
from the object's properties, whether the object is rigid like a car or it can change shape and relative
position of its parts like a person

## Challenges: Occlusion

Sometimes the object we are interested in may be partially occluded by other objects, in such cases it is possible
that some defining properties of this object, some very important properties of this object may be occludedl, so it
makes the object very difficult to be identified. Sometimes occlusion can also lead the object to be broken into
two different sections in the image and we may think of the two sections as two different objects instead of a
single object.

Occlusion does create a lot of problems for us and because handling occlusion is so important in real world
applications, many detection datasets have a metric that is exclusively for occluded objects and we can separately
calculate the accuracy of the algorithm for occluded objects.

Object detection if not done right can be computationally very expensive because we have to search for the object
of interest at many different locations.

Large search space over multiple:

1. Locations
2. Scale
3. Aspect ratio