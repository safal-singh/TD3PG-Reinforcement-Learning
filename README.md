# TD3PG-Reinforcement-Learning
Code for implementation of Twin Delayed Deep Deterministic Policy Gradient algorithm

Steps in the implementation:
1. ReplayBuffer class - maintains the replay memory (of size max_size) of transitions undertaken by the agent. Each transition is denoted by 5 variables -
      1. state - represents state of the agent at current instant.
      2. next_state - state of the agent at the next instant from the current one.
      3. action - action taken by agent to reach the next_state from current state.
      4. reward - feedback in the form of reward granted to the agent by environment for undertaking the action at current state.
      5. done - indicates whether the episode is completed (reached a point of no return, as described by the environment's rules) or not.
  
  
  
  The class has 2 methods -
      1. add - adds new Transition entry into Replay memory. Appends entries until the memory is full, after which new transitions replace the oldest entries.
      2. sample - Samples a subset of Replay memory of size batch_size for the networks to train. The transition elements - state, next_state, action, reward, done - are converted to numpy array and returned.
2. Actor class - defines the Neural network for Actors and the forward propagation method. The network 1 input (#neurons=no. of state variables), 2 hidden (400 followed by 300 neurons) and 1 output layer (#neurons=no. of possible actions).
