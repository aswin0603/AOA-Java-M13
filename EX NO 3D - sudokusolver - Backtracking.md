
# EX 3D Sudoku solver - Backtracking.
## DATE: 04-10-2025
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:

<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1. Read the 9×9 board input, where 0 indicates an empty cell.
2. Find the next empty cell and try placing numbers 1 to 9 in it.
3. For each number, check if placing it is valid in the current row, column, and 3×3 subgrid.
4. If valid, place the number and recursively attempt to solve the remaining board; if it fails, undo and try the next number.
5. If all cells are filled without conflict, the Sudoku is solved; otherwise, report no solution.   

## Program:
```java
import java.util.Scanner;

public class SudokuSolver {
    static boolean isSafe(int[][] board, int row, int col, int num) {
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    static boolean solveSudoku(int[][] board, int row, int col) {
        for (int i = row; i < 9; i++) {
            for (int j = (i == row ? col : 0); j < 9; j++) {

                if (board[i][j] == 0) {
                    for (int num = 1; num <= 9; num++) {
                        if (isSafe(board, i, j, num)) {
                            board[i][j] = num;
                            if (solveSudoku(board, i, j))
                                return true;
                            board[i][j] = 0;
                        }
                    }
                    return false;
                }
            }
        }
        return true;
    }

    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

      //  System.out.println("Enter the Sudoku puzzle row by row (use 0 for empty cells):");

        for (int i = 0; i < 9; i++) {
            //System.out.print("Enter row " + (i + 1) + ": ");
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}

```

## Output:
<img width="640" height="546" alt="image" src="https://github.com/user-attachments/assets/e5fddb10-d453-451b-9135-3fcd7aed8087" />



## Result:
The program successfully implemented and the expected output is verified.

```
Developed by: ASWIN B
Register Number:  212224110007
```
