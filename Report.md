# Learning Algorithm


### MADDPG algorithm


### Hyperparameters




# Plot of Rewards



The agent solved the environment at the 7th episode, since the average of the average scores from episodes 8 to 107 (inclusive) was greater than +30.
The detail process is written in "4. ② Train the Agent with DDPG" of <Continuous_Control.ipynb>


# Ideas for Future Work
Advanced algorithms such as Trust Region Policy Optimization (TRPO), Truncated Natural Policy Gradient (TNPG) can achieve better performance according to [Benchmark](https://arxiv.org/abs/1604.06778).

Distributed Distributional Deterministic Policy Gradients ([D4PG](https://openreview.net/forum?id=SyZipzbCb)) algorithm as another method for adapting DDPG can be used for this continuous control project.
