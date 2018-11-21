# Collaboration and Competition Tennis

### Models

The actor model uses 3 Linear layers with 600 nodes apiece. The critic model uses 4 Linear layers with varying nodes each (600, 500, 400). Identical to Last project. The noise applied to this is significantly higher than the noise of the previous project, however, the noise is multiplied by epsilon which decays every episode to a minimum of 0.01. 

### Learning Algorithm

The learning algorithm uses deep deterministic policy gradient (DDPG) to train. It uses one neural network, the actor to provide actions from states, and the second takes both states and actions to estimate the reward that will be produced.

### Learning parameters

Epsilon start = 1.0

Epsilon min = 0.01

Epsilon decay = 0.997

BUFFER_SIZE = int(1e6) # replay buffer size

BATCH_SIZE = 128 # minibatch size

GAMMA = 0.99 # discount factor

TAU = 1e-3 # for soft update of target parameters

LR_ACTOR = 5e-5 # learning rate of the actor

LR_CRITIC = 1e-4 # learning rate of the critic

WEIGHT_DECAY = 0.0000 # L2 weight decay

Learns from 3 samples at each step

For noise: mu=0.1, theta=1.5, sigma=0.2

### The results

Local average and local max refer to the average and max over 10 episodes. Max refers to the maximum score over all episodes, Average is the 100 episode average. 

The environment took 486 episodes to reach an average of 0.505. With a maximum of 2.6

![image](https://github.com/jmkGithub/CollaborationCompetitionTennis/blob/master/ScorePlot.jpg)

### The future

I had begun implementing an checkpoint system that would save the models at points where they produced the highest scores. The idea being that I can reload these points and clear the buffer to "reset" the training, this would be used to recover if the training starts to perform badly and does not show signs of improvement. This was not implemented as I sufficiently met project objectives with out this. A future would be to implement the model recovery in an effort to improve stability.
