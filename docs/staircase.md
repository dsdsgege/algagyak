# Shortest Path

## Feladat specifikáció
![task kép](./assets/images/staircase_task.png)


## Implementáció

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'staircase' function below.
     *
     * The function accepts INTEGER n as parameter.
     */

    public static void staircase(int n) {
    // Write your code here
        for (int i = n; i > 0; i--) {
            for(int j = i-1; j > 0; j--) {
                System.out.print(" ");
            } 
            int k = i;
            while (k++ <= n) {
                System.out.print("#");
            }
            System.out.println();
        }
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        Result.staircase(n);

        bufferedReader.close();
    }
}
```

## Feltöltés
![feltöltésről készült kép](./assets/images/staircase_upload.png)