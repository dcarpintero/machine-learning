# RoBERTa: An optimized method for pretraining self-supervised NLP systems
*[Summary of the RoBERTa paper listed in the references below]*

[RoBERTa](https://arxiv.org/abs/1907.11692) was developed by Facebook AI in 2019. It builds on [BERT](./BERT.md) with the following modifications:

1. dynamically generating the masking pattern applied to every training input;
2. removing the next sentence prediction objective;
3. training the model longer, with bigger batches, over more data; and
2. training on longer sequences.

# References
- [RoBERTa: An optimized method for pretraining self-supervised NLP systems](https://arxiv.org/abs/1907.11692)