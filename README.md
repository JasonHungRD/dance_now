# dance_now
# Everybody Dance Now Anime Avatar version
### Context

Following the  "[Everybody Dance Now](https://github.com/topics/everybody-dance-now)" topic, we tried to make anime character move as we move. We provided 3 sets of different [Mixamo](https://www.mixamo.com/) characters for this image generation task. 
A generator-discriminator network was built for training anime image generation from key points for each character. The network was trained on each pair of the image and the corresponding keypoints o of the character's pose. Each keypoint set should be able to generate the image of the specific anime character with the same pose.
Hope you enjoy teaching these characters to dance!

### Dataset

Data can be downloaded from [kaggle](https://www.kaggle.com/littlewayshuang/skeleton-to-anime-gan)
The images were fetched from Mixamo and resized to 512x512 size. There are more than 4000 images for each character with different poses.  The corresponding keypoints (facial features, joints, ...) were generated by [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose):
1. 70 facial keypoints
2. 25 body keypoints
3. 21 left-hand keypoints
4. 21 right-hand keypoints
Specific keypoint assignment can be found at [openpose doc file](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/master/doc/output.md)

### Usage

#### Training:

Enter directory: "dance_now/train_scripts/" and follow the order of the notebooks:
* 0.make_real_head.py: Crop 64x64 head image from given anime image according to skeleton
* 1.train_bodystick.py: train stick to body generation with multiple GPUs and save the model
* 2.cut_fake_head.py: Crop 64x64 head image from generated anime image according to skeleton
* 3_1.train_face_residue.py: Train the face residue enhancement process from raw generated face to the precise given anime face.

#### Inference:

In the root directory:
The pre-trained NN models can be found in [Drive](http://)
"inference_openpose.py" can be imported with NN models preloaded.
"try_preload.py" was provided for testing inference.

(Further Model discribed in https://hackmd.io/@usmile/Bkn9Vz-7P)

### Acknowledgements
Thanks for the opportunity provided by [Taiwan AI Academy](https://en.aiacademy.tw/) for us to form a study group of GAN. Thanks to Eric for inviting all the members to the group. Thanks to all the members: [Cloud](https://github.com/cloud-yun),[Eric](https://github.com/eric07109), [SeanLin](https://github.com/SeanLinH), [ShuYu](https://github.com/ShuYuHuang), and TA of the GAN study group.

### Inspiration
[Everybody Dance Now](https://github.com/topics/everybody-dance-now) is a topic in Github challenging for transferring ones' movement to another one. Inspired by this project, we proposed to automatically replace someone in the photo with the specific anime character with the same pose.
