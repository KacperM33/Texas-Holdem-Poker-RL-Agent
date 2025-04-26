# 🃏 Texas Hold'em Poker RL Agent 

A **Machine Learning agent** for **Texas Hold'em Poker**, developed using a **Reinforcement Learning** technique specifically, the **Dueling Deep Q-Network (Dueling DQN)** algorithm variant and evaluated within the RLCard environment.
<br>The project investigates the impact of **Neural Network Hyperparameter Tuning** on model performance, with both manual hyperparameter tuning and automatic tuning using Optuna.

## 📚 About This Project
This project was developed as part of my Engineering thesis in Computer Science. The goal was to build a **Reinforcement Learning** agent for Texas Hold'em Poker and explore the impact of neural network hyperparameter tuning on model performance.

## 🧰 Development Tools
- Python 3.12.2
- [PyTorch](https://pytorch.org)
- [RLCard](https://rlcard.org/index.html) (for Poker simulation)
- [Optuna](https://optuna.org) (for hyperparameter tuning)
- [Google Colab](https://colab.research.google.com) (Jupyter Notebook)

## 📊 Results
The project consists of five experiments focused on hyperparameter tuning and agent training strategies.

### 🧪 First Experiment
**Manual hyperparameter tuning** was performed by building a **neural network** with **two layers** containing different numbers of neurons. After identifying the best-performing agent, its learning rate was reduced. Additionally, the number of training episodes was increased from 10,000 to 50,000 once to test whether increasing the number of episodes would improve performance. Agents were trained against a random agent from the RLCard environment.<br>

A table with the results is shown below:
| **Agent** | **Neural Network** | **Learning Rate** | **Number of Episodes** | **Win Rate** | **Average Reward** |
|:---------:|:------------------:|:-----------------:|:----------------------:|:------------:|:------------------:|
| agent_0   | [64, 64]            | 0.001             | 10,000                  | -            | -                  |
| agent_1   | [128, 128]          | 0.001             | 10,000                  | 39.1%        | -3.216             |
| agent_2   | [256, 256]          | 0.001             | 10,000                  | 46.2%        | -0.59              |
| agent_3   | [512, 512]          | 0.001             | 10,000                  | 23.8%        | -3.5405            |
| agent_4   | [32, 32]            | 0.001             | 10,000                  | 49.3%        | 0.362              |
| agent_5   | [64, 64]            | 0.0001            | 10,000                  | 34.0%        | -2.306             |
| agent_6   | [64, 64]            | 0.001             | 50,000                  | 52.8%        | 1.387              |


The best agent from this experiment was **agent_6**, achieving a 52.8% win rate against the default created agent after being trained on 50,000 episodes. However, the performance gain did not justify the significantly longer training time. **Agent_0**, which was the default created agent, trained with the same parameters (**two layers with 64 neurons each and a learning rate of 0.001**) but on 10,000 episodes, completed training in around 15 minutes, whereas **agent_6** required approximately one and a half hours.<br>
Additionally, none of the other agents achieved win rate above 50%, so **agent_0** was selected as the best agent from this experiment.<br>

The chart below illustrates the training performance of **agent_0**:

![image](https://github.com/user-attachments/assets/49314139-17cd-4aee-a594-fcd57655619b)

(X-axis represents the number of episodes)<br>
(Y-axis represents the win ratio in percentages)

### 🧪 Second Experiment
The second experiment followed a similar approach to the first one but used **three-layer neural network architectures** instead of two. As before, agents were trained against a random agent from RLCard.

A table with the results is shown below:
| **Agent** | **Neural Network** | **Learning Rate** | **Number of Episodes** | **Win Rate** | **Average Reward** |
|:---------:|:------------------:|:-----------------:|:----------------------:|:------------:|:------------------:|
| agent_7   | [64, 64, 64]        | 0.001             | 10,000                  | 1.5%         | -0.8325            |
| agent_8   | [128, 128, 128]     | 0.001             | 10,000                  | 31.8%        | -6.302             |
| agent_9   | [256, 256, 256]     | 0.001             | 10,000                  | 49.7%        | 0.117              |
| agent_10  | [512, 512, 512]     | 0.001             | 10,000                  | 33.4%        | -6.458             |
| agent_11  | [256, 256, 256]     | 0.0001            | 10,000                  | 42.5%        | -2.452             |


The best agent from this experiment was **agent_9**, featuring **three layers of 256 neurons each and a learning rate of 0.001**, achieving 49.7% win rate against the default created agent.<br>

The chart below illustrates the training performance of **agent_9**:

![image](https://github.com/user-attachments/assets/898f242b-0dc3-44ab-9c3e-fd53f50ec4a5)

(X-axis represents the number of episodes)<br>
(Y-axis represents the win ratio in percentages)

### 🧪 Third Experiment
In the third experiment, the best-performing agents from the previous experiments were selected. Instead of training them against a random agent, they were trained against **previously trained agents**. For example, an agent from the first experiment was trained against an agent from the second experiment as well as against itself.

A table with the results is shown below:
| **Agent** | **Neural Network** | **Training Agent** | **Learning Rate** | **Win Rate** | **Average Reward** |
|:---------:|:------------------:|:------------------:|:-----------------:|:------------:|:------------------:|
| agent_12  | [64, 64]            | agent_0            | 0.001             | 47.7%        | -0.7               |
| agent_13  | [256, 256, 256]     | agent_0            | 0.001             | 46.1%        | -0.871             |
| agent_14  | [256, 256, 256]     | agent_9            | 0.001             | 12.2%        | -5.4475            |
| agent_15  | [64, 64]            | agent_9            | 0.001             | 37.9%        | -4.295             |


The best agent from this experiment was **agent_12**, featuring **two layers of 64 neurons each and a learning rate of 0.001**, trained against the agent from the first experiment (**agent_0**). **Agent_12** achieved a 47.7% win rate against the default created agent.<br>

The chart below illustrates the training performance of **agent_12**:

![image](https://github.com/user-attachments/assets/598f47d5-e53b-42bc-9e7e-d84dfaa0c1a3)

(X-axis represents the number of episodes)<br>
(Y-axis represents the win ratio in percentages)

Additionally, in this experiment an extra test was conducted: each agent from this experiment was tested against **agent_12** to verify whether it was truly the best agent.
| **Agent 1** | **Agent 2** | **Agent 1 Win Rate** | **Agent 1 Average Reward** |
|:-----------:|:-----------:|:--------------------:|:--------------------------:|
| agent_12    | agent_13    | 55.9%                | 2.719                      |
| agent_12    | agent_14    | 83.9%                | 4.41                       |
| agent_12    | agent_15    | 65.9%                | 6.162                      |


After the additional tests, it was observed that **agent_12** won more than 50% of the games against the other agents, confirming that it was truly the best agent in this experiment.

### 🧪 Fourth Experiment
The fourth experiment introduced **automatic hyperparameter tuning**. The **Optuna** framework was used to identify the **three best neural network architectures**. After selecting the architectures, the new agents were trained against a random agent from the RLCard environment.

A table with the neural network architectures selected by Optuna is shown below:
| **#** | **Neural Network Architecture**       | **Learning Rate**      |
|:-----:|:------------------------------------:|:----------------------:|
| 1     | [357, 357, 357, 357, 357, 357, 357]   | 0.00030632620661205764 |
| 2     | [287, 287, 287, 287, 287, 287, 287]   | 0.006429751557141102   |
| 3     | [411, 411, 411, 411, 411, 411]       | 0.00031761007622629813 |


A table with the results is shown below:
| **Agent**      | **Number of Episodes** | **Win Rate** | **Average Reward** |
|:--------------:|:----------------------:|:------------:|:------------------:|
| agent_optuna_1 | 10,000                 | 38.0%        | -4.482             |
| agent_optuna_2 | 10,000                 | 49.8%        | 0.131              |
| agent_optuna_3 | 10,000                 | 49.8%        | 0.558              |


The best agent from this experiment was **agent_optuna_3**, featuring **six layers of 411 neurons each and a learning rate of 0.00031761007622629813**, achieved a 49.8% win rate against the default created agent. **Agent_optuna_2** achieved the same win rate, but had a lower average reward, which is why **agent_optuna_3** was selected as the best agent in this experiment.<br>

The chart below illustrates the training performance of **agent_optuna_3**:

![image](https://github.com/user-attachments/assets/e025be28-41e1-47fb-b276-9d54b2beee81)

(X-axis represents the number of episodes)<br>
(Y-axis represents the win ratio in percentages)

### 🧪 Fifth Experiment
In the final experiment, **the best agents** from the previous experiments were evaluated against a **DQN agent from the RLCard environment**.<br>

The table presents the best agents:
| **Agent**      | **Neural Network**                        | **Learning Rate**                | **Trained on**  |
|:--------------:|:----------------------------------------:|:--------------------------------:|:---------------:|
| agent_0        | [64, 64]                                 | 0.001                            | random_agent    |
| agent_9        | [256, 256]                               | 0.001                            | random_agent    |
| agent_12       | [64, 64]                                 | 0.001                            | agent_0         |
| agent_optuna_3 | [411, 411, 411, 411, 411, 411]           | 0.00031761007622629813           | random_agent    |


A table with the results is shown below:
| **Agent**      | **Win rate vs DQN RLCard agent** |
|:--------------:|:--------------------------------:|
| agent_0        | 31.7%                            |
| agent_9        | 49.9%                            |
| agent_12       | 28.4%                            |
| agent_optuna_3 | 45.9%                            |


**Two of the best agents** from the previous table were selected for additional performance tests against the **DQN agent from the RLCard environment**. <br>
The table presents their results:

| **DQN RLCard agent vs** | **Test 1** | **Test 2** | **Test 3** |
|:-----------------------:|:----------:|:----------:|:----------:|
| agent_9                 | 49.9%      | 50.0%      | 49.2%      |
| agent_optuna_3          | 50.4%      | 48.69%     | 49.2%      |

## 🎮 Playing Against the Agent – Example Match
Last step of the project was testing the agents in real games, where a human player could compete against a selected agent.

Below is an example of a full game process:
### 1️⃣ ***Pre-flop*** - Players receive their hole cards and can choose one of the available actions, depending on the situation.

<img src="https://github.com/user-attachments/assets/c48b2a41-43c1-4080-80f6-1ea7e4b5d138" width=700>

### 2️⃣ ***Flop*** - Three community cards are dealt on the table, and a new round of betting begins.

<img src="https://github.com/user-attachments/assets/18d11e9c-4645-40e2-870d-d00eed9ddf60" width=700>

### 3️⃣ ***Turn*** - A fourth community card is revealed, followed by another round of betting.

<img src="https://github.com/user-attachments/assets/1a0e836d-03f2-4354-be1b-6f842af6c05b" width=700>

### 4️⃣ ***River*** - The fifth and final community card is dealt, and the last round of betting occurs.

<img src="https://github.com/user-attachments/assets/627f7750-a015-4f87-be82-504f01b19d21" width=700>

### 5️⃣ ***Showdown*** - The remaining players reveal their hole cards, and the winner is determined based on the best five-card poker hand.

<img src="https://github.com/user-attachments/assets/01b8dc33-986c-498a-bd74-2bd3314d4f2b" width=700>

## 💭 Conclusion
The developed **Dueling DQN Agent** achieves performance comparable to the built-in **DQN agent provided by RLCard**.<br>
Furthermore, while **manual hyperparameter tuning** produced results similar to **automatic tuning with Optuna**, it is inherently 
less consistent due to its trial-and-error nature. In contrast, automatic methods like **Optuna** offer a more reliable and 
efficient approach to finding the best performing hyperparameter configurations.

## 📂 Project Structure

📦 Texas-Holdem-Poker-RL-Agent <br>
├── 📄 **README.md** -- *Project documentation <br>*
├── 📊 **Poker_RL_Agent.ipynb** -- *Main notebook <br>*
└── 📂 **Models** -- *Folder with trained models <br>*
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── 📄 **dueling_agent_0_model.pth** -- *Model of trained agent (agent_0) <br>*
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── 📄 **...** -- *Other models of trained agents <br>*
