# 8 Puzzle Game Solver

This Java code provides an implementation of the classic 8 Puzzle game and a solver using the A* search algorithm to find the optimal solution to the puzzle.

## Board Class

The `Board` class represents the game board and provides methods to create, manipulate, and analyze the puzzle's state.

- `Board(int[][] tiles)`: Constructor to create a new puzzle board.
- `int dimension()`: Returns the board's dimension (n).
- `int hamming()`: Calculates the number of tiles out of place.
- `int manhattan()`: Calculates the sum of Manhattan distances between tiles and the goal state.
- `boolean isGoal()`: Checks if the current board is the goal state.
- `Iterable<Board> neighbors()`: Generates neighboring boards by making legal tile moves.
- `Board twin()`: Returns a board by exchanging any pair of non-blank tiles.

## Solver Class

The `Solver` class utilizes the A* search algorithm to find the optimal solution to the 8 Puzzle game.

- `Solver(Board initial)`: Constructor to initialize the solver with the initial puzzle state.
- `boolean isSolvable()`: Checks if the puzzle is solvable.
- `int moves()`: Returns the minimum number of moves to solve the puzzle.
- `Iterable<Board> solution()`: Returns a sequence of boards in the shortest solution path.

## Running the Solver

You can test the solver by running the `Solver` class. Here's an example of how to create a puzzle and solve it:

```java
public static void main(String[] args) {
    int[][] tiles = { { 0, 1, 3 }, { 4, 2, 5 }, { 7, 8, 6 } };
    Board initialBoard = new Board(tiles);
    Solver solver = new Solver(initialBoard);

    if (solver.isSolvable()) {
        System.out.println("Minimum number of moves: " + solver.moves());
        System.out.println("Solution path:");
        for (Board board : solver.solution()) {
            System.out.println(board);
        }
    } else {
        System.out.println("No solution exists.");
    }
}