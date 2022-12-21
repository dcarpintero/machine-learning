# DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter

*[Summary of the DistilBERT paper listed in the references below]*

[DistilBERT](https://arxiv.org/abs/1910.01108) is a small, fast, cheap and light Transformer model trained by distilling BERT base. 

It has 40% less parameters than bert-base-uncased, runs 60% faster while preserving over 95% of BERT’s performances as measured on the GLUE language understanding benchmark.

To leverage the inductive biases learned by larger models during pre-training, it introduces a triple loss combining language modeling, distillation and cosine-distance losses.

As its larger counterparts it can be finetuned with good performances on a wide range of tasks.

# Knowledge Distillation

[Knowledge distillation](https://arxiv.org/abs/1503.02531) is a compression technique in which a compact model - the student - is trained to reproduce the behaviour of a larger model - the teacher - or an ensemble of models.


# References
- [DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter](https://arxiv.org/abs/1910.01108)