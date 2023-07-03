# Introduction

- Deep Reinforcement Learning (Deep RL) is a subfield of machine learning that combines deep neural networks with the principles of reinforcement learning for solving control tasks (also called decision problems). 

- It involves building agents that learn to interact with an environment by making sequential decisions that optimize the expected cumulative reward. By guiding these interactions with rewards (positive or negative), the agents learn to optimize their decision-making policies and maximize the cumulative reward (which is the goal of any RL agent). 

- The RL process is a loop that outputs a sequence of **state**, **action** (discrete or continuous), **reward** and **next state**.

- The agents decision-making process is called the policy π, and to solve an RL problem, it is needed to find an Optimal Policy π, which determines the actions (given a state) that maximize the expected return. There are two approaches to train an agent to find its optimal policy π:
    - Directly, map from each state to the best corresponding action at that state: **Policy-Based Methods**.
    - Indirectly, train a value function that maps a state to the expected value of being at that state.: **Value-Based Methods**.