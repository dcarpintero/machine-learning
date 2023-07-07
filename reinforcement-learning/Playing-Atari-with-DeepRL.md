# Playing Atari with Deep Reinforcement Learning 

Published by Google's DeepMind team in 2013, it was the first study that successfully demonstrated how a convolutional neural network (CNN) could learn control policies directly from high-dimensional sensory inputs using reinforcement learning (RL).

## Network Architecture

The system utilized a variant of a Q-Learning algorithm integrated with a CNN. The architecture consisted of an input layer, followed by several convolutional layers, a fully connected layer, and an output layer. 

The input layer took raw pixel data from the game (specifically 84x84x4 image patches, with each image corresponding to a different frame). The convolutional layers automatically extracted relevant features from the input. The fully connected layer mapped these extracted features to the available game actions, and the output layer represented the predicted Q-values for each action.

## Training

The network was trained with a variant of the Q-learning algorithm, with stochastic gradient descent to update the weights. To alleviate the problems of correlated data and non-stationary distributions, it utilized a technique called **experience replay**, which randomly samples previous transitions, thereby reducing the correlation between consecutive training samples. In essence, the system would store its experiences at each time step in a replay memory, from which it would then draw random mini-batches to update the network weights.

## Challenges Overcome

Traditional RL algorithms struggle with high-dimensional raw data and usually require manual feature extraction to achieve acceptable performance. However, this DeepMind's approach enabled the model to learn directly from raw pixel data, thereby eliminating the need for manual feature extraction. This was a key development in the field of RL. Additionally, the use of **experience replay** improved the efficiency of learning by enabling the reuse of past experiences.

## References

- [Playing Atari with Deep Reinforcement Learning](https://arxiv.org/abs/1312.5602)