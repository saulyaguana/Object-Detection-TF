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