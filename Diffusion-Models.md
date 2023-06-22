# Diffusion Models

[Diffusion models](https://arxiv.org/abs/1503.03585), introduced in 2015, have emerged as the leading deep generative models for image, audio, and video synthesis due to their training stability and high-quality sample generation. While other generative models like *Generative Adversarial Networks (GANs)*, *Variational Autoencoders (VAEs)*, and *Flow-based* models can also produce high-quality images, diffusion models have demonstrated superior performance in their abilities towards training convergence (stability), fine control over noise levels, invertible process and flexibility across domains. 

In practice, diffusion models operate by gradually adding Gaussian noise to the training data until the data transforms into pure noise. The model then learns to reverse this process by computing the loss between the predicted and effective noise. By applying this learned denoising process to random seeds sampled from a normal distribution, diffusion models can generate data with realistic characteristics.

This process is inspired by the concept of diffusion in physics, wherein particles spread and disperse from an area of high concentration to areas of lower concentration through random motion. Similarly, in diffusion models, the gradual introduction of noise can be regarded as a diffusion-like process, where the noise "spreads" and interacts with the data, gradually transforming it. The iterative steps in the diffusion model mimic the progression of time in a diffusion process, with each step representing a moment of diffusion and information exchange.

## Network Architecture

[U-Net](https://arxiv.org/pdf/1505.04597v1.pdf) network architectures, which allow the preservation of dimensions, are commonly used in diffusion models as a part of the encoder and decoder components:

- The encoder takes the input data and progressively downsamples it into an embedding by applying convolutional layers. 
- After encoding the input data, the diffusion steps are applied to gradually introduce noise. 
- The decoder takes this diffused representation and aims at predicting (and removing) the noise. The decoder consists of upsampling layers that progressively increase the spatial dimensions while also taking further information in form of time embeddings (related to the timestep and noise level) and context embeddings.

## Controlling

Controlling in diffusion models refers to the ability to manipulate the generation process and produce samples with desired characteristics:

- Noise Scheduler: allows to influence the level of randomness introduced at each training step. In this regard, Denoising Diffusion Probabilistic Models (DDPM) follow a fixed noise schedule wherein the noise is uniformly dependent on the previous step; whereas Denoising Diffusion Implicit Models (DDIM) dynamically adapt the noise schedule based on the data, allowing more flexibility and a faster process.

- Temperature Parameter: controls the level of randomness in the generation process. Higher temperatures lead to more random and diverse samples, while lower temperatures produce more deterministic and focused samples. 

- Conditional Information: text prompts and class labels to exhibit desired attributes or follow certain constraints.

## References

- [High-Resolution Image Synthesis with Latent Diffusion Models](https://arxiv.org/abs/2112.10752)
- [Deep Unsupervised Learning using Nonequilibrium Thermodynamics](https://arxiv.org/abs/1503.03585)