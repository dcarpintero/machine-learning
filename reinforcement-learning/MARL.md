# Multi-Agents Reinforcement Learning (MARL)

Multi-Agent Reinforcement Learning (MARL) is a subfield of reinforcement learning that focuses on scenarios where multiple agents interact with each other and the environment. In MARL, the goal is to learn effective policies for each agent, considering the dynamic interactions and interdependencies among them. The agents can be cooperative (work together to maximize a common goal), competitive (compete against each other to maximize individual rewards) or mixed (where some agents need to cooperate to beat an opponent).  

## Decentralized Learning

Each agent is trained independently without considering the actions or policies of other agents. The primary idea behind this approach is to treat other agents as part of the environment dynamics rather than as individual agents. However, a significant challenge arises from the **non-stationarity8** introduced to the environment. As other agents interact and make decisions, the underlying Markov decision process undergoes changes over time, creating a dynamic environment. This poses a difficulty for many Reinforcement Learning algorithms that **struggle to converge to a global optimum** in such non-stationary settings.

## Centralized Learning

In a centralized learning architecture, a high-level process known as the **experience buffer** collects experiences from multiple agents to learn a shared common policy and achieve a global reward.

## Self-Play

In self-play, an agent uses previous versions of its own policy as opponents during training, creating a challenging but not overly difficult environment. Self-play serves as a mechanism to bootstrap an opponent and progressively increase its complexity.

The primary objective of self-play is to strike a **balance between the skill level and generality of the final policy while ensuring stable learning**. 

## ELO Score

In adversarial games, tracking the cumulative reward might not provide a meaningful learning metric, as it is heavily influenced by the skill of the opponent. To address this, an ELO rating system, named after Arpad Elo, is commonly used. The ELO system calculates the relative skill levels between two players within a given population in a zero-sum game.

In this system, each player is assigned an initial ELO score, often set at 1200. The ELO score can decrease initially but is expected to progressively increase during training. The score is determined based on the outcomes of matches against other players. The player's rating depends on the ratings of their opponents and the results achieved against them.

The Elo score represents the relative skill level of a player in a zero-sum game. The difference in rating between two players serves as a predictor of match outcomes. If a player wins but is highly likely to win, they will only gain a few points from their opponent, indicating that they are significantly stronger.
