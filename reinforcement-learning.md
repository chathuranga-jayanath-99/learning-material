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
### 1. install required dependencies 
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

### 2. Load Environments
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

Env. functions
- `env.reset()` - reset the env and obtain initial observations
- `env.render()` - visualise the env
- `env.step()` - apply an action to env 
- `env.close()` - close down render frame

### 3. Training 

RL algorithms
- model-free RL
  - policy optimization
  - Q-Learning
- model based RL
  - Learn the model 
  - given the model

src - https://stable-baselines3.readthedocs.io/en/master/

understaning training metrics 
- evaluation metrics
- time metrics 
- loss metrics 
- other metrics 

```python3
# MAKE YOUR DIRECTORIES FIRST
log_path = os.path.join('Training', 'Logs')

env = gym.make(environment_name)
env = DummyVecEnv([lambda: env])
model = PPO('MlpPolicy', env, verbose=1, tesorboard_log=log_path)

model.learn(total_timesteps=20000)
```

### 4. Save and Reload Model
```python3
PPO_Path = os.path.join('Training', 'Saved Models', 'PPO_Model_Cartpole')
model.save(PPO_Path)
del model 
model = PPO.load(PPO_Path, env=env)
```

### 5. Testing and Evaluation
evaluation methods
- monitor tensorboard

evaluation_policy(model, env, n_eval_episodes=10, render=True) 

### 6. Test Model

```python3
episodes = 5
for episode in range(1, episodes+1):
  state = env.reset()
  done = False
  score = 0
  
  while not done:
    env.render()
    action, _ = model.predict(obs)
    obs, reward, done, info = env.step(action)
    score += reward 
  print('Episode:{} Score:{}'.format(episode, score))
env.close()
```

### 7. View Logs in Tensorboard
```python3
training_log_path = os.path.join(log_path, 'PPO_2')
```

`!tensorboard --logdir={training_log_path}`
go and view the localhost tensorboard page.

## Applying Callbacks 
