# MCTS-in-Python

MCTS-in-Python is a repository that contains simple games with a complex training process. It’s kind of an experiment in “How far can you go with free compute these days?” Well, ~1000 epochs/45m for the AddingGame w/50 simulations per self-play.
It uses a version of a program like AlphaGo Zero, which is a self-learning algorithm that mastered the game of Go. 
The repository currently only includes the following game: an Adding Game: A game where the player has to add numbers to reach a target sum

## Table of Contents

- Preview
- Features
- License
- Contributing
- Acknowledgements

## Preview

To preview the Adding Game, follow these steps:

- Open this Google Colab notebook: https://colab.research.google.com/drive/1jj1-iQItF0umZX3pQsFPavEUzoaRjG0y

## Features

The repository also contains the code for the Monte Carlo Tree Search (MCTS) algorithm, which is a method for finding optimal decisions in complex and uncertain domains. The MCTS algorithm uses a neural network to guide the search and evaluate the game states. The neural network is trained by playing games against itself and learning from the outcomes.

ToDo:
Update the network with states and actions from many games of self-play
```python
# Initialize lists to store states, actions, and rewards from all games
all_states = []
all_actions = []
all_rewards = []

# Training loop
for i in range(epochs):
    # Play a game and get the states, actions, and rewards
    states, actions, reward = mcts.self_play(network, game, game_number)
    
    # Add the states, actions, and rewards to our lists
    all_states.extend(states)
    all_actions.extend(actions)
    all_rewards.extend([reward] * len(states))  # Assume the same reward for all states
    
    # If we've played enough games, train the network
    if (i + 1) % num_games_per_update == 0:
        loss = mcts.train(all_states, all_actions, all_rewards, epochs)
        losses.append(loss)
        
        # Clear our lists for the next batch of games
        all_states = []
        all_actions = []
        all_rewards = []
    
    game_number += 1

    # Step the learning rate scheduler
    scheduler.step()
```
Suggested Improvements:

Use of Residual Networks: AlphaGo Zero uses a residual network (ResNet) for its policy and value networks. You might want to replace PolicyValueNet with a ResNet.
Temperature Parameter: AlphaGo Zero uses a temperature parameter to control the level of exploration during self-play. This could be implemented in the self_play function when choosing the action.
Updating the Network: In AlphaGo Zero, the network is updated with states and actions from many games of self-play, not just one. You might want to modify your training loop to accumulate states, actions, and rewards from multiple games before updating the network.
Simultaneous Self-Play: AlphaGo Zero generates self-play games from multiple instances of the game simultaneously. This could be implemented with multi-threading or distributed computing.
Noise for Exploration: AlphaGo Zero adds Dirichlet noise to the root node to encourage exploration. You could add this in the self_play function.
Window of Past Games: AlphaGo Zero only uses the most recent games for training, discarding older games. You could implement a similar mechanism.

## License
MCTS-in-Python is licensed under the MIT License. See LICENSE for more details.

## Contributing

MCTS in Python welcomes contributions from anyone who wants to improve or enhance the project. To contribute, please follow these steps:

- Fork this repository and create a new branch
- Make your changes and commit them with a descriptive message
- Push your branch to your fork and create a pull request
- Wait for your pull request to be reviewed and merged

Please follow the code of conduct and the style guide when contributing. You can also check the issues page for any open tasks or bugs that you can help with.

Contributing to an open source project is a rewarding and fun way to learn new skills, meet new people, and make a positive impact on the world. By contributing to MCTS in Python, you can help us create better and more enjoyable games and AI for everyone. You can also showcase your creativity and expertise, and get feedback and recognition from other developers. Whether you are a beginner or an expert, there is always something you can do to help. We appreciate your interest and support!

## Acknowledgements
MCTS-in-Python was inspired by or uses the following resources:

-AlphaGo Zero: A paper by DeepMind that describes how they created a self-learning program that mastered the game of Go
-Monte Carlo Tree Search: A Wikipedia page that explains the MCTS algorithm and its applications
-Microsoft Copilot (formerly Bing Chat): An AI companion that helped us write this README and the code

Thank you for your interest in MCTS-in-Python. We hope you enjoy using it or contributing to it. If you have any questions or feedback, please feel free to contact us at emm32449@gmail.com.
