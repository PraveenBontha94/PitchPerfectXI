# PitchPerfectXI

PitchPerfectXI is a smart cricket team selection system that uses Deep Q-Network (DQN) reinforcement learning to automatically choose the best Playing XI from a user-defined squad based on venue-specific performance data.

## Project Overview

This project aims to automate and optimize the process of cricket team selection using deep reinforcement learning. Given a list of players and a match venue, the system selects the best combination of 11 players based on historical performance, role constraints, and match relevance.

## Features

- Uses Deep Q-Learning to intelligently select a Playing XI
- Considers role constraints: 4 Batsmen, 3 Bowlers, 3 All-Rounders, 1 Wicket-Keeper
- Utilizes venue-specific stats to rank players dynamically
- Includes a reward function that guides the model to learn effective team combinations
- Interactive user input for squad and venue

## Datasets Used

- `batsman_avg_pivot_1.csv` – Venue-wise batting average
- `batsman_sr_pivot_1.csv` – Venue-wise strike rate
- `batsman_matches_pivot_1.csv` – Venue-wise matches played
- `final_del_1.csv` – Historical performance stats

## Reinforcement Learning Setup

### Environment

The environment simulates the process of selecting a cricket team. The agent (model) learns to select players one by one to form an optimal Playing XI.

### State

Each state is a numeric vector composed of:
- 4 role counts: number of Batsmen, Bowlers, AllRounders, and WKs selected so far
- 5 features of the next available player: batting average, strike rate, matches played, wickets, economy

Total state size = 9

### Action

An action is selecting a player (by index) from the available squad.  
Only unselected players are valid actions.

### Reward Function

The reward is calculated after the agent selects 11 players:
- A negative reward is given if the team is incomplete or role constraints are not met
- A positive reward is computed based on:
  - Team batting strength (average + strike rate)
  - Bowling strength (wickets and economy)
  - Venue experience (log-scaled matches played)

This helps the agent learn to form balanced and high-performing teams.

## Technologies Used

- Python  
- TensorFlow / Keras  
- Pandas, NumPy  
- Scikit-learn  
- Reinforcement Learning (DQN)

## Files Included

- `Code.ipynb` – Complete Jupyter Notebook implementation  
- `Report.pdf` – Mid-semester project report  
- `Presentation.pptx` – Project presentation  
- `README.md` – This documentation  
- CSV files – All necessary datasets

## How to Run

1. Clone this repository
2. Ensure you have Python 3.x and required libraries installed
3. Open and run `Code.ipynb` in Jupyter Notebook
4. Input your squad (min 15 players) and desired venue
5. Model will train and return the optimized Playing XI

## Contributors

- B.Praveen
- Mounish Maram
