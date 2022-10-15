# Learning Algorithm

In this project, I used MMDDPG to solve the given environment. The code starts from DDPG code for prev project.
I modified several codes to convert DDPG for multi-agent use.

### MADDPG algorithm
Multi-Agent DDPG(MADDPG) algorithm is a multi-agent version of DDPG ([Multi Agent Actor Critic for Mixed Cooperative Competitive environments](https://papers.nips.cc/paper/7217-multi-agent-actor-critic-for-mixed-cooperative-competitive-environments.pdf)). In this algorithm, a single critic receives the actions and state observations as input from all agents. To implement this algorithm, I modified codes so that two other agents can share replay memory and learn from the common memory.

### DDPG algorithm
![DDPG](https://user-images.githubusercontent.com/55370676/195970978-28a2dd2d-05bc-4efa-941a-c0cff805464c.png)

DDPG algorithm is a base algorithm of MMDDPG. The critic in DDPG is used to approximate maximizer over the Q values of the next state, not as a learned baseline. DDPG uses a replay buffer and soft updates to the target network to get a faster convergence.

#### Replay buffer and Gradient Clipping
The function Step() decides to learn according to the parameter UPDATE_CYCLE, SAMPLE_NUM in maddpg_agent.py.

Gradient clipping was applied when training the critic network. (Agent.learn() in ddpg_agent.py)

    torch.nn.utils.clip_grad_norm_(self.critic_local.parameters(), 1)


#### Exploitation and Exploration
I assumed that the main reason for not converging result was too much exploration made during the training process.
So, I tried to adjust exploitation and exploration ratio by applying an epsilon parameter to decay the noise.(in maddpg_agent.py)

    EPS_START = 1.0
    EPS_END = 0.05
    EPS_DECAY_RATE = 1e-6
    
    def act(self, state, add_noise=True):
        ...
        if add_noise:
            action += self.noise.sample() * self.epsilon  
        return np.clip(action, -1, 1)
        
Added epsilon parameter decreased the noise over time as the agent gains more experience.
Then it started to converge and get higher scores as time goes by.


First, I used parameters just as I used at project #2. The result was just like the plot below. 
It seemed to be not working and unsuccessful to learn.

![nonlearning - 1](https://user-images.githubusercontent.com/55370676/195971703-e392c58d-9c60-4583-bccf-92ca0c248ba1.png)

So , I fixed some error and modified hyperparameters to converge earlier. To promote higher exploitation rather than exploration, TAU, EPS_START was raised.
After plenty of tries, I got successful results. The hyperparameters and the plot of result are written below.

### Hyperparameters

    BUFFER_SIZE = int(1e5)  # replay buffer size
    BATCH_SIZE = 128        # minibatch size
    GAMMA = 0.99            # discount factor
    TAU = 1e-2              # for soft update of target parameters
    LR_ACTOR = 1e-3         # learning rate of the actor 
    LR_CRITIC = 1e-3        # learning rate of the critic
    WEIGHT_DECAY = 0        # L2 weight decay
    UPDATE_CYCLE = 20       # the (local) actor and critic networks are updated 20 times in a row (one for each agent)
    SAMPLE_NUM = 10         # using 20 different samples from the replay buffer
    EPS_START = 1.0         # epsilon parameter applying to noise (for exploitation)
    EPS_END = 0.05          # epsilon decay
    EPS_DECAY_RATE = 1e-4   # epsilon decay

# Plot of Rewards

![image](https://user-images.githubusercontent.com/55370676/195972826-0401a9f7-e697-4065-a8f7-b6213d53ff6f.png)

The agent solved the environment at the 1678th episode, since the average of the average scores from episodes 1579 to 1678 (inclusive) was greater than +0.5.
The detail process is written in "4. ② Train the Agent with DDPG" of <Tennis.ipynb>


# Ideas for Future Work
Fine tuning can have better results. I feel so tricky at parameter tuning due to lack of experience but it seems to be possible to have better results with parameter modifications.

Advanced algorithms such as Trust Region Policy Optimization (TRPO), Truncated Natural Policy Gradient (TNPG) can be used to base algorithm of multi-agent method to achieve better performance according to [Benchmark](https://arxiv.org/abs/1604.06778).

Distributed Distributional Deterministic Policy Gradients ([D4PG](https://openreview.net/forum?id=SyZipzbCb)) algorithm as another method for adapting DDPG can be used for this project.
