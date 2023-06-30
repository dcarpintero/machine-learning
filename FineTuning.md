

# Fine-Tuning

Fine-tuning is a supervised learning process designed to enhance the performance and adaptability of a pre-trained language model (LLM) for a specific task. It involves updating the model's weights using a dataset that contains task-specific labeled examples, known as prompt-completion pairs.

In practice, it is feasible to fine-tune a LLM model for a single task, even with a relatively small number of examples (approximately 500-1000). However, this approach can lead to the model forgetting its previously learned tasks (catastrophic forgetting).

## FLAN-Models

The model can be simultaneously fine-tuned on multiple tasks (this might require around 50.000 examples).

- FLAN-T5: general purpose instruct model, fine-tuned on 473 datasets across 146 task categories.

## Parameter Efficient Fine-Tuning (PEFT)

Another option is the use of parameter efficient fine-tuning (PEFT), a set of techniques that preserves the weights of the original LLM and trains only a small number of task-specific adapter layers and parameters.

## References

- Chung et al. 2022 "Scaling Instruction-Finetuned Language Models"