

# Fine-Tuning

Fine-tuning is a supervised learning process designed to enhance the performance and adaptability of a pre-trained language model (LLM) for a downstream task. It involves updating the model's weights using a dataset that contains specific task-specific labeled examples, known as prompt-completion pairs.

In practice, it is feasible to fine-tune a LLM model for a single task, even with a relatively small number of examples (approximately 500-1000). However, this approach can lead to the model forgetting its previously learned tasks (catastrophic forgetting), which can be addressed with multitask fine-tuning, and parameter efficient fine-tuning (PEFT).

## FLAN, Multitask Intruction Fine-Tuning

FLAN fine-tunes the model on a large set of varied instructions that use a simple and intuitive description of the task, such as “Classify this movie review as positive or negative,” or “Translate this sentence to Danish”. As more types of tasks are added to the fine-tuning data model performance improves.

## Parameter Efficient Fine-Tuning (PEFT)

PEFT offers two main advantages over full fine-tuning. Firstly, by keeping most, if not all, of the LLM weights frozen, the number of trained parameters is much smaller than in the original model, making memory management more feasible. Secondly, PEFT is less prone to catastrophic forgetting. Instead of creating separate versions of the model for each task, PEFT combines the PEFT weights with the original LLM weights during inference, enabling efficient adaptation to multiple tasks. There are different approaches within PEFT, including selective methods, reparameterization methods, and additive methods, each with their own trade-offs in terms of parameter efficiency, memory efficiency, training speed, model quality, and inference costs.

### LoRA

### Soft-Prompts

## References

- [Finetuned Language Models are Zero-Shot-Learners](https://arxiv.org/pdf/2109.01652.pdf)
- [Introducing FLAN: More generalizable Language Models with Instruction Fine-Tuning](https://ai.googleblog.com/2021/10/introducing-flan-more-generalizable.html)
- [Scaling Instruction-Finetuned Language Models, Chung et al. 2022](https://arxiv.org/abs/2210.11416)
- [The FLAN Collection](https://github.com/google-research/FLAN/tree/main/flan/v2)
- [Templates/Prompts](https://github.com/google-research/FLAN/blob/main/flan/v2/templates.py)
