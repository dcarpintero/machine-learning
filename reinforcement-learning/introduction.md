# Introduction

- Deep Reinforcement Learning (Deep RL) is a machine learning framework that combines deep neural networks with the principles of reinforcement learning for solving control tasks (also called decision problems). It involves building agents that learn to make sequential decisions in an environment. Through interactions with the environment, guided by positive (or negative) rewards, these agents learn to optimize their decision-making policies and maximize the expected cumulative reward (which is the goal of any RL agent). 

- The RL process is a loop that outputs a sequence of **state**, **action** (discrete or continuous), **reward** and **next state**.

- To solve an RL problem, it is needed to find optimal policy, which determines the actions (given a state) that maximize the expected return. The Policy π is the function that defines the agent's behavior by determining what action to take given a state.

There are two approaches to train an agent to find its optimal policy π:
- Directly, map from each state to the best corresponding action at that state: **Policy-Based Methods**.
- Indirectly, train a value function that maps a state to the expected value of being at that state.: **Value-Based Methods**.