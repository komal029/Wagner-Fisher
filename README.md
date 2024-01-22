# Wagner-Fisher

The Wagner-Fisher algorithm is commonly used for dynamic programming-based string edit distance computations, such as in spell-checking. It's specifically designed for finding the minimum number of operations (insertions, deletions, or substitutions) needed to transform one string into another.

In the context of spelling check:

1. **Initialization:** Create a matrix where each cell represents the edit distance between substrings of the two words. The top-left cell represents the distance between empty strings, and the bottom-right cell represents the distance between the entire words.

2. **Recurrence Relation:** Fill in the matrix using a recurrence relation. The value in each cell is calculated based on the values in the adjacent cells and the current characters being compared.

3. **Backtracking:** Once the matrix is filled, the minimum edit distance is found. Backtrack through the matrix to identify the specific edit operations that need to be applied to transform one word into the other.

**Mathematics Behind It:**
Let's denote the two words as `A` and `B`. The matrix `D` is used to represent the edit distance between substrings of `A` and `B`, where `D[i][j]` is the edit distance between the first `i` characters of `A` and the first `j` characters of `B`.

The Wagner-Fisher algorithm uses the following recurrence relation:

\[ D[i][j] = \min \left\{
  \begin{array}{ll}
    D[i-1][j] + 1 & \text{(deletion)} \\
    D[i][j-1] + 1 & \text{(insertion)} \\
    D[i-1][j-1] + \text{cost}(A[i], B[j]) & \text{(substitution)}
  \end{array}
\right. \]

The cost function \(\text{cost}(A[i], B[j])\) is 0 if \(A[i] = B[j]\) (no substitution needed) and 1 otherwise.

This recurrence relation is computed for each cell in the matrix, and the minimum edit distance is found in the bottom-right cell. Backtracking through the matrix provides the sequence of edit operations needed for the transformation.
