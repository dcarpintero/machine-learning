# Diffusion Models

[Diffusion models](), originally proposed in 2015, are becoming the leading deep generative models in image, audio and video synthesis due to their training stability and sample quality results. Generative models are a class of machine learning models that can generate new data based on training data. Other generative models include Generative adversarial networks (GANs), Variational Autoencoders (VAEs), and Flow-based models. Each can produce high-quality images, but they all have limitations that make them inferior to diffusion models.

In practice, diffusion models work by (i) gradually introducing Gaussian (distribution) noise to the training data, until said data transforms into pure noise; and (ii) learning to invert this process (i.e. to remove the added noise). The model can then apply this denoising process to random seeds sampled from a normal distribution to synthesize samples that exhibit realistic characteristics. 

The Neural Network

Training

Controlling

Speeding Up

Summary