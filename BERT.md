# BERT
*[Summary of the Google publications about BERT listed in the references below]*

[BERT (Bidirectional Encoder Representations from Transformers)](https://arxiv.org/abs/1810.04805) is a Natural Language Representation Model developed by Google in 2018, aimed at addressing the problem related to the shortage of specific training data for NLP tasks.

It is designed as a unified architecture to (i) pre-train [non-directional] representations from unlabeled text, and (ii) fine-tune the result - using a smaller labeled dataset - by incorporating one additional output layer. This allows to carry out a wide range of corpus-level and token-level downstream tasks, such as:

- Sentiment Analysis: ["Fine-grained Sentiment Classification using BERT"](https://arxiv.org/abs/1910.03474);
- Text Classification: ["How to Fine-Tune BERT for Text Classification?"](https://arxiv.org/abs/1905.05583) and ["DocBERT: BERT for Document Classification"](https://arxiv.org/abs/1904.08398);
- Question Answering: ["End-to-End Open-Domain Question Answering with BERTserini"](https://arxiv.org/abs/1902.01718);
- Named Entity Recognition (NER): ["Portuguese Named Entity Recognition using BERT-CRF"](https://arxiv.org/abs/1909.10649);
- Machine Translation: ["Incorporating BERT into Neural Machine Translation"](https://arxiv.org/abs/2002.06823); and
- Text Summarization: ["Text Summarization with Pretrained Encoders"](https://arxiv.org/abs/1908.08345).

> The original BERT implementation featured the BERT-BASE (L=12, H=768, A=12, **Total Parameters=110M**) and BERT-LARGE (L=24, H=1024, A=16, **Total Parameters=340M**) models, wherein L, H and A refer to the number of layers, hidden size and self-attention heads; respectively.

# Architecture and Pre-Training

## Transformer
At the core of the BERT model is a Transformer (["Attention Is All You Need"](https://arxiv.org/abs/1706.03762) and ["Transformer: A Novel Neural Network Architecture for Language Understanding"](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)), a neural network architecture based on a self-attention mechanism that weights the relationships between all words (or sub-words) in a sentence (regardless of their respective position). This allows to represent a word based on the entire context, and in particular to determine how much each of the other words should contribute to the intended word representation. 

A transformer includes an encoder that reads the text input, and a decoder that produces a prediction for the task.

![The Transformer applied to Machine Translation](https://3.bp.blogspot.com/-aZ3zvPiCoXM/WaiKQO7KRnI/AAAAAAAAB_8/7a1CYjp40nUg4lKpW7covGZJQAySxlg8QCLcBGAs/s1600/transform20fps.gif)

*The Transformer applied to Machine Translation* *(source: https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)*

This self-attention approach results in **higher accuracy, improved computational performance, and better understanding of the flow of information** when compared to Recurrent Neural Networks (RNNs) and Convolutional Neural Networks (CNNs):
- RNNs struggle to fully take advantage of modern fast computing devices such as TPUs and GPUs, due to their sequential nature. 
- CNNs are much less sequential than RNNs, but in most cases the number of steps required to combine information is correlated to the distance to the input. In contrast, the Transformer only performs a small, constant number of steps (chosen empirically).
- Transformers allow to visualize what word(s) of a sentence the encoder attends to when computing the final representation of a word. This allows to address the notoriously known phenomenon of **coreference resolution** in machine translation, wherein a word might refer to a different word depending on the meaning of the antecedent(s).

![Encoder self-attention distribution for the word “it”](https://1.bp.blogspot.com/-AVGK0ApREtk/WaiAuzddKVI/AAAAAAAAB_A/WPV5ropBU-cxrcMpqJBFHg73K9NX4vywwCLcBGAs/s1600/image2.png)


*Encoder self-attention distribution for the word “it”* *(source: https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)*



## Masked LM Training

BERT alleviates the unidirectionality constraint present in standard conditional language models (they can only be trained left-to-right or right-to-left, since bidirectional conditioning would allow each word to indirectly "see itself") by using a **masked language model (MLM)** (also referred in the literature as Cloze task) pre-training objective.

In particular, the Transformer encoder reads the entire sequence of words at once. In each sequence of the input, a percentage of words are randomly replaced by a mask token, and the objective is to predict the original vocabulary id of the masked words based on the context provided by the non-masked words in the sequence. 

> As described by the authors, 80% of the words are replaced with the [MASK] token, 10% with a random word, and 10% keep the word unchanged. The advantage of this procedure is that the Transformer encoder does not know which words it will be asked to predict or which have been replaced by random words, so it is forced to keep a distributional contextual representation of every input token.

## Next Sentence Prediction Training (NSP)

In order to understand the relationship between two sentences, the model further receives pairs of two spans of text from the corpus (referred as sentences A and B), and learns to predict if sentence B is connected to sentence A. 

In practice, both sentences are separated by a [CLS] token (inserted at the beginning of sentence A) and a [SEP] token (inserted at the end of sentence A), whereas every token is labeled as belonging to sentence A or sentence B.

> When choosing sentences A and B for each pretraining example, 50% of the time B is the actual next sentence that follows A (labeled as IsNext), and 50% of the time it is a random sentence from the corpus (labeled as NotNext). In the original implementation, a GELU activation - instead of a RELU function - was used.

# Fine-Tuning BERT

Fine-tuning is straightforward and relatively inexpensive since the self-attention mechanism in the Transformer allows BERT to model many downstream tasks by swapping out the appropriate inputs and outputs.

Task specific inputs and outputs are plugged into BERT, and the parameters are finetuned end-to-end.

> The Google Team found the following range of possible values to work well across all tasks:

> • Batch size: 16, 32

> • Learning rate (Adam): 5e-5, 3e-5, 2e-5

> • Number of epochs: 2, 3, 4


# References
- [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding
](https://arxiv.org/abs/1810.04805)
- [Transformer: A Novel Neural Network Architecture for Language Understanding](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html)
- [https://github.com/google-research/bert](https://github.com/google-research/bert)
- [The Annotated Transformer](http://nlp.seas.harvard.edu/annotated-transformer/)