

# Fine-Tuning

Fine-tuning is a supervised learning process designed to enhance the performance and adaptability of a pre-trained language model (LLM) for a downstream task. It involves updating the model's weights using a dataset that contains specific task-specific labeled examples, known as prompt-completion pairs.

In practice, it is feasible to fine-tune a LLM model for a single task, even with a relatively small number of examples (approximately 500-1000). However, this approach can lead to the model forgetting its previously learned tasks (catastrophic forgetting), which can be addressed with multitask fine-tuning, and parameter efficient fine-tuning (PEFT).

## Instruction Fine-Tuning (FLAN Models)

FLAN fine-tunes the model on a large set of varied instructions that use a simple and intuitive description of the task, such as “classify this movie review as positive or negative,” or “translate this sentence to Danish”. As more types of tasks are added to the fine-tuning data model performance improves.

## Parameter-Efficient Fine-Tuning (PEFT)

PEFT offers two main advantages over full fine-tuning. Firstly, by keeping most of the LLM weights frozen, the number of trained parameters is much smaller than in the original model, making memory management more feasible. Secondly, PEFT is less prone to catastrophic forgetting. Instead of creating separate versions of the model for each task, **PEFT combines the PEFT weights with the original LLM weights during inference**, enabling efficient adaptation to multiple tasks. There are different approaches within PEFT, including selective methods, reparameterization methods, and additive methods, each with their own trade-offs in terms of parameter efficiency, memory efficiency, training speed, model quality, and inference costs.

### LoRA: Low Rank Adaptation of LLMs

LoRA is a parameter-efficient fine-tuning technique (PEFT) falling under the reparameterization category. It reduces the number of parameters to be trained during fine-tuning by freezing the original model parameters and introducing a pair of rank decomposition matrices. These smaller matrices, when multiplied together, create a matrix with the same dimensions as the frozen weights. By updating and replacing only these low-rank matrices instead of the original weights, LoRA achieves significant parameter reduction and computational efficiency. It allows for fine-tuning on different tasks by swapping out the appropriate set of LoRA matrices at inference time.

By updating and replacing only these low-rank matrices instead of the original weights, LoRA achieves significant parameter reduction, making it computationally efficient. The reduced number of trainable parameters allows for fine-tuning on multiple tasks without the need for extensive computational resources. Additionally, the memory requirements for storing the LoRA matrices are minimal.

LoRA can be applied to specific components of the language model, such as the self-attention layers, where the majority of the model's parameters reside. By fine-tuning with LoRA, performance gains can be achieved for various tasks, such as dialogue summarization. While the performance improvement may be slightly lower compared to full fine-tuning, the reduced computational cost and parameter efficiency make LoRA an attractive choice.

The choice of rank for the LoRA matrices is crucial and remains an active area of research, with ranks ranging from 4 to 32 striking a good balance between parameter reduction and model performance.

### Soft-Prompts

Soft prompt is an additive parameter-efficient fine-tuning technique (PEFT) used to improve the performance of language models for specific tasks without modifying the original model architecture.

It focus on manipulating the input text to enhance model performance. This can be achieved by adding trainable parameters to the prompt embeddings or by keeping the input fixed and retraining the embedding weights. By adjusting the prompt, the model's behavior can be guided and tailored to the desired task.

Unlike other fine-tuning methods that update a large number of model parameters, soft prompt methods only introduce a small number of new trainable components, resulting in a smaller footprint and reduced memory requirements during training and inference.

Soft prompt techniques offer flexibility in adapting language models to multiple tasks. Different prompts can be used for different tasks, allowing the same model to be fine-tuned and utilized for various applications. This approach avoids the need to store multiple full-size versions of the language model for each specific task.

## Reinforcement Learning from Human Feedback (RLHF)

RLHF (Reward Learning from Human Feedback) is a fine-tuning process used to align Language Models (LLMs) with human preferences. It involves assessing LLM completions using a reward model based on human preference metrics like helpfulness. Through a reinforcement learning algorithm, e.g. the Proximal Policy Optimization (PPO) algorithm, the weights of the LLM are updated according to the assigned rewards. This iterative process is repeated with different prompts and weight updates until the desired alignment is achieved, resulting in a human-aligned LLM.

A challenge in reinforcement learning is reward hacking, where the agent learns to maximize rewards without truly aligning with the intended objective. In the context of LLMs, reward hacking can result in the addition of words or phrases that boost scores for the aligned metric but may compromise the overall quality of the generated language.

To address reward hacking, KL divergence (Kullback-Leibler divergence) is used. KL divergence is a statistical measure of how different two probability distributions are. During training, each prompt is passed to both the reference LLM (with frozen weights) and the updated LLM. The completions generated by both models are compared using KL divergence, providing insight into how much the updated LLM has diverged from the reference LLM. In practice, the KL divergence shift penalty is added to the reward, encouraging the updated model to stay closer to its intended language model's behavior.

## References

### Multitask Instruction Fine-Tuning
- [Finetuned Language Models are Zero-Shot-Learners](https://arxiv.org/pdf/2109.01652.pdf)
- [Introducing FLAN: More generalizable Language Models with Instruction Fine-Tuning](https://ai.googleblog.com/2021/10/introducing-flan-more-generalizable.html)
- [The FLAN Collection](https://github.com/google-research/FLAN/tree/main/flan/v2)
- [Scaling Instruction-Finetuned Language Models, Chung et al. 2022](https://arxiv.org/abs/2210.11416)

### Parameter-Efficient-Fine-Tuning (PEFT)
- [Scaling Down to Scale Up: A Guide to Parameter-Efficient Fine-Tuning](https://arxiv.org/pdf/2303.15647.pdf)

### LoRA
- [LoRA Low-Rank Adaptation of Large Language Models](https://arxiv.org/pdf/2106.09685.pdf)

### Prompt Tuning with Soft Prompts
- [The power of Scale for Parameter-Efficient Prompt Tuning, Lester et. al 2021]()
- [Templates/Prompts](https://github.com/google-research/FLAN/blob/main/flan/v2/templates.py)
