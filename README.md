# Anime-Video-Generator
Pose guided Anime Video Generator using Deep Learning. Its a self project created being inspired by [StyleGAN2](https://arxiv.org/abs/1912.04958), [ProgressiveGAN](https://arxiv.org/abs/1710.10196) and Unsupervised Image-to-Image translation.

## Idea and Goal

Well in the current revolutionising digital world, animated videos are making a huge impact over society. Every person irrespective of their age group loves to watch animated videos because its engaging not only in terms of entertainment but also educative. As its getting day by day popular among millenials or middle class person, still there's a part of society who cannot afford such electronic gadets or have cable connection or subscriptions of TV channels, running such animated programs. So, this project Idea arise from this thought, to why not use Deep learning (especially, [Generative Adversarial Networks](https://arxiv.org/abs/1406.2661)) to design such model which can generate Animated Videos directly from Real time videos recoreded from Mobile and this available to every class of society. 

### Approach
The Idea behind this project is to generate Anime video (Target Video) from corresponding real time human video (Source Video). 
The Idea is split into three parts - 

    1. Split video into Frames
    2. Extract the pose sequence for each person from each frame.
    3. Generate the Anime character corresponding to each pose sequence.
 

## Pose Estimation

This part deals with the Human pose estimation. **Human Pose Estimation** is defined as the problem of localization of human joints in images or videos. This represents the orientation of the person in that frame. So, graphically, human pose represents the coordinates of joints ( Elbow, knee, wrist, etc) based on person orientation.

It can be of two types -

    2D Pose Estimation - Estimate a 2D pose (x,y) coordinates for each joint from a RGB image.
    3D Pose Estimation - Estimate a 3D pose (x,y,z) coordinates from a RGB image.

Human pose estimation is a heated topic now day as it has a wide application like gaming, security survelliance, animation etc. There are several approaches for pose estimation using Deep learning like [OpenPOSE](https://arxiv.org/abs/1812.08008), [DensePOSE](https://arxiv.org/abs/1802.00434) and [MaskRCNN](https://arxiv.org/abs/1703.06870), etc. As this project deals with the multiperosn in the video, more accurate the object detection model will be, higly efficient the pose estimation is. So, the idea is to use pretrained model of DensePose or OpenPose to extract the keyjoints for this task, as they have shown remarkable results till now compared to other Pose estimation approaches.       


## High resolution Anime Image synthesis from Pose Sequence

Once we have the pose, the next step is to translate those pose into a Anime character. This can be acheived in both the ways i.e. Supervised and Unsupervised. 
For supervised way, we have to prepare custom dataset of Paired images ((Pose) <-> (target Animes)) and train Deep Learning models like [Pix2Pix GAN](https://arxiv.org/abs/1611.07004), a very popular GAN architecture for Image to Image (I2I) translation. Other variant of Pix2Pix is [Pix2PixHD](https://arxiv.org/abs/1711.11585), that is capable of generating High Resolution and fine grained images. 

But for this task, best way will to use Unsupervised way, as custom dataset creation is not feaible solution. The reason behind this is that the generated anime character should preserve the sementic charactersitcs of the Input Image (i.e. it should resemble similar to the person in the video frames). Now the point is that input video can contain ***N*** number of unknown person, so to create custom dataset corresponding to them is a difficult task. So for this task, I found unsupervised learning is the better approach for Pose to Anime generation. Several research work has been published focusing on Unsupervised way of Image synthesis from a latent noise. Out of various State of the Art generative appraches Progressive Generative Adversarial Network, StyleGAN and its variant StyleGAN2 has proved to be the good choices for High resolution image synthesis. 

Apart from these, I found the paper ["Unsupervised Image-to-Image Translation via Pre-trained StyleGAN2 Network"](https://arxiv.org/abs/2010.05713) is best suited for this task. ***Huang, J et. al.*** used pre-trained StyleGAN2 model for high quality anime face generation, preserving the sementic charactersistcs of the input image. I'm also inspired by the work of ***Koichi Hamada et. al.*** for ["Full-body High-resolution Anime Generation with Progressive Structure-conditional Generative Adversarial Networks"](https://arxiv.org/pdf/1809.01890.pdf), which can be taken as a reference for this task. 



## Related Works

Some of the related state of the art works done in the past and in the recent years are mentioned below : 
1. [**DeepPose: Human Pose Estimation via Deep Neural Networks**](https://arxiv.org/abs/1312.4659) -  This was the first research that applied Deep Learning to Human Pose Estimation. The aper formulates the Pose Estimation problem as a DNN-based regression problem towards body  joints. 

        We present a cascade of such DNN regressors which results in high precision pose estimates. 
        The approach has the advantage of reasoning about pose in a holistic fashion and has a simple 
        but yet powerful formulation which capitalizes on recent advances in Deep Learning. - Alexander Toshev et. al. 

<p align="center">
  <img src="/images/deeppose.png" width=70% height=70% >
</p>  
        
        
2. [**First Order Motion Model**](https://arxiv.org/abs/2003.00196)-  This paper presents the appraoch of generating the video sequences by learning the motion using keypoints from a driving video. It uses a Deep Generative model that decouples the motion aand appearance together to generate animated videos.   
<p align="center">
  <img src="/images/fom2.gif"><span class="img_caption" style="display: block; text-align: center; font-size: 7pt;">Fig: How FOM generates image of a women turning 180 degree.</span>
</p> 

3. [**Every Body Dance Now**](https://arxiv.org/abs/1808.07371) -  This paper presents a simple approach for Motion Transfer using pose as a intermediate representation. It takes a input source video of a person dancing and based on the extracted pose, it transfers the motion to the target subject. 
<p align="center">
  <img src="/images/pose2pose.gif">
</p>



