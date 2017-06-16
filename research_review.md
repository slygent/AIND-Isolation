# Research Review of "Mastering the game of Go with deep neural networks and tree search" by Silver et al #

## Summary of the paper's goals and techniques ##

Silver et al describes a new AI Go player called AlphaGo. Because the branching factor is approximately 250, and depth of the game approximately 150, exhaustive search of the game tree from almost any game position is completely infeasible. The search space, as usual in this field, is reduced by a) the use of a value function which estimates the quality of a game position; and b) sampling intelligently from the game tree of any position by exploring moves that are more probable to be fruitful in achieving victory. 

The state of the art at the publication of this paper was Monte Carlo tree search (MCTS), which samples intelligently from the game tree, but was hobbled by having overly simplistic models for both the value function and sampling probability distribution.

Silver et al instead use deep convolutional neural networks to estimate the value function and the sampling probability distributions for each game position. This is done by first using previously-played expert games to estimate probabilities of which actions to take at various positions. This is then improved using gradient learning from playing games against itself, which leads to an estimated value function based on outcomes during self-play.

## Summary of the paper's results ##

AlphaGo was pitted against other Go-playing programs such as Crazy Stone, Fuego, and GNU Go. It won 494 out of 495 games. With a four-stone handicap, AlphaGo's worst performance was a 77% win rate against Crazy Stone. It was also shown that a distributed version of AlphaGo, allowing access to much more computing power, beat a single-machine version of AlphaGo 77% of the time. Additionally, the best version of AlphaGo was the one that used both the value function and searching the game tree intelligently.

Finally, AlphaGo won 5-0 against the 2-dan Fan Hui, who was the European Go champion in 2013, 2014 and 2015.
