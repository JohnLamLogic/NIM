# Nim Player

An optimal AI agent for the mathematical strategy Game of Nim, built using the Minimax algorithm to play a perfect, unbeatable game.

> An example of the AI making a move in a game of Nim.

---

## Overview

This project explores game theory and adversarial search by creating an AI that can play the Game of Nim perfectly. Nim is a mathematical game of strategy in which two players take turns removing objects from distinct heaps or piles. The program implements the Minimax algorithm, allowing the AI to evaluate all possible future moves and choose the one that guarantees a win if a winning path exists.

---

## Features

- **Minimax Algorithm**: Implements the Minimax algorithm to determine the optimal move in a two-player, zero-sum game. The AI scores each potential move by assuming the opponent will also play optimally.

- **Adversarial Search**: The AI searches the game tree to maximize its own score while anticipating that its opponent is actively trying to minimize it, allowing it to play a perfect game.

- **Game Modes**: Supports both Human vs. AI and AI vs. AI modes for testing and demonstration.

- **Dynamic Move Generation**: Includes a function that generates all possible legal moves from any given game state for the AI to evaluate.

---

## How It Works

The core of the AI is the `min_max_thing` function, which implements the Minimax algorithm.

### Recursive Evaluation

The function recursively explores the game tree from the current state. For each move, it calls itself to evaluate the state that would result, switching the perspective between the maximizing and minimizing player.

### Terminal State Scoring

The recursion's base case is a game-over state (no piles left). The state is scored as +1 for a win and -1 for a loss from the current player's perspective.

### Optimal Move Selection

As the recursion unwinds, it propagates the scores back up the tree. The AI chooses the move that leads to the branch with the highest possible score for itself, assuming the opponent will always choose the move with the lowest score for the AI.

---

## Code Snippet: The Minimax Function

This function recursively explores game moves, returning the best possible score and corresponding move from the current player's perspective.

```python
def min_max_thing(piles, perspective, current, other):
    if game_over(piles):
        return eval_term(perspective, current), None

    best_max, best_min = -2, 2
    best_max_move = best_min_move = None

    for m in gen_moves(piles):
        nxt = apply_move(piles, m)
        score, _ = min_max_thing(nxt, perspective, other, current)
        # ... logic to find best max and min scores/moves ...

    if current == perspective:
        return best_max, best_max_move
    else:
        return best_min, best_min_move
```

---

## Technologies Used

- **Language**: Python
- **Core Concepts**: Minimax Algorithm, Game Theory, Adversarial Search, Recursion, Game Trees

---

## Getting Started

### Run the script from your terminal:

```bash
python nim_player.py
```

### Enter the number of piles for the game.

### Choose the game mode:

- `H` for Human vs. AI
- `A` for AI vs. AI


