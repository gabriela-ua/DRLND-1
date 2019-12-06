# Udacity Deep Reinforcement Learning Nanodegree

# Project 3: Collaboration and Competition

[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/42135622-e55fb586-7d12-11e8-8a54-3c31da15a90a.gif "Soccer"

### Goal of the Project


For this project, you will work with the [Tennis](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis) environment.

![Trained Agent][image1]

In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1.  If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01.  Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation.  Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping. 

The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single **score** for each episode.

The environment is considered solved, when the average (over 100 episodes) of those **scores** is at least +0.5.

## Project requirements: See 'requirements.txt'


## Approach
The high-level steps taken in building an agent that solves this environment.

1. Start the Environment
1. Evaluate the state and action space.
1. Implement the learning algorithm.
1. Results

### 1. Start the Environment
Import the required libraries and create the UnityEnvironment

### 2. Evaluate the state and action space.
The state space has 24 dimensions which include the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

### 3.Implement the learning algorithm.
The algorithm used is Multi-Agent Deep Deterministic Policy Gradients (MADDPG).
The final hyper-parameters used were as follows (n_episodes=2500, max_t=1000).

- BUFFER_SIZE = int(1e6)  - # replay buffer size
- BATCH_SIZE = 128        -# minibatch size
- LR_ACTOR = 1e-3        - # learning rate of the actor
- LR_CRITIC = 1e-3        - # learning rate of the critic
- WEIGHT_DECAY = 0       - # L2 weight decay
- LEARN_EVERY = 10        - # learning timestep interval
- LEARN_NUM = 5           - # number of learning passes
- GAMMA = 0.99           -  # discount factor
- TAU = 8e-3              - # for soft update of target parameters
- OU_SIGMA = 0.2          - # Ornstein-Uhlenbeck noise parameter, volatility
- OU_THETA = 0.15         - # Ornstein-Uhlenbeck noise parameter, speed of mean reversion
- EPS_START = 5.0         - # initial value for epsilon in noise decay process in Agent.act()
- EPS_EP_END = 300        - # episode to end the noise decay process
- EPS_FINAL = 0          - # final value for epsilon after decay




### 4.Results

Plots and Results are shown in the Jupyter notebook (Tennis_v4 _AP.ipynb) and Report.

### For additional information:
Please see the Jupyter Notebook: 'Tennis_v4 _AP.ipynb'

# Try to train your own agents!!!
The original Udacity repository for this project can be found [here](https://github.com/udacity/deep-reinforcement-learning/tree/master/p3_collab-compet) 



### Getting Started
#### Clone this repository using Git version control system
If you are not sure about having Git installed in your system, run the following command to verify that:

```
$ git --version
```
If you need to install it, follow [this link](https://git-scm.com/downloads) to do so.

Having Git installed in your system, you can clone this repository by running the following command:

```
$ git clone https://github.com/silviomori/udacity-deep-reinforcement-learning-p3-collab-compet.git
```  

### Installing Miniconda
Miniconda is a free minimal installer for conda. It is a small, bootstrap version of Anaconda that includes only conda, Python, the packages they depend on, and a small number of other useful packages, including pip, zlib, and a few others.  

If you would like to know more about Anaconda, visit [this link](https://www.anaconda.com/).

In the following links, you find all the information to install **Miniconda** (*recommended*)

### Configuring the local environment
- Option 1: Using the environment descriptor file

The environment descriptor file included in this repository describes all the packages required to set up the environment.
Run the following commands to configure it.

#### for Linux:
$ conda create -f environment-linux.yml  
$ conda activate drlnd-p3-collab-compet  

#### for Windows:
$ conda create -f environment-windows.yml  
$ conda activate drlnd-p3-collab-compet  

- Option 2: Installing the packages
If you have problems to create the environment following the steps above, alternatively you can create the environment and install the required packages by following the steps below.

#### 1. Create the environment

$ conda create --name drlnd-p3-collab-compet python=3.6 -y
$ conda activate drlnd-p3-collab-compet

#### 2. Install PyTorch
Follow this link to select the right command for your system.
Here, there are some examples which you can use, if it fit in your system:

#### a. Linux or Windows

#### Run this command if you have an NVIDIA graphic card and want to use it  
$ conda install pytorch cudatoolkit=10.1 -c pytorch -y

#### Run this command, otherwise
$ conda install pytorch cpuonly -c pytorch -y

#### b. Mac
MacOS Binaries do not support CUDA, install from source if CUDA is needed

$ conda install pytorch -c pytorch -y

#### 3. Install Unity Agents

$ pip install unityagents

### Download the Unity environment with the Agents

Download the environment from one of the links below and decompress the file into your project folder.
You need only select the environment that matches your operating system:

Download the environment from one of the links below.  You need only select the environment that matches your operating system:

    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
    
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
    
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
    
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)
    
    
   (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

   (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux_NoVis.zip) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)

- Place the file in the DRLND GitHub repository, in the `p3_collab-compet/` folder, and unzip (or decompress) the file. 

### Instructions

Follow the instructions in `Tennis.ipynb` to get started with training your own agent!  


