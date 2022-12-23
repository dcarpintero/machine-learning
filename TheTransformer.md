# The Transformer: Attention is All You Need
*[Summary of the Transformer publications listed in the references below]*

The Transformer is an encoder-decoder architecture aimed at reducing sequential computation. It was introduced by Google in 2017, and has been widely used in natural language processing tasks such as machine translation, reading comprehension, abstractive summarization, and text classification.

The core contribution of the Transformer is the use a **self-attention mechanism**, which allows the model to directly consider the relationships between input words (or tokens) at different positions in the input sequence.

This approach results in **higher accuracy, improved computational performance, and better understanding of the flow of information** when compared to Recurrent Neural Networks (RNNs) and Convolutional Neural Networks (CNNs):
- RNNs struggle to fully take advantage of modern fast computing devices such as TPUs and GPUs, due to their sequential nature. 
- CNNs are much less sequential than RNNs, but in most cases the number of steps required to combine information is correlated to the distance to the input (linearly for ConvS2S and logarithmically for ByteNet), which makes it more difficult to learn dependencies between distant positions.  

    In contrast, the Transformer only performs a small, constant number of steps (chosen empirically), albeit at the cost of reduced effective resolution due to averaging attention-weighted positions. An effect that is addressed with Multi-Head Attention.
- Transformers allow to visualize what word(s) of a sentence the encoder attends to, when computing the final representation of a word. This allows to address the notoriously known phenomenon of **coreference resolution** in machine translation, wherein a word might refer to a different word depending on the meaning of the antecedent(s).

# Model Architecture

The Transformer follows an encoder-decoder architecture using stacked self-attention, and feedforward neural network layers.

<p align="center">
  <img src="/img/the-encoder-architecture" width="200">
</p>

*[The Transformer Architecture - source: https://arxiv.org/pdf/1706.03762.pdf]*

## Encoder

The encoder processes the input sequence and produces a sequence of hidden states. It is composed of a stack of N = 6 identical layers (each comprising two sub-layers). 

The first sublayer is a **multi-head self-attention** mechanism that allowss the encoder to attend to different positions in the input sequence and compute a weighted sum of the hidden states at those positions. 

The second sublayer, a **feedforward neural network**, is a standard fully-connected neural network that processes the output of the self-attention sublayer. In practice it consists of multiple hidden units and applies a non-linear activation function to the inputs.

## Decoder

The decoder is also composed of a stack of N = 6 identical layers. 

In addition to the two sub-layers in each encoder layer, it inserts a third sub-layer, which performs **multi-head attention over the output of the encoder stack** (allowing the decoder to attend to the hidden states produced by the encoder). Similar to the encoder, the decoder employs residual connections around each of the sub-layers, followed by layer normalization.

The self-attention sub-layer in the decoder stack prevents positions from attending to subsequent positions. This masking, combined with the offset by one position of the output embeddings, ensures that the predictions for position ii can depend only on the known outputs at positions less than ii.

## Self-Attention Mechanism

An attention function can be described as mapping a query and a set of key-value pairs to an output, where the query, keys, values, and output are all vectors. The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key.

The self-attention mechanism allows the model to directly consider the relationships between input words (or tokens) at different positions in the input sequence, rather than relying on a fixed-length context window or recurrence. This enables the Transformer to process input sequences of arbitrary length and results in a more effective handling of long-range dependencies.

# References
- [Attention Is All You Need](https://arxiv.org/pdf/1706.03762.pdf)
- [Transformer: A Novel Neural Network Architecture for Language Understanding](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)
- [The Annotated Transformer](http://nlp.seas.harvard.edu/annotated-transformer/)