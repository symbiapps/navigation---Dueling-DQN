## Report
### Dueling DQN

The difference in Dueling DQN is in the structure of the model. The model is created in a way to output the formula below:
![1_sHh7CknXpNikJG6LWpIpGg](https://user-images.githubusercontent.com/39303516/108522382-c4f73f00-729a-11eb-88b2-a27a9f16b52d.png)


Here, the V(s) stands for the Value of state s and A is the Advantage of doing action a while in state s. The Value of a state is independent of action. It means how good is it to be in a particular state. But what is an Advantage? How is it different from Q-value? Let’s explain it with an example. The agent might be in a state where each of the actions would give the same Q-value. So there is no good action in this state. What would happen if we divide the Q-value to Value of a state and the Advantage that each action has. If every action has the same result, then the Advantage of each action will have the same value. Now, if we subtract the mean of all the Advantages from each advantage, we get zero (or close to zero) and Q-value would actually be the Value that the state has. So overtime the Q-value would not overshoot. The states that are independent of action would not have a high Q-value to train on.
("Deep Reinforcement learning: DQN, Double DQN, Dueling DQN, Noisy DQN and DQN with Prioritized Experience Replay", 2019)





class QNetwork(nn.Module):
    """Actor (Policy) Model."""

    def __init__(self, state_size, action_size, seed, fc1_units=64, fc2_units=64):
        """Initialize parameters and build model.
        Params
        ======
            state_size (int): Dimension of each state
            action_size (int): Dimension of each action
            seed (int): Random seed
            fc1_units (int): Number of nodes in first hidden layer
            fc2_units (int): Number of nodes in second hidden layer
        """
        super(QNetwork, self).__init__()
        self.seed = torch.manual_seed(seed)
        self.fc1 = nn.Linear(state_size, fc1_units)
        self.fc2 = nn.Linear(fc1_units, fc2_units)
        self.fc3 = nn.Linear(fc2_units, action_size)

    def forward(self, state):
        """Build a network that maps state -> action values."""
        x = F.relu(self.fc1(state))
        x = F.relu(self.fc2(x))
        return self.fc3(x)



Dueling DQN is very simple to apply the only changes in my example are bolded in the lower model.





class QNetwork(nn.Module):
    """Actor (Policy) Model."""

    def __init__(self, state_size, action_size, seed, fc1_units=64):
        """Initialize parameters and build model.
        Params
        ======
            state_size (int): Dimension of each state
            action_size (int): Dimension of each action
            seed (int): Random seed
            fc1_units (int): Number of nodes in first hidden layer
           
        """
        super(QNetwork, self).__init__()
        self.seed = torch.manual_seed(seed)
        self.fc1 = nn.Linear(state_size, fc1_units)
   - self.advantage = nn.Linear(fc1_units, 4)
   - self.value = nn.Linear(fc1_units, 4)
        
        self.activation = nn.Tanh()

    def forward(self, state):
        """Build a network that maps state -> action values."""
        output1 = self.fc1(state)
        output1 = self.activation(output1)
        
  - output_advantage = self.advantage(output1)
  - output_value = self.value(output1)
  - output_final =  output_value  + (output_advantage - output_advantage.mean())
        
        return output_final
        
    
![reward](https://user-images.githubusercontent.com/39303516/108601850-c98c2800-736c-11eb-81a8-b2cb8f2db1f7.png)

The  Dueling DQN choice worked out well it was able to solved the enviroment by the 900th episode.

The hyperparameter values used to train the agent as follows
- BUFFER_SIZE = int(1e5)  # replay buffer size
- BATCH_SIZE = 64         # minibatch size
- GAMMA = 0.99            # discount factor
- TAU = 1e-3              # for soft update of target parameters
- LR = 5e-4               # learning rate 
- UPDATE_EVERY = 4        # how often to update the network


