# Monkbananas solution

## Running the code online IDE
https://onecompiler.com/java/3ydebnpw8

## Java Code
``` java
import static java.lang.Math.max;
import static java.lang.Math.min;

public class Main {
    public static void main(String[] args) {
    int[][] mat = {
        {1, 3, 3},
        {2, 1, 4},
        {0, 6, 4}
    };
    assert maxForwardPathSum(mat) == 13;

    int[][] mat2 = {
        {1, 3, 1, 5},
        {2, 2, 4, 1},
        {5, 0, 2, 3},
        {0, 6, 1, 2}
    };
    assert maxForwardPathSum(mat2) == 16;

    int[][] mat3 = {
        {10, 33, 13, 15},
        {22, 21, 4, 1},
        {5, 0, 2, 3},
        {0, 6, 14, 2}
    };
    assert maxForwardPathSum(mat3) == 83;
  }
  
  /*
  Time Complexity: O(N*N)
  Space Complexity: O(N*M)
  */
  public static int maxForwardPathSum(int[][] mat) {
    int n = mat.length;
    int m = mat[0].length;
    int maxSum = Integer.MIN_VALUE;
    for (int c = 1; c < m; c++)
      for (int r = 0; r < n; r++) {
        mat[r][c] += max(mat[r][c - 1],
            max(mat[max(0, r - 1)][c - 1],
                mat[min(n - 1, r + 1)][c - 1]));
        maxSum = max(mat[r][c], maxSum);
      }
    return maxSum;
  }
```
