# Deep Reinforcement Project #3 - Udacity DeepRL Nanodegree course

### 1. Project Details

   In this environment, two agents control rackets to bounce a ball over a net. Each agent should keep the ball in play.
      
   - Reward : +0.1 when an agent hits the ball over the net, -0.01 when an agent lets a ball hit the ground or hits the ball out of bounds.

   - State Space : The state space has 8 dimensions and contains the agent's position and velocity of the ball and racket.

   - Vector Action Space (continous) : Each action is a vector with two numbers corresponding to movement toward (or away from) the net, and jumping.

   - Goal : Environment is solved when agents get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents).
            The average score means the average of each 20 agents' scores in one episode.
 

### 2. Getting Started

    File list  : ① Tennis.ipynb ② maddpg_agent.py ③ model.py ④ checkpoint_actor1.pth ⑤ checkpoint_critic1.pth ⑥ checkpoint_actor2.pth ⑦ checkpoint_critic2.pth
1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux_NoVis.zip) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)

2. Place the file in the DRLND GitHub repository, in the `p3_collab-compet/` folder, and unzip (or decompress) the file. 
        
        
#### Dependencies

To set up your python environment to run the code in this repository, follow the instructions below.

① Create (and activate) a new environment with Python 3.6.

	- __Linux__ or __Mac__: 
	```bash
	conda create --name drlnd python=3.6
	source activate drlnd
	```
	- __Windows__: 
	```bash
	conda create --name drlnd python=3.6 
	activate drlnd
	```
	
② If running in **Windows**, ensure you have the "Build Tools for Visual Studio 2019" installed from this [site](https://visualstudio.microsoft.com/downloads/).  This [article](https://towardsdatascience.com/how-to-install-openai-gym-in-a-windows-environment-338969e24d30) may also be very helpful.  This was confirmed to work in Windows 10 Home.  

③ Follow the instructions in [this repository](https://github.com/openai/gym) to perform a minimal install of OpenAI gym.  
	- Next, install the **classic control** environment group by following the instructions [here](https://github.com/openai/gym#classic-control).
	- Then, install the **box2d** environment group by following the instructions [here](https://github.com/openai/gym#box2d).
	
④ Clone the repository (if you haven't already!), and navigate to the `python/` folder.  Then, install several dependencies.  
    ```bash
    git clone https://github.com/udacity/deep-reinforcement-learning.git
    cd deep-reinforcement-learning/python
    pip install .
    ```

⑤ Create an [IPython kernel](http://ipython.readthedocs.io/en/stable/install/kernel_install.html) for the `drlnd` environment.    
    ```bash
    python -m ipykernel install --user --name drlnd --display-name "drlnd"
    ```

⑥ Before running code in a notebook, change the kernel to match the `drlnd` environment by using the drop-down `Kernel` menu. 


### 3. Instructions
   - Follow the instructions in 'Tennis.ipynb'.
   - Run the codes below '4. It's Your Turn!' in 'Continuous_Control.ipynb' to check the trained agent.
   - 'maddpg_agent.py','model.py', 'checkpoint_actor.pth' and 'checkpoint_critic.pth' should be included in the same project with 'Tennis.ipynb'.
   - Experiment results of the trained model was already recorded in the notebook files.
   - 'checkpoint_actor1.pth', 'checkpoint_actor2.pth', 'checkpoint_critic2.pth' and 'checkpoint_critic.pth' contain trained networks' weights.
