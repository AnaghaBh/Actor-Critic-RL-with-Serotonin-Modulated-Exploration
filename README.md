# Actor-Critic Reinforcement Learning with Serotonin-Modulated Exploration

## Overview

This project implements a simple Actor-Critic reinforcement learning agent in a discrete environment, with a biologically inspired extension: **serotonin-modulated exploration**.

The model explores how neuromodulatory signals (here, serotonin) can influence decision-making by controlling the balance between exploration and exploitation.

---

## Environment

A simple 1D environment with 5 states:

- The agent starts at state 0  
- The goal state is 4  
- Actions:
  - `0` → move left  
  - `1` → move right  

### Reward Structure
- Reward = 1 if goal state is reached  
- Reward = 0 otherwise  

---

## Model: Actor-Critic

The agent consists of two components:

### Critic
- Learns a **state-value function** \( V(s) \)
- Updated using Temporal Difference (TD) learning:
  δ = r + γV(s') − V(s)
---

### Actor
- Learns a **policy** \( π(a|s) \)
- Uses a softmax distribution over action preferences  
- Updated using the TD error signal from the critic  

---

## Serotonin-Modulated Exploration

A key feature of this model is the introduction of a **serotonin parameter**, which modulates exploration.

- Exploration is controlled via the **softmax temperature**
- Temperature is defined as:
  temperature = 1 − serotonin_level

  
### Interpretation
- High serotonin → low temperature → less exploration (more deterministic behaviour)  
- Low serotonin → high temperature → more exploration  

This provides a simple computational analogy to neuromodulatory control in biological systems.

---

## Training

- Episodes: 100  
- Maximum steps per episode: 20  
- The agent learns to reach the goal state efficiently over time  

During training:
- The agent selects actions using a softmax policy  
- Updates value estimates and policy using TD error  
- Gradually improves its behaviour  

---

## Output

The program prints:
- Action choices and probabilities  
- State transitions  
- TD error values  
- Updated value function and policy  
- Episode rewards  

This makes the learning process fully interpretable step-by-step.

---

## Tech Stack

- Python  
- NumPy  

---

## Key Insights

- Actor-Critic methods effectively learn optimal behaviour even in simple environments  
- Exploration is critical in early learning stages  
- Modulating exploration via a biologically inspired parameter provides a useful framework for modelling behaviour  

---

## Future Work

- Extend to larger or continuous environments  
- Introduce stochastic rewards  
- Model additional neuromodulators (e.g., dopamine for reward prediction error)  
- Compare with Q-learning and policy gradient methods  

---

## How to Run

```bash
python actor_critic.py
