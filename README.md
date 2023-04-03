# Notebook to create backgammon evaluation data for openai/evals

It turns out gpt3.5 nor gpt4 are particularly good at playing backgammon - well in fact they are terrible. This notebook creates evaluation data using the nice backgammon library from https://github.com/softwerks/backgammon. 

There are basically 2 main questions gpt needs to answer, given a specific backgammon game state and a dice roll:
- can the opponent be hit with the provided dice roll?
- is a the provided play an illegal play?

For both cases, "easy" board states are constructed and eventually converted into a prompt and wrapped as an evaluation compotible with https://github.com/openai/evals.


## can hit?
Example for a board state where the answer to "can backgammonGPT hit" is ```True```.

```
                 Position ID: aOfgBwA2ZvABMA
                 Match ID   : cIgRAAAAAAAA
 +13-14-15-16-17-18------19-20-21-22-23-24-+
 | X           O    |   | O  O  O        X |
 | X           O    |   | O  O           X |
 | X           O    |   | O                |
 | X                |   |                  |
 | X                |   |                  |
v|                  |BAR|                  |
 | 6                |   |                  |
 | O                |   |                  |
 | O                |   |                  |
 | O           X    |   | X        X  X    |
 | O           X    |   | X        X  X    |
 +12-11-10--9--8--7-------6--5--4--3--2--1-+

dice: (3, 4)

these plays hit an opponents checker:
24/21 6/2
24/21 8/4
24/21 13/9
```

## is illegal move?
Example for a board state where the answer to is "24/19 8/5" illegal is also ```True```.

```
                 Position ID: mOfEATDI58EBMA
                 Match ID   : cIgOAAAAAAAA
 +13-14-15-16-17-18------19-20-21-22-23-24-+
 | X     O     O    |   | O     O        X |
 | X           O    |   | O     O        X |
 | X           O    |   | O                |
 |                  |   | O                |
 |                  |   |                  |
v|                  |BAR|                  |
 |                  |   | X                |
 |             X    |   | X                |
 | O           X    |   | X                |
 | O           X    |   | X              O |
 | O           X    |   | X     X        O |
 +12-11-10--9--8--7-------6--5--4--3--2--1-+

dice: (5, 3)

this ia an illegal move:
24/19 8/5
```










