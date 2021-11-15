# dark-image-enhancement-Pix2Pix
This objective is to switch light conditions / enhance color for dark images. In general, there are three types of machine learning techniques which can be used to enhance image color: 
1. supervised learning models based on paired dark/light images; 
2. unsupervised learning style transfer models based on one stack of dark images and the other stack of light images; 
3. reinforcement learning to learn steps to adjust brightness, sharpness, or contrast. 

This project implements the Pix2Pix model, which uses [U-Net](https://arxiv.org/abs/1505.04597) as the image generator to produce estimated light images. Structured like the contracting path of the U-Net, the PatchGAN discriminator tells how much the estimated images are close to the real light images. Generator loss consists of adversarial loss and reconstruction loss while discriminator loss includes the difference between contracted real images and ones-arrary, and the difference between conratcted generated fake images and zeros-array.

Mandatory python packages:
- torch (cpu/cuda)
- torchvision
- PIL
- matplotlib

<p align="center">
  <img src="./img-to-img.png" width=600>
</p>

## Training Images

The training dataset includes 170 paired augmented dark/light toy images taken by mobile phone with a fixed ISO value. 

<p align="center">
  <img src="./trainset.png" width=600>
</p>


## Testing Images

After training 8500 steps, the model generated good estimations for training images. Then 3 new images are used for testing. The color is indeed lighten as expected. What surprises is the shadow of the toy in the image is also estimated by Pix2Pix model. As we can see, the shadow doesn't exist in the dark image and only appears in the light image because the light is turned on when taking the photo. Although the shape of generated shadow is not exactly the same with the shadow in the real image, it's pretty close. It's believed that the generated image quality can be even improved by adding more training images and traing more epochs.

<p align="center">
  <img src="./test_results.png" width=600>
</p>
