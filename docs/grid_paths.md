# Grid Paths I.

## Feladat specifikáció


**Time limit:** 1.00 s &nbsp;|&nbsp; **Memory limit:** 512 MB

Consider an *n* x *n* grid whose squares may have traps. It is not allowed to move to a square with a trap.

Your task is to calculate the number of paths from the upper-left square to the lower-right square. You can only move right or down.

### Input

The first input line has an integer *n*: the size of the grid.

After this, there are *n* lines that describe the grid. Each line has *n* characters: `.` denotes an empty cell, and `*` denotes a trap.

### Output

Print the number of paths modulo 10^9 + 7.

### Constraints

* 1 <= *n* <= 1000

### Example

**Input:**
4 <br>
.... <br>
.*.. <br>
...* <br>
*... <br>


## Implementáció

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;


public class Main {
    private static final int MOD = 1_000_000_000 + 7;

    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

        String firstLine = reader.readLine();
        int size = Integer.parseInt(firstLine);

        String[][] grid = new String[size][size];
        int[][] dp = new int[size][size];

        for (int i = 0; i < size; i++) {
            grid[i] = reader.readLine().split("");
        }

        if ("*".equals(grid[0][0])) {
            System.out.println(0);
            return;
        }
        dp[0][0] = 1;

        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                if (i == 0 && j == 0) {
                    continue;
                }

                if ("*".equals(grid[i][j])) {
                    dp[i][j] = 0;
                    continue;
                }

                if (i > 0) {
                    dp[i][j] += dp[i-1][j];
                }

                if (j > 0) {
                    dp[i][j] += dp[i][j-1];
                }
                dp[i][j] = dp[i][j] % MOD;
            }
        }

        System.out.println(dp[size-1][size-1]);
    }
}
```

## feltöltés
![feltöltésről készült kép](../site/assets/images/gird_paths_upload.JPG)