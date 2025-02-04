# Ultimate Tic-Tac-Toe Agent

## What is Ultimate Tic-Tac-Toe?

Ultimate Tic-Tac-Toe is an advanced version of the classic Tic-Tac-Toe game, adding layers of strategy and complexity. Instead of a single 3x3 grid, the game board consists of **nine 3x3 Tic-Tac-Toe grids**, making a **supergrid** of 81 cells in total.

## How It Works

- Each small 3x3 grid is called a **block**, and the entire 9-block grid is called the **board**.
- Players take turns placing **X** or **O** in the cells.
- The first move can be made in any of the 81 cells.
- After the first move, the opponent’s move determines **which block** the next player must play in.
- If a block is already won or full, the player can move freely to any unoccupied cell in an **unfinished block**.

## Winning Conditions

- A player wins a **block** by forming a standard Tic-Tac-Toe winning pattern (row, column, or diagonal).
- The game is won by the first player to **win three blocks in a row**, forming a winning pattern in the supergrid.

## Why Play Ultimate Tic-Tac-Toe?

- **More Strategy:** Unlike classic Tic-Tac-Toe, where the best strategy often leads to a draw, Ultimate Tic-Tac-Toe requires deeper planning and adaptability.
- **Dynamic Gameplay:** Every move affects not just a single block but the entire board, making the game unpredictable and engaging.
- **Competitive and Fun:** The game is popular for AI competitions, tournaments, and casual play among friends.


## Rules

1. **[FIRST MOVE]** The first move can be made in any of the 81 cells.
2. **[OTHER MOVES]** If the opponent plays in a cell with index *k*, the player must move in the block with index *k*, placing the mark in an empty cell within that block.
3. **[FREE MOVE]** If the designated block (according to Rule 2) is full (no empty cells) or has already been won (according to Rule 4), the player may move to any empty cell on the board that is not inside a won block.
4. **[BLOCK WINNING RULE]** A player who forms a winning pattern within a block is considered to have won that block.
5. **[GAME WINNING RULE]** A player wins the game by forming a winning pattern using the blocks they have won.

## Requirements

Implement the function:  `def select_move(cur_state, remain_time)`

- **Input: `cur_state`**, which contains:
  - `global_cells`: An array of 9 elements representing the status of each block.
  - `blocks`: A 3x3 matrix array representing the individual cell states within each block.
  - `player_to_move`: The current player (1 for 'X', -1 for 'O').
  - `previous_move`: The last move made by the opponent.
- **Input: `remain_time`**, the remaining time for move calculation.
- **Output: `move`**, the chosen move:
  - `None`: If no valid move is available.
  - `move`: An `UltimateTTT_Move` object, containing:
    - `index_local_board`: The selected block index.
    - `x, y`: The chosen cell's coordinates in the block.
    - `value`: 1 (X) or -1 (O).

## Evaluation

The assignment is graded in two parts:

### **Part 1 (60% of total score)** - Competing against a random-move agent (10 games, 5 starting first):
- **Win:** 3 points.
- **Draw:**
  - If the player controls more blocks than the opponent: 2 points.
  - Otherwise: 1 point.
- **Loss:** 0 points.

> *Note: If the program plays randomly like the provided source, it will receive a score of 0 for this section.*

### **Part 2** - Tournament against other teams.

## Time Constraints

Each player has the following time limits per game:
- **Each move:** Must not exceed 10 seconds.
- **Total game time:** Must not exceed 120 seconds.

> *Violation of these limits results in an automatic loss.*

## Tournament

### **[ROUND 1]**  
Teams are randomly divided into groups of 8-10. Matches are round-robin style. A coin toss decides which team moves first (or teams may agree to play two rounds, alternating who moves first). Points are calculated as in Part 1.  
Group standings determine whether teams advance to the next round and contribute to Part 2's final score.

- **1st place:** Advances to Round 2, earns 4 points.
- **2nd place:** Advances to Round 2, earns 3 points.
- **3rd place:** Eliminated, earns 2 points.
- **4th place:** Eliminated, earns 1 point.
- **Lower ranks:** Eliminated, earns 0 points.

### **[ROUND 2]**  
Teams are re-divided into 4 groups. Matches are played round-robin as in Round 1.

- **1st place:** Advances to Quarter-finals, earns 7 points.
- **2nd place:** Advances to Quarter-finals, earns 6 points.
- **3rd place:** Eliminated, earns 5 points.
- **Lower ranks:** Eliminated, keeps points from Part 1.

### **[QUARTER-FINALS]**  
8 teams are matched into 4 pairs in a knockout format. Each match consists of two games (each team goes first once). Points are awarded as in Part 1. The team with more points advances. If tied, a coin toss determines the winner.

- **Winner:** Advances to Semi-finals, earns 8 points.
- **Loser:** Eliminated, keeps points from Round 2.

### **[SEMI-FINALS]**  
4 teams compete in 2 knockout matches, same format as Quarter-finals.

- **Winner:** Advances to Finals, earns 9 points.
- **Loser:** Eliminated, earns 8 points.

### **[FINALS]**  
The two finalists play a match similar to the Semi-finals.

- **Winner:** 10 points.
- **Loser:** 9 points.

> **Note:** Teams that withdraw from matches will:
> - Be placed last in their group during Rounds 1 & 2.
> - Be considered to have lost in later rounds.
