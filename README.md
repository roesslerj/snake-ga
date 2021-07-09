# Deep Reinforcement Learning Project: Train AI to play Snake

This is a fork of [this project from maurock](https://github.com/maurock/snake-ga), so we have a working starting-point.

## Introduction

The original project had several drawbacks, that we wanted to improve on:

- It stores and manages the board in the actual pixel size, instead of having a logical board that gets transformed only for rendering.
- It gives only a feature vector of 8 features to the DNN, which already encodes a lot of information about the rules and goals of the game.
- The way the reinforcement is implemented already implicitly encodes some of the rules and goals of the game.

## Run
To run and show the game, executes in the snake-ga folder:

```python
python snakeClass.py
```
Arguments description:

- --display - Type bool, default True, display or not game view
- --speed - Type integer, default 50, game speed

The default configuration loads the file *weights/weights.h5* and runs a test.

To train the agent, set in the file snakeClass.py:
- `params['train'] = True`
The parameters of the Deep neural network can be changed in *snakeClass.py* by modifying the dictionary `params` in the function `define_parameters()`

If you run snakeClass.py from the command line, you can set the arguments `--display=False` and `--speed=0`. This way, the game display is not shown and the training phase is faster.

## Optimize Deep RL with Bayesian Optimization
To optimize the Deep neural network and additional parameters, run:

```python
python snakeClass.py --bayesianopt=True
```

This method uses Bayesian optimization to optimize some parameters of Deep RL. The parameters and the features' search space can be modified in *bayesOpt.py* by editing the `optim_params` dictionary in `optimize_RL`.

## For Mac users
It seems there is a OSX specific problem, since many users cannot see the game running.
To fix this problem, in update_screen(), add this line.

```                              
def update_screen():
    pygame.display.update() <br>
    pygame.event.get() # <--- Add this line ###
```
## License

Unfortunately, the upstream project didn't specify a license, so we can't either.

