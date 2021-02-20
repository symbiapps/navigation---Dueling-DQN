# Navigation --- Dueling-DQN 
## Solving Unity's navigation Environment with Dueling DQN

The Dueling neural network architecture was introduced in 2015 in a paper called “Dueling Network Architectures for Deep Reinforcement Learning” by Ziyu Wang when he was a PhD student at the University of Oxford. This was arguably the first paper to introduce a custom deep neural network architecture designed specifically for value-based deep reinforcement learning methods. Dueling DQN is an architecture that separates the representation of state values and state-dependent action advantages via two separate streams.("Grokking Deep Reinforcement Learning",2020)

The main idea behind this architecture is that knowing the value of each action at every timestep is not always needed.



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
- [Udacity](https://github.com/udacity/deep-reinforcement-learning/tree/master/p1_navigation#getting-started)
- [Udacity](https://classroom.udacity.com/nanodegrees/nd893/parts/6b0c03a7-6667-4fcf-a9ed-dd41a2f76485/modules/e7499d4f-24f9-42ec-9864-23adcfa4e241/lessons/69bd42c6-b70e-4866-9764-9bfa8c03cdea/concepts/319dc918-bd2c-4d3b-80a5-063bb5f1905a)
