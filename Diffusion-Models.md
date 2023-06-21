# Diffusion Models

[Diffusion models](), originally proposed in 2015, are becoming the leading deep generative models in image, audio and video synthesis due to their training stability and sample quality results. Generative models are a class of machine learning models that can generate new data based on training data. Other generative models include Generative adversarial networks (GANs), Variational Autoencoders (VAEs), and Flow-based models. Each can produce high-quality images, but they all have limitations that make them inferior to diffusion models.

In practice, diffusion models work by (i) gradually adding Gaussian noise levels to the training data, until said data transforms into pure noise; and (ii) learning to invert this process (i.e. to remove the added noise). The model can then apply this learnt denoising process to random seeds sampled from a normal distribution for synthesizing samples that exhibit realistic characteristics. 

This noising process is inspired by diffusion in physics.

The Neural Network

Training

Controlling

Speeding Up

Summary

## References

- [Dall-E 2](https://openai.com/dall-e-2): DALL·E 2 is an AI system that can create realistic images and art from a description in natural language. It uses a diffusion prior on CLIP latents, and cascaded diffusion models to generate high resolution 1024×1024 images. 
- [Imagen](https://imagen.research.google/):  Imagen consists of multiple diffusion models, which start by generating a small image and progressively increase its resolution. It leverages large transformer language models pretrained on text-only corpora, and does not require to learn from a latent prior. 
- [Stable Diffusion](https://stability.ai/)
- [Midjourney]()