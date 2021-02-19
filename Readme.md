# Navigation --- Dueling-DQN 
## Solving Unity's navigation Environment with Dueling DQN

"The Dueling neural network architecture was introduced in 2015 in a paper called “Dueling Network Architectures for Deep Reinforcement Learning” by Ziyu Wang when he was a PhD student at the University of Oxford. This was arguably the first paper to introduce a custom deep neural network architecture designed specifically for value-based deep reinforcement learning methods. Dueling DQN is an architecture that separates the representation of state values and state-dependent action advantages via two separate streams."

The main idea behind this architecture is that knowing the value of each action at every timestep is not always needed.

Morales, M (2020). Grokking Deep Reinforcement Learning: Manning Publications

## The Environment
For this project, you will train an agent to navigate (and collect bananas!) in a large, square world.


A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

- 0 - move forward.
- 1- move backward.
- 2 - turn left.
- 3 - turn right.

The task is episodic, and in order to solve the environment, your agent must get an average score of +13 over 100 consecutive episodes.

![banana](https://user-images.githubusercontent.com/39303516/108419424-7c8b4300-7200-11eb-84b8-ec25f4f32850.gif)
## Requirements
- Pytorch
- Pytorn 3.6
- Unityagent
