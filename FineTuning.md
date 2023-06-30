

# Fine-Tuning

Fine-tuning is a supervised learning process that updates the weights of a LLM using a dataset consisting of task-specific labeled examples, known as prompt-completion pairs.

In practice, it is possible to fine-tune a LLM model for a single task even with a limited number of  examples (around 500-1000). However, this approach can lead to the model forgetting its previously learned tasks (catastrophic forgetting). To mitigate this issue, the model can be simultaneously fine-tuned on multiple tasks. Another option is the use of parameter efficient fine-tuning (PEFT), a set of techniques that preserves the weights of the original LLM and trains only a small number of task-specific adapter layers and parameters.