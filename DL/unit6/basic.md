# UNIT 6 – REINFORCEMENT LEARNING (RL) & DEEP REINFORCEMENT LEARNING

### 10 Marks Detailed Answers (Combined Repeated Questions)

---

# 1. REINFORCEMENT LEARNING (RL)

### Covers Questions:

**1, 2, 3, 4, 5**

---

# Reinforcement Learning (RL)

## Definition

Reinforcement Learning (RL) is a machine learning technique in which an **agent learns by interacting with an environment** and receives rewards or penalties for its actions.

The objective of the agent is to learn an optimal strategy that maximizes cumulative rewards over time.

Unlike supervised learning, RL does not require labeled data. Learning occurs through **trial and error**.

---

## Basic Components of RL

### 1. Agent

Decision maker.

Examples:

* Robot
* Self-driving car
* Chess player

---

### 2. Environment

The world with which the agent interacts.

Examples:

* Road
* Chess board
* Video game

---

### 3. State (S)

Current situation of the environment.

Example:
In Tic-Tac-Toe:
Current board configuration.

---

### 4. Action (A)

Possible move performed by agent.

Example:
Move left, move right, place X.

---

### 5. Reward (R)

Feedback from environment.

Example:

```text
Win = +10
Draw = +1
Lose = -10
```

---

### 6. Policy (π)

Strategy followed by agent.

Policy determines:

```text
State → Action
```

---

## Working of RL

### Step 1

Agent observes state.

### Step 2

Agent selects action.

### Step 3

Environment changes.

### Step 4

Reward is received.

### Step 5

Agent updates knowledge.

### Step 6

Process repeats.

---

## Characteristics of RL

### 1. Trial-and-Error Learning

Learns from experience.

### 2. Delayed Reward

Reward may come later.

### 3. Sequential Decision Making

Current decisions affect future states.

### 4. Goal-Oriented Learning

Focuses on maximizing reward.

### 5. Exploration and Exploitation

Balances learning and using knowledge.

---

# Types of Reinforcement Learning

## 1. Positive Reinforcement

Reward is given for good action.

Example:

```text
Correct Action → + Reward
```

Advantages:

* Faster learning.
* Better performance.

---

## 2. Negative Reinforcement

Penalty removed after correct action.

Example:

```text
Obstacle removed after right move
```

Encourages desirable behavior.

---

# Active vs Passive Reinforcement Learning

| Active RL                 | Passive RL           |
| ------------------------- | -------------------- |
| Learns policy             | Follows fixed policy |
| Chooses actions           | No action selection  |
| More complex              | Simpler              |
| Optimizes strategy        | Evaluates strategy   |
| Example: Self-driving car | Policy evaluation    |

---

# Advantages of RL

### 1. Learns Automatically

No labeled data needed.

### 2. Adapts to Dynamic Environments

Useful in changing situations.

### 3. Handles Complex Problems

Suitable for games and robotics.

### 4. Long-Term Optimization

Maximizes future rewards.

---

# Disadvantages of RL

### 1. Requires Large Training Time

Many interactions needed.

### 2. High Computational Cost

Needs significant resources.

### 3. Exploration Risk

Wrong actions may occur.

### 4. Reward Design Difficulty

Poor rewards lead to poor learning.

---

# Applications

* Robotics
* Self-driving cars
* Game AI
* Recommendation systems
* Resource allocation

---

# 2. MARKOV DECISION PROCESS (MDP)

### Covers Questions:

**6, 7, 8, 9**

---

# Markov Decision Process (MDP)

## Definition

MDP is a mathematical framework used to model decision-making problems where outcomes are partly random and partly controlled by an agent.

It forms the foundation of Reinforcement Learning.

---

# Markov Property

The future depends only on the present state.

It does not depend on past history.

Mathematically:

```text
P(St+1 | St)
```

not

```text
P(St+1 | St, St−1, St−2 ...)
```

---

## Components of MDP

### 1. State (S)

All possible situations.

Example:
Robot position.

---

### 2. Action (A)

Available actions.

Example:
Move Left, Right.

---

### 3. Transition Probability (P)

Probability of moving to next state.

```text
P(S'|S,A)
```

---

### 4. Reward Function (R)

Immediate feedback.

```text
R(S,A)
```

---

### 5. Policy (π)

Action-selection strategy.

---

# MDP Diagram

```text
Current State
      |
      V
   Action
      |
      V
Environment
      |
      V
Next State + Reward
```

---

# Importance of MDP

* Models uncertainty.
* Forms basis of RL algorithms.
* Helps optimize long-term rewards.

---

# Example

Robot navigation:

State:
Current location.

Action:
Move North.

Reward:
+10 if goal reached.

---

# 3. DYNAMIC PROGRAMMING IN RL

### Covers Questions:

**10, 11, 12, 13, 14**

---

# Dynamic Programming (DP)

## Definition

Dynamic Programming is a collection of methods used to solve MDPs when the complete model of the environment is known.

DP computes optimal policies through iterative updates.

---

## Requirements

Must know:

* States
* Actions
* Rewards
* Transition probabilities

---

# Policy Iteration

Policy Iteration consists of two steps.

---

## Step 1: Policy Evaluation

Calculate value of each state.

```text
Vπ(s)
```

---

## Step 2: Policy Improvement

Improve policy using calculated values.

---

### Process

```text
Policy
   ↓
Evaluation
   ↓
Improvement
   ↓
Optimal Policy
```

---

## Advantages

* Accurate solution.
* Guaranteed convergence.

---

# Value Iteration

Instead of evaluating complete policy:

Directly update values.

Formula:

```text
V(s)=max[R+γV(s')]
```

---

### Process

```text
Initialize Values
       ↓
Update Values
       ↓
Convergence
       ↓
Optimal Policy
```

---

# Policy Iteration vs Value Iteration

| Policy Iteration       | Value Iteration        |
| ---------------------- | ---------------------- |
| Policy + Value Updates | Only Value Updates     |
| Faster convergence     | Simpler implementation |
| More memory            | Less memory            |

---

# DP in RL vs Traditional DP

| Traditional DP               | RL DP            |
| ---------------------------- | ---------------- |
| Solves optimization problems | Solves MDPs      |
| Deterministic                | Stochastic       |
| Fixed solution               | Policy learning  |
| Example: Knapsack            | Policy Iteration |

---

# 4. Q-LEARNING & DEEP Q LEARNING

### Covers Questions:

**15,16,17,18,19**

---

# Q-Learning

## Definition

Q-Learning is a model-free RL algorithm that learns the value of actions directly without knowing environment dynamics.

---

# Q-Value

Q-value measures:

```text
Expected future reward
```

for a state-action pair.

---

## Q-Table

```text
State | Left | Right
S1    | 10   | 5
S2    | 20   | 15
```

Agent chooses maximum value.

---

# Q-Learning Update Formula

```text
Q(s,a)=Q(s,a)+α[R+γmaxQ(s',a')−Q(s,a)]
```

Where:

α = Learning rate

γ = Discount factor

R = Reward

---

# Advantages

* No model required.
* Learns optimal policy.

---

# Deep Q-Learning (DQN)

## Problem with Q-Learning

Large state spaces make Q-table impossible.

---

## Solution

Replace Q-table with Deep Neural Network.

---

# DQN Architecture

```text
State
  |
Neural Network
  |
Q-values
  |
Best Action
```

---

# Working of DQN

### Step 1

Observe state.

### Step 2

Pass state to neural network.

### Step 3

Predict Q-values.

### Step 4

Select best action.

### Step 5

Receive reward.

### Step 6

Update network weights.

---

# DQN Advantages

* Handles huge state spaces.
* Works on images.
* Better scalability.

---

# Applications

* Atari games
* Robotics
* Autonomous driving

---

# 5. DEEP RECURRENT Q NETWORK (DRQN)

### Covers Questions:

**20,21**

---

# Deep Recurrent Q-Network (DRQN)

## Definition

DRQN extends DQN by adding recurrent layers such as **LSTM** or **RNN**.

This allows the agent to remember previous observations.

---

# Architecture

```text
State Sequence
      |
      V
     CNN
      |
      V
   LSTM/RNN
      |
      V
  Q Values
```

---

# Need for DRQN

DQN assumes full observation.

Real-world environments may provide partial information.

Example:

Video game frame shows only part of environment.

---

# Role of Recurrent Layer

### Memory

Stores previous states.

### Temporal Understanding

Learns sequence patterns.

### Better Decision Making

Uses past and present information.

---

# DRQN vs DQN

| DQN                           | DRQN                              |
| ----------------------------- | --------------------------------- |
| Single state                  | State sequence                    |
| No memory                     | Has memory                        |
| Fully observable environments | Partially observable environments |

---

# 6. DEEP REINFORCEMENT LEARNING (DRL)

### Covers Questions:

**22,23,24,25**

---

# Deep Reinforcement Learning (DRL)

## Definition

Deep Reinforcement Learning combines:

```text
Deep Learning + Reinforcement Learning
```

to solve complex decision-making problems.

---

# Architecture

```text
Environment
      ↑
      |
Reward
      |
Agent
      |
Deep Neural Network
      |
Action
```

---

# Working

### Step 1

Observe state.

### Step 2

Neural network extracts features.

### Step 3

Action selected.

### Step 4

Environment responds.

### Step 5

Reward received.

### Step 6

Network updated.

---

# Objectives of DRL

### 1. Learn Optimal Policy

Maximize rewards.

### 2. Handle High-Dimensional Inputs

Images, videos, sensors.

### 3. Reduce Human Intervention

Automatic feature learning.

---

# Challenges of DRL

### 1. Large Training Data

Requires millions of interactions.

### 2. High Computation

Needs GPUs.

### 3. Exploration Problem

Finding optimal actions is difficult.

### 4. Reward Sparsity

Rewards may be rare.

---

# Applications

* Self-driving cars
* Robotics
* Healthcare
* Finance
* Gaming

---

# 7. CHALLENGES OF REINFORCEMENT LEARNING

### Covers Questions:

**26,27**

---

# Challenges in Reinforcement Learning

## 1. Exploration vs Exploitation

Agent must balance:

* Trying new actions.
* Using known actions.

---

## 2. Sparse Rewards

Rewards occur rarely.

Learning becomes slow.

---

## 3. Delayed Rewards

Correct action may be rewarded much later.

---

## 4. Large State Space

Huge number of possible states.

---

## 5. High Computational Cost

Requires extensive training.

---

## 6. Sample Inefficiency

Needs many interactions.

---

## 7. Non-Stationary Environments

Environment changes over time.

---

## 8. Safety Issues

Wrong actions may cause damage.

Example:

Autonomous vehicles.

---

# 8. TIC-TAC-TOE USING REINFORCEMENT LEARNING

### Covers Questions:

**28,29,30,31**

---

# Tic-Tac-Toe using Reinforcement Learning

## Problem Formulation

### Agent

Computer player.

---

### Environment

Tic-Tac-Toe board.

---

### State

Current board configuration.

Example:

```text
X | O | -
---------
- | X | -
---------
O | - | -
```

---

### Actions

Place X in empty cell.

---

### Rewards

```text
Win  = +10
Draw = +1
Lose = -10
```

---

# Working

### Step 1

Observe board state.

### Step 2

Choose move.

### Step 3

Receive reward.

### Step 4

Update strategy.

### Step 5

Repeat over thousands of games.

---

# Learning Process

Initially:

Random moves.

After training:

Learns:

* Winning strategies.
* Blocking opponent.
* Creating opportunities.

---

# RL Formulation

```text
Board State
      ↓
Agent Action
      ↓
New Board State
      ↓
Reward
      ↓
Policy Update
```

---

# Advantages

* Learns automatically.
* No predefined rules required.
* Improves through experience.

---

# MOST IMPORTANT EXAM QUESTIONS (Highest Probability)

1. Reinforcement Learning – Definition, Characteristics, Advantages & Disadvantages
2. Active vs Passive Reinforcement Learning
3. MDP with Components and Markov Property
4. Dynamic Programming in RL
5. Policy Iteration vs Value Iteration
6. Q-Learning and DQN
7. Deep Reinforcement Learning Architecture
8. DRQN and DQN Comparison
9. Challenges in Reinforcement Learning
10. Tic-Tac-Toe using Reinforcement Learning

These 10 answers cover almost every question asked from Unit 6.
