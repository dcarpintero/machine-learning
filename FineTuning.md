

# Fine-Tuning

Fine-tuning is a supervised learning process designed to enhance the performance and adaptability of a pre-trained language model (LLM) for a downstream task. It involves updating the model's weights using a dataset that contains specific task-specific labeled examples, known as prompt-completion pairs.

In practice, it is feasible to fine-tune a LLM model for a single task, even with a relatively small number of examples (approximately 500-1000). However, this approach can lead to the model forgetting its previously learned tasks (catastrophic forgetting), which can be addressed with multitask fine-tuning, and parameter efficient fine-tuning (PEFT).

## Instruction Fine-Tuning (FLAN Models)

FLAN fine-tunes the model on a large set of varied instructions that use a simple and intuitive description of the task, such as “classify this movie review as positive or negative,” or “translate this sentence to Danish”. As more types of tasks are added to the fine-tuning data model performance improves.

## Parameter-Efficient Fine-Tuning (PEFT)

PEFT offers two main advantages over full fine-tuning. Firstly, by keeping most of the LLM weights frozen, the number of trained parameters is much smaller than in the original model, making memory management more feasible. Secondly, PEFT is less prone to catastrophic forgetting. Instead of creating separate versions of the model for each task, **PEFT combines the PEFT weights with the original LLM weights during inference**, enabling efficient adaptation to multiple tasks. There are different approaches within PEFT, including selective methods, reparameterization methods, and additive methods, each with their own trade-offs in terms of parameter efficiency, memory efficiency, training speed, model quality, and inference costs.

### LoRA: Low Rank Adaptation of LLMs

LoRA is a parameter-efficient fine-tuning (PEFT) technique falling under the reparameterization category. It reduces the number of parameters to be trained during fine-tuning by freezing the original model parameters and introducing a pair of rank decomposition matrices. These smaller matrices, when multiplied together, create a matrix with the same dimensions as the frozen weights. By updating and replacing only these low-rank matrices instead of the original weights, LoRA achieves significant parameter reduction and computational efficiency. It allows for fine-tuning on different tasks by swapping out the appropriate set of LoRA matrices at inference time.

By updating and replacing only these low-rank matrices instead of the original weights, LoRA achieves significant parameter reduction, making it computationally efficient. The reduced number of trainable parameters allows for fine-tuning on multiple tasks without the need for extensive computational resources. Additionally, the memory requirements for storing the LoRA matrices are minimal.

LoRA can be applied to specific components of the language model, such as the self-attention layers, where the majority of the model's parameters reside. By fine-tuning with LoRA, performance gains can be achieved for various tasks, such as dialogue summarization. While the performance improvement may be slightly lower compared to full fine-tuning, the reduced computational cost and parameter efficiency make LoRA an attractive choice.

The choice of rank for the LoRA matrices is crucial and remains an active area of research, with ranks ranging from 4 to 32 striking a good balance between parameter reduction and model performance.

### Soft-Prompts

## References

- [Finetuned Language Models are Zero-Shot-Learners](https://arxiv.org/pdf/2109.01652.pdf)
- [Introducing FLAN: More generalizable Language Models with Instruction Fine-Tuning](https://ai.googleblog.com/2021/10/introducing-flan-more-generalizable.html)
- [Scaling Instruction-Finetuned Language Models, Chung et al. 2022](https://arxiv.org/abs/2210.11416)
- LORA paper
- [The power of Scale for Parameter-Efficient Prompt Tuning, Lester et. al 2021]()
- [The FLAN Collection](https://github.com/google-research/FLAN/tree/main/flan/v2)
- [Templates/Prompts](https://github.com/google-research/FLAN/blob/main/flan/v2/templates.py)
