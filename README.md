# Snake game AI with Genetic Algorithm (2020.07.17)
![Best_Genome](./images/snake30_neat_1017_271_p200.gif)

## Input & Output
### Input
<img src="./images/input.png" width="400" height="400"/>

Distances of wall, food, and snake itself for 8 directions (24 inputs)  
& Previous direction of movement (one-hot encoding, 3 inputs)  
→ Total 27 inputs

### Output
Direction of movement (one-hot encoding for turn left, go straight, turn right)  

## Genetic Algorithm
![genetic_algorithm](./images/genetic_algorithm.PNG)

### Selection: Roulette Wheel  
Every Genome can be a parent for next generation, but probability of becoming a parent is proportial to fitness  
Fitness: $ f(s,m) = 2^s + m + 500s^{2.1} - 0.25s^{1.2}m^{1.3} $  
(REF: https://github.com/Chrispresso/SnakeAI)

### Crossover
![image](./images/crossover.PNG)  

### Gaussian Mutation
1. Select weight/bias where the mutation will occurs ($w_i$)  
2. For each weight/bias, pick a random value from normal distribution, multiply scale, and add it to weight/bias  
$ w_i <- w_i + scale \times N(0,1) $

### Result
![genetic_algorithm_gif](./images/snake24_1788_118_p500.gif)
![genetic_algorithm_plot](./images/best_score_ga.PNG)
**Score: 118 (Generation: 1788)**  
> Population: 500  
> Selection: Roulette Wheel  
> Crossover: Simulated Binary Crossover 30% + Single Point Binary Crossover 70%  
> Mutation: Gaussian Mutation 5%  

## NEAT (NeuroEvolution of Augmenting Topologies)  
![image](./images/neat.png)  

### Result
![neat_gif](./images/snake30_neat_1017_271_p200.gif)
![neat_plot](./images/best_score_neat.PNG)

**Score: 271 (Generation: 1017)**  
> Population: 150  
> Initial Connection: unconnected  
> Node add/delete rate: 8.5% / 3.5%  
> Connection add/delete rate: 99% / 15%  
> Weight mutate/replace rate: 45% / 2.5%  
> Bias mutate/replace rate: 5% / 10%  

## vs. Reinforcement Learning  
### Deep Q Network (DQN)  
![dqn_gif](./images/animation_dqn_17163_100.gif)  
**Score: 100**  

### Proximal Policy Optimization (PPO)  
![ppo_gif](./images/animation_ppo_4225_132.gif)  
**Score: 132**  
