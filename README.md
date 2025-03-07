# 🃏 Texas Hold'em Poker RL Agent 

A Reinforcement Learning agent for Texas Hold'em Poker, using the RLCard environment for agent evaluation. 
The project focuses on developing the **Reinforcement Learning** agent using the **Dueling Deep Q-Network** algorithm variant and 
examining the impact of neural network hyperparameter tuning on model performance, with both manual hyperparameter tuning and automatic tuning using Optuna.

## 📚 About This Project
This project was developed as part of my Engineering thesis in Computer Science. The goal was to build a **Reinforcement Learning** agent for Texas Hold'em Poker and explore the impact of neural network hyperparameter tuning on model performance.

## 🧰 Development Tools
- Python 3.12.2
- [PyTorch](https://pytorch.org)
- [RLCard](https://rlcard.org/index.html) (for Poker simulation)
- [Optuna](https://optuna.org) (for hyperparameter tuning)
- [Google Colab](https://colab.research.google.com) (Jupyter Notebook)

## 📊 Results

### Example performance chart of the agent:

![Training Performance](https://github.com/user-attachments/assets/93972d74-5061-4c7e-b71a-6c746bb8ed33)
The chart shows the training performance of the default agent of created algorithm. <br>
(X-axis represents the number of episodes)
(Y-axis represents the win ratio in percentages)

### Results of experiments:

The best agent from each stage of the experiments was selected to test its performance against the built-in DQN agent from the RLCard environment. <br>
The table presents the best agents:

<table>
  <tr>
    <td>
      <b>Agent</b>
    </td>
    <td>
      <b>Neural Network</b>
    </td>
    <td>
      <b>Learning Rate</b>
    </td>
    <td>
      <b>Trained on</b>
    </td>
  </tr>
  <tr>
    <td>
      agent_0
    </td>
    <td>
      [64, 64]
    </td>
    <td>
      0.001
    </td>
    <td>
      random_agent
    </td>
  </tr>
  <tr>
    <td>
      agent_9
    </td>
    <td>
      [256, 256]
    </td>
    <td>
      0.001
    </td>
    <td>
      random_agent
    </td>
  </tr>
  <tr>
    <td>
      agent_12
    </td>
    <td>
      [64, 64]
    </td>
    <td>
      0.001
    </td>
    <td>
      agent_0
    </td>
  </tr>
  <tr>
    <td>
      agent_optuna_3
    </td>
    <td>
      [411, 411, 411, 411, 411, 411]
    </td>
    <td>
      0.00031761007622629813
    </td>
    <td>
      random_agent
    </td>
  </tr>
</table>

Two of the best agents from the previous table were selected for additional performance tests against the DQN agent from the RLCard environment. <br>
The table presents their results:

<table>
  <tr>
    <td>
      <b>DQN RLCard agent vs</b>
    </td>
    <td>
      <b>Test 1</b>
    </td>
    <td>
      <b>Test 2</b>
    </td>
    <td>
      <b>Test 3</b>
    </td>
  </tr>
  <tr>
    <td>
      agent_9
    </td>
    <td>
      49.9%
    </td>
    <td>
      50.0%
    </td>
    <td>
      49.2%
    </td>
  </tr>
  <tr>
    <td>
      agent_optuna_3
    </td>
    <td>
      50.4%
    </td>
    <td>
      48.69%
    </td>
    <td>
      49.2%
    </td>
  </tr>
</table>

### Conclusion
The results indicate that the developed **Dueling DQN Agent** achieves
performance comparable to the built-in DQN agent in RLCard.

## 📂 Project Structure

📦 Texas-Holdem-Poker-RL-Agent <br>
├── 📄 **README.md** -- *Project documentation <br>*
├── 📊 **Poker_RL_Agent.ipynb** -- *Main notebook <br>*
└── 📂 **Models** -- *Folder with trained models <br>*
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── 📄 **dueling_agent_0_model.pth** -- *Model of trained agent (agent_0) <br>*
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── 📄 **...** -- *Other models of trained agents <br>*
