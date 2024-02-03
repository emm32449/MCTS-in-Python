# MCTS-in-Python
A Version of a Program Like Alpha Go Zero

ToDo:
Use of Residual Networks: AlphaGo Zero uses a residual network (ResNet) for its policy and value networks. You might want to replace PolicyValueNet with a ResNet.

Temperature Parameter: AlphaGo Zero uses a temperature parameter to control the level of exploration during self-play. This could be implemented in the self_play function when choosing the action.

Updating the Network: In AlphaGo Zero, the network is updated with states and actions from many games of self-play, not just one. You might want to modify your training loop to accumulate states, actions, and rewards from multiple games before updating the network.

Simultaneous Self-Play: AlphaGo Zero generates self-play games from multiple instances of the game simultaneously. This could be implemented with multi-threading or distributed computing.

Noise for Exploration: AlphaGo Zero adds Dirichlet noise to the root node to encourage exploration. You could add this in the self_play function.

Window of Past Games: AlphaGo Zero only uses the most recent games for training, discarding older games. You could implement a similar mechanism.
