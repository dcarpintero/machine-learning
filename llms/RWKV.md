# RWKV: Reinventing RNNs for the Transformer Era

*[Summary of the RMKV Paper and References listed at the bottom]*

RWKV (Receptance Weighted Key Value) is a modified RNN with GPT-level LLM performance. It leverages a linear attention mechanism and enables the formulation of the model as either a Transformer or an RNN, thereby parallelizing computations during training and maintaining constant computational and memory complexity during inference.

## Motivation

**Transformer models** have emerged as a powerful alternative to RNNs and CNNs due to their ability to: **handle long-range dependencies** (in contrast to CNNs which are limited to a local context), **and parallelize training** (in contrast to RNNs which are hard to parallelize due to its sequential nature). 

**However, the self-attention mechanism inherent to Transformers (capable of processing and comparing all tokens in parallel) renders its architecture computationally expensive and memory-intensive for tasks involving long input sequences, or in resource-constrained situations**. In practice, the attention mechanism scales quadratically with the length of the sequence to be processed, as the attention scores are computed simultaneously for the entire sequence. This effectively limits the model’s input size (or "context length"). Additionally, because of the attention mechanism, when generating text, transformer models need to keep attention vectors for all previous tokens in memory (RNNs store only a single state).

The RMKV model aims to bridge the gap between computational efficiency and expressive capacity by combining the advantages of both RNNs and Transformers.

## RwKV Contributions

- During training, it uses the transformer type architecture (allowing parallelization) with a new attention mechanism (eschewing the traditional dot-product token interaction) that scales linearly with the number of tokens, and without approximation. In practice, it splits the RNN network into multiple smaller layers, where each layer's hidden state can be used independently to compute the next token hidden state for the same layer. This allows for the next token states to be computed partially in parallel, while awaiting the complete calculation of the first hidden state. In a cascading like pattern.

- At inference time, it works like an RNN with a state.

# References
- [RWKV: Reinventing RNNs for the Transformer Era](https://arxiv.org/abs/2305.13048)
- [RWKV Github Repo](https://github.com/BlinkDL/RWKV-LM)
- [RWKV Language Model - Wiki](https://wiki.rwkv.com/)
- [HuggingFace - RWKV](https://huggingface.co/blog/rwkv)
- [Apple’s Attention Free Transformer](https://machinelearning.apple.com/research/attention-free-transformer)