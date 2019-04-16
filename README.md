# Cargoes

Consider the following assignment problem, called Cargoes: Let n be a parameter. We are given a n × n grid. Each row and column is labelled with a nonnegative integer, corresponding to the total weight of the corresponding row/column. A solution assigns to every cell a nonnegative integer, its weight, satisfying the following constraints:
1. The sum of the weights for every row equals the corresponding constraint.
2. The sum of the weights for every column equals the corresponding constraint.
3. Let a cargo be a maximal contiguous sequence of nonzero weights in a row or column. Then:
        a) Two cargoes cannot overlap.
        b) Two cargoes cannot touch diagonally.

Your task is to solve a Cargo puzzle with the help of an SMT solver. Write a program that reads the description of a puzzle from standard input (in the format described below), translates the problem above to an instance of SMT, runs Z3 over it, and writes the result to the standard output (in the format described below).

### Input

The first line of the input contains one number: n (the width and height of the square grid). The second line contains `n` integers `a1, ..., an` separated by single spaces, representing the row constraints. The third and last line contains `n` integers `b1, ..., bn` separated by single spaces, representing the column constraints. Rows and columns are described from top to bottom and from left to right.

### Output

If no solution has been found, then the first and only line of the output should be unsolvable. If a solution exists, then the output consists of n lines, representing the rows of some solution. Each line contains `n` integers `c1, ..., cn` separated by single spaces, representing the value of the cell in the corresponding position.

## Example

```bash
$ cat inputs/1                           
8
1 2 5 2 5 2 6 1
3 3 2 2 1 4 5 4

$ cat inputs/1 | ./cargoes 
0 0 1 0 0 0 0 0
1 0 0 0 1 0 0 0
0 0 0 0 0 0 5 0
1 0 1 0 0 0 0 0
1 0 0 0 0 4 0 0
0 0 0 2 0 0 0 0
0 3 0 0 0 0 0 3
0 0 0 0 0 0 0 1
```
