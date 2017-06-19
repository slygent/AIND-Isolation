# Heuristic analysis #

## Results ##

Running tournament.py gave the following results:

```
Match #   Opponent    AB_Improved   AB_Custom   AB_Custom_2  AB_Custom_3
                        Won | Lost   Won | Lost   Won | Lost   Won | Lost
    1       Random      10  |   0     9  |   1     7  |   3     7  |   3
    2       MM_Open     10  |   0    10  |   0     9  |   1     9  |   1
    3      MM_Center    10  |   0    10  |   0     9  |   1    10  |   0
    4     MM_Improved    7  |   3    10  |   0     6  |   4     9  |   1
    5       AB_Open      4  |   6     5  |   5     5  |   5     6  |   4
    6      AB_Center     6  |   4     5  |   5     5  |   5     5  |   5
    7     AB_Improved    6  |   4     6  |   4     6  |   4     5  |   5
--------------------------------------------------------------------------
           Win Rate:      75.7%        78.6%        67.1%        72.9%
```

The scores are very similar in performance, with my first custom score slightly winning over the baseline `AB_Improved` scorer, followed by my two other score functions.

## Description of three custom heuristic functions ##

I developed three custom scoring functions, each of which was a linear combination of a subset or all of the following game characteristics:

* Number of possible moves by current player
* Difference in number of possible moves between current player and opposing player
* Distance on board between players
* Distance of current player from the centre of the board

`AB_Custom_3` is the sum of the first two metrics, and therefore in a sense a combination of `AB_Improved` and `AB_Open`. However, it did not perform better than `AB_Improved`. 

`AB_Custom_2` was my attempt to include all four metrics, by simply adding them all up. However, it performed worse than `AB_Custom_3`.

`AB_Custom_1` performed the best, including beating `AB_Improved` 6-4. However, this is probably not a significant margin, i.e. re-running the simulation is likely to lead to a non-victory such as a 5-5 draw. However, it won 78.6% of all matches, more than the other custom scores. This function is double the number of moves available to the current player, plus double the distance from the centre, plus (without doubling) the distance between the players and the difference in the number of moves available to each player.

A development of the scores would try non-linear functions, as well as improving the parameter choices or functional form using something like genetic algorithms.
