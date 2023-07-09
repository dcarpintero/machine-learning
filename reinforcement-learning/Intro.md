# Introduction

- Deep Reinforcement Learning (Deep RL) is a subfield of machine learning that combines deep neural networks with the principles of reinforcement learning for solving control tasks (also called decision problems). 

- It involves building agents that learn to interact with an environment by making sequential decisions that optimize the expected cumulative reward. By guiding these interactions with rewards (positive or negative), the agents learn to optimize their decision-making policies and maximize the cumulative reward (which is the goal of any RL agent). 

- The RL process is a loop that involves a sequence of **state**, **action** (discrete or continuous), **reward** and **next state**.

- The agents' decision-making process is called the policy π. To solve an RL problem, it is needed to find an Optimal Policy π, which determines the actions (given a state or observation of the environment) that maximize the expected return. There are two approaches to train an agent to find its optimal policy π:
    - **Policy-Based Methods**: Train the policy (π) directly to learn which action to take given a state.
    - **Value-Based Methods**: Train a value function (Q) to learn which state is more valuable and use this value function to take the action that leads to it. In other words, finding an optimal value function (denoted Q* or V*) leads to having an optimal policy.
    
    Types of value-based functions:

        - State-Value: outputs the expected return if the agent starts at a given state and acts according to the policy forever after.
        - Action-Value: outputs the expected return if the agent starts in a given state, takes a given action at that state and then acts accordingly to the policy forever after.

    Types of methods to learn a policy:

        - Monte Carlo: learning at the end of the episode. 
        - TD Learning: learning at each step.
