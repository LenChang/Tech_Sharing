# Overview
> We will briefly go through VAE/GAN/Flow-based/Diffusion in this page.

## VAE
> Start from AE (AutoEncoder)

![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/452fe50c-ff58-4d62-aded-04eaefeb5aa8)

### Objective
- Minimize the input and output L2 loss (MSE)

### Discussion
- AutoEncoder can help us to find a discrete representation. But it's hard to include all possible data due to discrete representations.
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/854b6b39-a32f-4493-a474-ea84271bbd28)
  - adding variance so that we can include all possible data variance
  - Transfer data representation with continues distribution, such as Gaussian Distribution.
  - We can use multiple normal distribution to simulate the data, try to fix the distribution of training data. → GMM (Gaussian Mixture Model)
    ![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/72d62d66-38a2-4eee-804a-11f6a8eef088)
    - Pros
      - We can include more variance in hidden represenation
      - GMM is generative model, the improved AE could be used to generate images through pure noise → VAE
- We already know that we can use multiple normal distribution to simulate training data and generate data, but the GMM is not learnable
  - Use neural network to make it learnable → VAE
  ![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/1de991f6-ef7a-412d-b737-b9549492de03)
- How VAE generate image from noise ?
  - VAE will learn a normal distribution parameter (mean, std) for every image feature, and sample from each image feature to reconstruct the image
  ![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/71897ff2-29c4-46b1-a591-f77cb56e1ff5)
- VQVAE (Vector-Quantized VAE) (DALL-E is based on VQVAE)
  - Similar to VAE, but create a codebook to record all classes, make the generation process more controllable
  ![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/aa6e25d7-8d43-4b18-b091-45b24cc3d463)

## GAN
- TBC
## Diffusion Model
- TBC
## Flow-based model
- TBC

  

