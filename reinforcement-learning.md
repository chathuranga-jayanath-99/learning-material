# Reinforcement Learning

src - https://www.youtube.com/watch?v=Mut_u40Sqz4 

done by - Nicholas Renotte 

## Applications of RL 
- autonomous driving 
- securities trading 
- neural network architecture search 
- simulated training of robots 

## Limitations and considerations 
- for simple problems RL can be overkill
- assumes the env is markovian
- training time is long 

## Setup 
1. install required dependencies 
```
# Stable Baselines Install
!pip install stable_baselines3[extra]
```
```python3
import os 
import gym 
from stable_baseline3 import PPO 
from stable_baseline3.common.vec_env import DummyVecEnc 
from stable_baseline3.common.evaluation import evaluate_policy 
```

2. Load Environments
stable baselines install - https://gym.openapi.com/docs/
```python3
environment_name = "CartPole-v0 # Case sensitive
env = gym.make(environment_name)

episodes = 5
for episode in range(1, episodes+1):
  state = env.reset()
  donce = False
  score = 0
  
  while not done:
    env.render()
    action = env.action_space.sample()
    n_state, reward, done, info = env.step(action)
    score += reward 
  print('Episode:{} Score:{}'.format(episode, score))
env.close()
```

values taken from 
```python3
env.reset()
```
given to the reinforcement learning model. 

`env.action_space.sample()` provide random number 0, 1
`env.observation_space.sample()` result of this will look like?

what is the task of `env.step()` ?

4. 
