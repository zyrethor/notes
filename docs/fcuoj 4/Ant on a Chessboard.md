# Ant on a Chessboard

Description

有一天，一隻名叫愛麗絲的螞蟻來到了一個 M*M 的棋盤上。她想要走遍所有的格子。

於是她按照這樣的方式開始走遍棋盤：（你可以假設她的速度是每秒一格）

在第一秒，愛麗絲站在（1,1）處。她首先向上走了一格，然後向右走了一格，再向下走了一格。

之後，她向右走了一格，然後向上走了兩格，再向左走了兩格，就像一條蛇一樣。

例如，她的前 25 秒走法是這樣的：

（格子中的數字表示她進入該格的時間）

![https://oj.fcu.edu.tw/public/upload/f3b0fe6957.png](https://oj.fcu.edu.tw/public/upload/f3b0fe6957.png)

在第 8 秒時，她在（2,3）處，而在第 20 秒時，她在（5,4）處。

你的任務是確定在給定的時間她身在何處（你可以假設 M 足夠大）。

- ------------------------------------------------------------------------------

One day, an ant called Alice came to an M*M chessboard. She wanted to go around all the grids.

Soshe began to walk along the chessboard according to this way: (you can assume that her speed is onegrid per second)

At the first second, Alice was standing at (1,1). Firstly she went up for a grid, then a grid to theright, a grid downward.

After that, she went a grid to the right, then two grids upward, and then twogrids to the left¡in a word, the path was like a snake.

For example, her first 25 seconds went like this:

( the numbers in the grids stands for the time when she went into the grids)

![https://oj.fcu.edu.tw/public/upload/f3b0fe6957.png](https://oj.fcu.edu.tw/public/upload/f3b0fe6957.png)

At the 8-th second , she was at (2,3), and at 20-th second, she was at (5,4).

Your task is to decide where she was at a given time (you can assume thatMis large enough).

Input

輸入文件將包含多行，每行包含一個數字 N（1 ≤ N ≤ 2∗10^9），代表時間。

文件將以一行包含數字「0」的行結束。

- ------------------------------------------------------------------------------

Input file will contain several lines, and each line contains a numberN(1 ≤ N ≤ 2∗109), which standsfor the time.

The file will be ended with a line that contains a number ‘0’.

Output

對於每個輸入情況，你應該打印一行包含兩個數字（x, y），即列和行號碼，它們之間只能有一個空格。

- ------------------------------------------------------------------------------

For each input situation you should print a line with two numbers (x, y), the column and the rownumber, there must be only a space between them.

Sample Input 1

```
8
20
25
0

```

Sample Output 1

```
2 3
5 4
1 5

```

Sample Input 2

```
17
50
89
128
0

```

Sample Output 2

```
5 1
1 8
8 10
7 12
```

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int findSquare(int n)
{
  int k = 1;
  while (n > 0)
  {
    if ((n - k*k <= 0))
      return k-1;
    k++;
  }
}

int main()
{
  int n, a, b;
  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    
    int sq = findSquare(n);
    int idx = n - sq * sq;
    if (sq % 2 == 0)
    {
      if (idx <= sq + 1)
      {
        a = sq + 1;
        b = idx;
      }
      else
      {
        a = 2 * (sq + 1) - idx;
        b = sq + 1;
      }
    }
    else
    {
      if (idx <= sq + 1)
      {
        a = idx;
        b = sq + 1;
      }
      else
      {
        a = sq + 1;
        b = 2 * (sq + 1) - idx;
      }
    }
    printf("%d %d\n", a, b);
  }
  
  return 0;
}

```