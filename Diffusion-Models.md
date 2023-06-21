# Diffusion Models

Diffusion models, originally proposed in 2015, have emerged as the leading deep generative models for image, audio, and video synthesis due to their training stability and high-quality sample generation. While other generative models like *Generative Adversarial Networks (GANs)*, *Variational Autoencoders (VAEs)*, and *Flow-based* models can also produce high-quality images, diffusion models have demonstrated superior performance while overcoming certain limitations.

In practice, diffusion models operate by gradually adding Gaussian noise to the training data until the data transforms into pure noise. The model then learns to reverse this process, effectively removing the added noise. By applying this learned denoising process to random seeds sampled from a normal distribution, diffusion models generate samples with realistic characteristics.

This process is inspired by the concept of diffusion in physics, wherein particles spread and disperse from an area of high concentration to areas of lower concentration through random motion. Similarly, in diffusion models, the gradual introduction of noise can be regarded as a diffusion-like process, where the noise "spreads" and interacts with the data, gradually transforming it. The iterative steps in the diffusion model mimic the progression of time in a diffusion process, with each step representing a moment of diffusion and information exchange.

The Neural Network

Training

Controlling

Speeding Up

Summary

## References

- [Dall-E 2](https://openai.com/dall-e-2): DALL·E 2 is an AI system that can create realistic images and art from a description in natural language. It uses a diffusion prior on CLIP latents, and cascaded diffusion models to generate high resolution 1024×1024 images. 
- [Imagen](https://imagen.research.google/):  Imagen consists of multiple diffusion models, which start by generating a small image and progressively increase its resolution. It leverages large transformer language models pretrained on text-only corpora, and does not require to learn from a latent prior. 
- [Stable Diffusion](https://stability.ai/stablediffusion/).
- [Deep Unsupervised Learning using Nonequilibrium Thermodynamics](https://arxiv.org/abs/1503.03585)