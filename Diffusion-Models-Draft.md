ElvGames

you want a NN to learn what a sprite is:
- fine details (characteristics)
- general outlines (head, body)
- everything in between


Sampling
--------
NN tries to fully predict the noise at each step, and then substracts it from the sample. In practice several steps are needed to get high quality examples. 
ddpm algorithm

The NN expects noisy example as input => add in additional noise before it gets passed to the next step.

Empirically, this stabilizes the NN so it doesn't collapse to sth closer to the average of the dataset.

The Neural Network
------------------
Takes an image as input, and produces as output an image of the same size, which in this case is the predicted noise. UNets have been around since 2015, and they were first used for image segmentation.

It first downsamples the image with CNN into an embedding that compresses the information, and then upsamples with the same number of up-sampling blocks to predict the noise that was applied to the image.
The UNet can take in more information in form of embeddings such as time embedding (related to the timestep and noise level) and context embedding which helps to control what the model generates, for example a text description.

Training
--------
The goal of the NN is to predict noise, and it learns what is and what is not noise. In practice it uses a sample random timestep (noise level) per image to train more stably.

- Sample a training image
- Sample timestep t. This determines the level of noise.
- Sample the noise.
- Add noise to image.
- Input this into the NN. NN predicts the noise.
- Compute loss between predicted and true noise.
- Backprop & learn.

Controlling
-----------
Embeddings (vectors of numbers) capturing a meaning.
Text with similar content will have similar vectors.

Context is a vector for controlling generation.

Speeding Up
-----------
New sampling method that is 10 times more efficient than DDPM => DDIM

Sampling is slow because there are many timesteps, and each timestep is dependent on the previous one (markovian). 

Many samplers address this problem of speed:

DDIM: denoising diffusion implicit models (faster because it is able to skip time steps, removing the randomness from the sampling process) It predicts a rough sketch of the final output and then it refines with the denoising process

Summary
-------
Diffusion models aren't bound to images either, that's just where they've been the most popular. There are diffusion models for music, where you can give it any prompt and get music out, for proposing new molecules to accelerate drug discovery, in-painting, textual inversion. 
 
latent diffusion which operates on image embeddings instead of images
cross-attention, text conditioning, classifier-free guidance



To understand how diffusion generative models work, it is helpful to explain them based on image-generating diffusion models. Here, diffusion models gradually add random noise to a 2D image through a series of steps, destroying the data in the image until it becomes nothing but grainy static. A neural network is then trained to recover the original image by reversing this noising process. The model can then generate new data by starting from a random configuration and iteratively removing the noise.

https://arxiv.org/abs/2209.00796 

Team
####
Do you have subject-matter expertise? Do you know which tools users are using?
Do you have relationships in the industry who can help make introductions?
Can you secure pilots, poc or even just get meetings?
Are you part of the customer base?
Can you execute or have you done it before? 


Market
######
Who is your customer and how many of them are there?
What is the problem? How much time or money does it waste? How much risk or fustration does it create? What is their current experience or process? Tell a story of a potential customer.


Product
######
Does your product address the customer problem?
Have you built it? Is someone using it?
How much or how often are they using it?


Revenue & Go-To-Market
######
Is someone paying for your product?
What is your revenue model?
How much revenue can you generate per customer?
What is the margin?
What is the cost for a customer to star using your product?
How do you ensure your customers renew?
How many ways can you monetize products/services to that customer?
