# Deep face segmentation in extremely hard conditions
![alt text](https://yuvalnirkin.github.io/assets/img/projects/face_segmentation/face_segmentation_samples.jpg "Samples")  
COFW sample images segmented using our method.

[Yuval Nirkin](http://www.nirkin.com/), [Iacopo Masi](http://www-bcf.usc.edu/~iacopoma/), [Anh Tuan Tran](https://sites.google.com/site/anhttranusc/), [Tal Hassner](http://www.openu.ac.il/home/hassner/), and [Gerard Medioni](http://iris.usc.edu/people/medioni/index.html).

## Overview
This project provides an interface for face segmentation using Caffe with a fully connected convolutional neural network.
The network was trained on IARPA Janus CS2 dataset (excluding subjects that are also in [LFW](http://vis-www.cs.umass.edu/lfw/)) using a novel process for collecting ground truth face segmentations, involving our tool for [semi-supervised Face video segmentation](https://github.com/YuvalNirkin/face_video_segment). Additional synthetic images were generated by augmenting hands from the [EgoHands dataset](http://vision.soic.indiana.edu/projects/egohands/), and augmenting 3D models of glasses and microphones.

If you find this code useful, please make sure to cite our paper in your work:

Yuval Nirkin, Iacopo Masi, Anh Tuan Tran, Tal Hassner, Gerard Medioni, "[On Face Segmentation, Face Swapping, and Face Perception](https://arxiv.org/abs/1704.06729)", arXiv preprint arXiv:1704.06729, 22 Apr 2017

Please see [project page](http://www.openu.ac.il/home/hassner/projects/faceswap/) for more details, more resources and updates on this project.

## Dependencies
| Library                                                            | Minimum Version | Notes                                    |
|--------------------------------------------------------------------|-----------------|------------------------------------------|
| [Boost](http://www.boost.org/)                                     | 1.47            |Optional - For command line tools         |
| [OpenCV](http://opencv.org/)                                       | 3.0             |                                          |
| [Caffe](https://github.com/BVLC/caffe)                             | 1.0             |☕️                                        |

## Installation
- Use CMake and your favorite compiler to build and install the library.
- Download the [face_seg_fcn8s.zip](https://github.com/YuvalNirkin/face_segmentation/releases/download/1.0/face_seg_fcn8s.zip) and extract to "data" in the installation directory.
- Add "bin" in the installation directory to path.

## Usage
- For using the library's C++ interface, please take a look at the [Doxygen generated documentation](https://yuvalnirkin.github.io/projects/face_segmentation/).
- For python go to "interfaces/python" in the installation directory and run:
```BASH
python face_seg.py
```
- For running the segmentation on a single image:
```BASH
cd path/to/face_segmentation/bin
face_seg_image ../data/images/Alison_Lohman_0001.jpg -o . -m ../data/face_seg_fcn8s.caffemodel -d ../data/face_seg_fcn8s_deploy.prototxt
```
- For running the segmentation on all the images in a directory:
```BASH
cd path/to/face_segmentation/bin
face_seg_batch ../data/images -o . -m ../data/face_seg_fcn8s.caffemodel -d ../data/face_seg_fcn8s_deploy.prototxt
```
- For running the segmentation on a list of images, first prepare a file "img_list.txt", in which each line is a path to an image and call the following command:
```BASH
cd path/to/face_segmentation/bin
face_seg_batch img_list.txt -o . -m ../data/face_seg_fcn8s.caffemodel -d ../data/face_seg_fcn8s_deploy.prototxt
```

## Important note
In our paper we used a different network for our face segmentation. In the process of converting it to the Caffe model used in our [end-to-end face swap distribution](https://github.com/YuvalNirkin/face_swap) we notices some performance drop. We are working to fix this. We therefore ask that you please check here soon for updated on this Caffe model. 


## Related projects
- [End-to-end, automatic face swapping pipeline](https://github.com/YuvalNirkin/face_swap), example application using out face segmentation method.
- [Interactive system for fast face segmentation ground truth labeling](https://github.com/YuvalNirkin/face_video_segment), used to produce the training set for our deep face segmentation.
- [CNN3DMM](http://www.openu.ac.il/home/hassner/projects/CNN3DMM/), estimation of 3D face shapes from single images.
- [ResFace101](http://www.openu.ac.il/home/hassner/projects/augmented_faces/), deep face recognition used in the paper to test face swapping capabilities. 

## Copyright
Copyright 2017, Yuval Nirkin, Iacopo Masi, Anh Tuan Tran, Tal Hassner, and Gerard Medioni 

The SOFTWARE provided in this page is provided "as is", without any guarantee made as to its suitability or fitness for any particular use. It may contain bugs, so use of this tool is at your own risk. We take no responsibility for any damage of any sort that may unintentionally be caused through its use.
