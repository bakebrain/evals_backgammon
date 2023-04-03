# Notebook to create backgammon evaluation data for openai/evals

It turns out gpt3.5 nor gpt4 are particularly good at playing backgammon - well in fact they are terrible. This notebook creates evaluation data using the nice backgammon library from https://github.com/softwerks/backgammon. 

There are basically 2 main questions gpt needs to answer, given a specific backgammon game state and a dice roll:
- can the opponent be hit with the provided dice roll?
- is a the provided play an illegal play?

For both cases, "easy" board states are constructed and eventually converted into a prompt and wrapped as an evaluation compotible with https://github.com/openai/evals.

