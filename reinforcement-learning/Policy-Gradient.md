# Policy-Methods

Policy-based methods in reinforcement learning aim to directly optimize the policy without relying on a value function. Policy-based methods use a parameterized policy, such as a neural network, to output a probability distribution over actions. 

## Policy-Gradient

Policy gradient is a subset of policy-based methods that directly performs gradient ascent on the performance of the objective function to find the optimal policy. Policy-gradient methods offer advantages such as the ability to learn stochastic policies, effectiveness in high-dimensional and continuous action spaces, and smoother convergence properties. However, they can suffer from slower training, potential local optima, and high variance.


