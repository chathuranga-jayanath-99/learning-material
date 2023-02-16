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
