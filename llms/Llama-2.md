# LLaMA 2: Open Foundation and Fine-Tuned Chat Models

 Llama 2 is a collection of pretrained and fine-tuned large language models (LLMs) ranging in scale from 7 billion to 70 billion parameters. 
 
 At its core, LLaMA is an auto-regressive language model, built on the transformer architecture. In practice, it takes a sequence of words as input and predicts the next word, recursively generating text.

Llama 2 features various improvements:

 - RMSNorm normalizing function is used to improve the training stability, by normalizing the input of each transformer sub-layer, instead of normalizing the output.

 - The ReLU non-linearity is replaced by the SwiGLU activation function to improve performance.

 - Absolute positional embeddings are removed and instead rotary positional embeddings (RoPE) are added at each layer of the network.





![Llama2](../img/llama.jpg)
*(source: https://ai.meta.com/llama/#inside-the-model)*

# Training

![Llama2 Training](../img/llama-training.jpg) *(source: https://ai.meta.com/resources/models-and-libraries/llama/)*

Llama 2 was pretrained using publicly available online data. An initial version of Llama-2-chat was supervised fine-tuning. Next, Llama-2-chat was iteratively refined using RLHF, which included rejection sampling and proximal policy optimization (PPO). 

# References

- [Llama by Meta](https://ai.meta.com/llama/)
- [Llama Recipes](https://github.com/facebookresearch/llama-recipes/)
- [Github Code](https://github.com/facebookresearch/llama)
- [Llama 2: an incredible open LLM](https://www.interconnects.ai/p/llama-2-from-meta)