# Q-Learning

Q-Learning (also Tabular Q-Learning) is a reinforcement learning algorithm that utilizes a Q-function and a Q-table to learn an optimal policy. The Q-function (Quality-function) is a mathematical function that estimates the expected cumulative reward for each state-action pair. The Q-table is a data structure that stores the Q-values for all possible state-action pairs in the environment.

During training, the agent iteratively updates the Q-values in the Q-table based on its experiences. It explores the environment by taking actions, observing rewards, and transitioning to new states. The Q-values in the Q-table are updated using the Bellman equation, which considers the immediate reward, the maximum expected future reward from the next state, and the learning rate (alpha) and discount factor (gamma) parameters. By iteratively updating the Q-values, the agent gradually learns which actions are more likely to yield higher rewards in each state.

As the training progresses, the Q-table is refined, and the Q-values converge towards the optimal values. Once the Q-values are learned, the agent can select actions in a given state by consulting the Q-table and choosing the action with the highest Q-value. This allows the agent to make decisions that maximize the expected cumulative rewards over time.

Using a Q-function and a Q-table in Q-Learning provides a practical way to represent and update the knowledge acquired by the agent. However, the use of a Q-table becomes infeasible for large state and action spaces due to the exponential growth of memory requirements. In such cases, alternative approaches like function approximation using deep neural networks (as in Deep Q-Networks) can be employed to approximate the Q-values for each possible action at a state.

# Deep Q-Learning

In Deep Q-Learning, during the training phase, the Q-value of a state-action pair is not updated directly. Instead, a loss function is created to compare the predicted Q-value with the Q-target, which is estimated using the Bellman equation. The weights of the Deep Q-Network are then updated using gradient descent to improve the approximation of the Q-values and infer the optimal policy, π(s).

## Deep Q-Learning Phases

- Sampling: actions are performed, and observed experience tuples are stored in a replay memory.
- Training: batches of tuples are selected randomly from the replay memory, and the neural network updates its weights using gradient descent.

## Solutions to stabilize Deep Q-Learning:

- Experience Replay: A replay memory is created to save experiences samples that are randomly sampled during training. By breaking the temporal correlation between consecutive experiences, the agent avoids forgetting previous experiences as it gets new ones, and getting stuck in suboptimal states.

- Fixed Q-Target: In order to calculate the Q-Target we need to estimate the discounted optimal Q-value of the next state by using Bellman equation. The problem is that the same network weights are used to calculate the Q-Target and the Q-value. This means that everytime we are modifying the Q-value, the Q-Target also moves with it. To avoid this issue, a separate network with fixed parameters is used for estimating the Temporal Difference Target. The target network is updated by copying parameters from our Deep Q-Network after certain C steps.

- Double Q-Learning: In traditional Q-Learning, the same Q-value estimation is used for both selecting and evaluating actions, which can lead to overoptimistic value estimates. Double Q-Learning addresses this issue by using two separate value functions. One value function is used to select the best action, while the other is used to evaluate the selected action. 

# References
- [Playing Atari with Deep Reinforcement Learning](https://arxiv.org/abs/1312.5602)
- [Human-level control through deep reinforcement learning](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf)