# Anime-Video-Generator
Pose guided Anime Video Generator using Deep Learning. Its a self project created being inspired by StyleGAN2, PSGAN and Unsupervised Image-to-Image translation.

## Idea and Goal

The Idea behind this project is to generate Anime video (Target Video) from corresponding real time human video (Source Video). 
The Idea is split into three parts - 
  1. Split video into Frames
  2. Extract the pose sequence from each frame.
  3. Generate the Anime character corresponding to each pose.
 

## Pose sequence extraction

This part deals with the Human pose estimation. Human Pose Estimation is defined as the problem of localization of human joints in images or videos. This represents the orientation of the person in that frame. So, graphically, human pose represents the coordinates of joints ( Elbow, knee, wrist, etc) based on person orientation. 
It can be of two types - 
    2D Pose Estimation - Estimate a 2D pose (x,y) coordinates for each joint from a RGB image.
    3D Pose Estimation - Estimate a 3D pose (x,y,z) coordinates from a RGB image.

Human pose estimation is a heated topic now day as it has a wide application like gaming, security survelliance, animation etc. There are several approaches for pose estimation using Deep learning like OpenPOSE, DensePOSE and MaskRCNN, etc.      


## High resolution Anime Image synthesis from Pose Sequence


## Related Work

### Image to Image translation


### Video to Video translation
