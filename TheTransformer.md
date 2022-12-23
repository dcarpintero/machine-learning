# The Transformer: Attention is All You Need
*[Summary of the Transformer publications listed in the references below]*

The Transformer is an encoder-decoder architecture aimed at reducing sequential computation (to speed-up the training time). It was proposed by Google in 2017, and has been widely used in Natural Language Processing tasks such as machine translation, reading comprehension, abstractive summarization, and text classification.

The core contribution of the Transformer is the use a **self-attention mechanism**, which allows the model to directly consider the relationships between input words (or tokens) at different positions in the input sequence.

This approach results in **higher accuracy, improved computational performance, and better understanding of the flow of information** when compared to Recurrent Neural Networks (RNNs) and Convolutional Neural Networks (CNNs):
- RNNs struggle to fully take advantage of modern fast computing devices such as TPUs and GPUs, due to their sequential nature. 
- CNNs are much less sequential than RNNs, but in most cases the number of steps required to combine information is correlated to the distance to the input (linearly for ConvS2S and logarithmically for ByteNet), which makes it more difficult to learn dependencies between distant positions.  

    In contrast, the Transformer only performs a small, constant number of steps (chosen empirically), albeit at the cost of reduced effective resolution due to averaging attention-weighted positions. An effect that is addressed with Multi-Head Attention.
- Transformers allow to visualize what word(s) of a sentence the encoder attends to, when computing the final representation of a word. This allows to address the notoriously known phenomenon of **coreference resolution** in machine translation, wherein a word might refer to a different word depending on the meaning of the antecedent(s).

# Model Architecture

The Transformer follows a stacked encoder-decoder architecture using Multi-Head Self-Attention Mechanism, and Position-Encoding and Position-Wise Feed Forward Neural Networks.

<p align="center">
  <img src="img/the-encoder-architecture.png" width="400">
</p>

<p align="center">The Transformer Architecture - source: https://arxiv.org/pdf/1706.03762.pdf</p>

## Encoder

The encoder processes the input sequence and produces a sequence of hidden states. It is composed of a stack of N = 6 identical layers (each comprising two sub-layers). 

The first sublayer is a **multi-head self-attention** mechanism that enables the encoder to attend to different positions in the input sequence and compute a weighted sum of the hidden states at those positions. 

The second sublayer, a **feedforward neural network**, is a standard fully-connected NN that processes the output of the self-attention sublayer. In practice it consists of multiple hidden units and applies a non-linear activation function to the inputs.

## Decoder

The decoder is also composed of a stack of N = 6 identical layers. 

In addition to the two sub-layers in each encoder layer, it inserts a third sub-layer, which performs **multi-head attention over the output of the encoder stack**. Similar to the encoder, the decoder employs residual connections around each of the sub-layers, followed by layer normalization.

The self-attention sub-layer in the decoder stack prevents positions from attending to subsequent positions. This masking, combined with the offset by one position of the output embeddings, ensures that the predictions for position ii can depend only on the known outputs at positions less than ii.

## Self-Attention Mechanism

An attention function can be described as mapping a query and a set of key-value pairs to an output, wherein the query, keys, values, and output are all vectors. The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key.

There are two types of attention mechanisms used in the Transformer architecture: **self-attention** and **encoder-decoder attention**.

The **self-attention** mechanism allows the model to directly consider the relationships between input words (or tokens) at different positions in the input sequence, rather than relying on a fixed-length context window or recurrence. This enables the Transformer to **process input sequences of arbitrary length** and **results in a more effective handling of long-range dependencies**.

The self-attention process can be described as follows:

1. The input sequence is passed through an embedding layer, which maps the input tokens to a high-dimensional space. In practice it is implemented as a lookup table that maps each input token to a 512 size embedding vector.

    This allows the model to (i) handle words that are not present in the training data (out-of-vocabulary words) by mapping them to a special "unknown" embedding vector, and (ii) incorporate additional information about the input tokens, such as their part-of-speech or syntactic role.

2. Positional encoding is used instead of convolutional layers or recurrent mechanism (which process the input word by word in a sequencial manner) to record the relative or absolute position information of the tokens in the sequence.

3. The query, key, and value representations are used to compute the attention weights using a dot-product (of the query vector with the key vector of the respective word) followed by a normalization step.

4. The attention weights are used to compute a weighted sum of the value representations, which is input to the feedforward neural network.

The **encoder-decoder attention** is used in the decoder layer to attend to the hidden states produced by the encoder (from where the keys and values are coming).



# References
- [Attention Is All You Need](https://arxiv.org/pdf/1706.03762.pdf)
- [Transformer: A Novel Neural Network Architecture for Language Understanding](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)
- [The Annotated Transformer](http://nlp.seas.harvard.edu/annotated-transformer/)
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)