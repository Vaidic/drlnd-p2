# Report
## The Learning algorithm
> DDPG algorithm (Deep Deterministic Policy Gradients) based on Udacity DRL ddpg-bipedal notebook was used to solve the environment.
>
> The observation space, per agent, consists of 33 variables – corresponding to position, rotation, velocity, and angular velocities 
of the arm. Each action is a vector with four numbers with values between \[-1, 1\], corresponding to torque applicable to two joints.
>
> DDPG adapts the ideas of Deep Q-Learning to the continuous action domain. The actor network approximates the optimal policy deterministically. The critic evaluates the optimal action value function using the best believed action given by the actor network. DDPG also uses a repĺay buffer where experience tuples are stored. This implementation uses a simple replay buffer.
>
> For each time step and agent the Agent acts upon the state utilising a shared replay_buffer, actor_local, actor_target, actor_optimizer, critic_local, criticl_target and critic_optimizer networks.

## Model
Following structure was used for agent & critic: 

+ The Actor is a mapping of state to action values via 3 fully connected Linear layers with relu activation. The final output layer yields 4 values with tanh activation. The Actor networks utilised two fully connected layers with 256 and 128 units with relu activation and tanh activation for the action space. The network has an initial dimension the same as the state size.

  - Feature layer: Linear ReLu (33, 256)
  - First hidden layer: ReLu (256, 128)
  - Second hidden layer: Tanh (128, 4)

+ The Critic is a value function, measuring the quality of the actions via 3 fully connected Linear layers with relu activation with the third layer yielding the single output value.The Critic networks utilised two fully connected layers with 256 and 128 units with relu activation and linear activation. The critic network has an initial dimension the size of the state size plus action size.


## Hyperparameters
+ Learning rate (actor): 0.001
+ Learning rate (critic): 0.001
+ Discount factor (gamma): 0.99
+ Target network update frequency (target_update_frequency): 1000
+ Policy network update frequency (update_frequency): 4
+ Replay memory capacity (buffer_size): 100000
+ Batch size (batch_size): 256

## Performance
> Agent achieves average score **30.0** over 100 episodes at 125 episode. 

## Result 
![Result](result.png)

## Comments
During solving this problem, the biggest challenge was to set the learning rate & update frequency.
A small learning rate gave more stable training process, same was observed with update frequency of models. 
Too small was destabilizing training. 

## Future ideas
> I believe the results could be further improved using:

+ Actor and Critic NN could have more layers or more units per layer. The current setup was not stablizing, so increasing number of episode likely to result in higher scores.
+ Improvements made to DDPG, such as D3PG and D4PG, A3C and PPO will yield better result.
