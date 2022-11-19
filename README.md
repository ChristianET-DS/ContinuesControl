# ContinuesControl

Project Details
The project uses the unity agent environment  Reacher.

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible.
The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.
Example of untrained agents.			Trained Agents 

 
 
 
 
 
 
 
 
 
 
For the implementation I used DDPG as the base algorithm.
DDPG 
Deep Deterministic Policy Gradient (DDPG) is an algorithm which concurrently learns a Q-function and a policy. It uses off-policy data and the Bellman equation to learn the Q-function, and uses the Q-function to learn the policy.


 
DDPG is an off-policy algorithm.
DDPG can only be used for environments with continuous action spaces.
DDPG can be thought of as being deep Q-learning for continuous action spaces.
The Spinning Up implementation of DDPG does not support parallelization.
DDPG use an Actor-Critic method, reason why we implemented it as two models
Actor - It proposes an action given a state.
Critic - It predicts if the action is good (positive value) or bad (negative value) given a state and an action.
Why two networks? Because it adds stability to training. In short, we are learning from estimated targets and Target networks are updated slowly, hence keeping our estimated targets stable.
Conceptually, this is like saying, "I have an idea of how to play this well, I'm going to try it out for a bit until I find something better", as opposed to saying "I'm going to re-learn how to play this entire game after every move".
DDPG uses experience relay : We store a list of tuples (state, action, reward, next_state), and instead of learning only from recent experience, we learn from sampling all of our experience accumulated so far.
 
 
Case one agent:
The task is episodic, and in order to solve the environment, the agent must get an average score up to 30 over 100 consecutive episodes.
Reacher environment  used: Reacher_One_Linux_NoVis.x86_64
Case Multi Agent case:
The agents must get an average score up to 30 (over 100 consecutive episodes, and over all agents).
After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 20 (potentially different) scores. We then take the average of these 20 scores. This yields an average score for each episode ( avg of the 20 agents).
Reacher environment  used:  Reacher.x86_64
Getting Started:
What you need to install 
Pytorch
Python 3x
Instructions:
How to Run, simple agent:
Github Link:
https://github.com/ChristianET-DS/ContinuesControl/tree/main/SingleAgent
