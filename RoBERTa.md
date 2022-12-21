# RoBERTa: An optimized method for pretraining self-supervised NLP systems
*[Summary of the RoBERTa paper listed in the references below]*

[RoBERTa](https://arxiv.org/abs/1907.11692) was developed by Facebook AI in 2019. It builds on [BERT](./BERT.md) with the following modifications:

1. training the model longer, with bigger batches, over more data; 
2. removing the next sentence prediction objective;
3. training on longer sequences; and
4. dynamically changing the masking pattern applied to the training data.


RoBERTa modifies key hyperparameters in BERT, including removing BERT’s next-sentence pretraining objective, and training with much larger mini-batches and learning rates. This allows RoBERTa to improve on the masked language modeling objective compared with BERT and leads to better downstream task performance.

