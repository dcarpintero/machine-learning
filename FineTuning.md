

# Fine-Tuning

Fine-tuning is a supervised learning process designed to enhance the performance and adaptability of a pre-trained language model (LLM) for a downstream task. It involves updating the model's weights using a dataset that contains specific task-specific labeled examples, known as prompt-completion pairs.

In practice, it is feasible to fine-tune a LLM model for a single task, even with a relatively small number of examples (approximately 500-1000). However, this approach can lead to the model forgetting its previously learned tasks (catastrophic forgetting), which can be addressed with multitask fine-tuning, and parameter efficient fine-tuning (PEFT).

## FLAN, Multitask Intruction Fine-Tuning

FLAN fine-tunes the model on a large set of varied instructions that use a simple and intuitive description of the task, such as “Classify this movie review as positive or negative,” or “Translate this sentence to Danish”. As more types of tasks are added to the fine-tuning data model performance improves.

## Parameter Efficient Fine-Tuning (PEFT)

Another option is the use of parameter efficient fine-tuning (PEFT), a set of techniques that preserves the weights of the original LLM and trains only a small number of task-specific adapter layers and parameters.

## References

- [Finetuned Language Models are Zero-Shot-Learners](https://arxiv.org/pdf/2109.01652.pdf)
- [Introducing FLAN: More generalizable Language Models with Instruction Fine-Tuning](https://ai.googleblog.com/2021/10/introducing-flan-more-generalizable.html)
- [Scaling Instruction-Finetuned Language Models, Chung et al. 2022](https://arxiv.org/abs/2210.11416)
