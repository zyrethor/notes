# GCD

Description

Given the value of N, you will have to find the value of G. The definition of G is given below:

![https://oj.fcu.edu.tw/public/upload/833d3daa26.png](https://oj.fcu.edu.tw/public/upload/833d3daa26.png)

Here GCD(i, j)means the greatest common divisor of integeriand integerj.

For those who have trouble understanding summation notation, the meaning ofGis given in the

following code:

![https://oj.fcu.edu.tw/public/upload/c82b9c8e8c.png](https://oj.fcu.edu.tw/public/upload/c82b9c8e8c.png)

Input

輸入文件最多包含 100 行輸入。每行包含一個整數N(1 < N < 501)。

N的含義在問題描述中給出。輸入以包含單個零的行終止。

這個零不應該被處理。

- ------------------------------------------------------------------------------

The input file contains at most 100 lines of inputs. Each line contains an integer N(1< N <501).

The meaning of N is given in the problem statement. Input is terminated by a line containing a singlezero.

This zero should not be processed.

Output

對於每一行輸入，產生一行輸出。該行包含對應N的G值。

- ------------------------------------------------------------------------------

For each line of input produce one line of output. This line contains the value of G for correspondingN.

Sample Input 1

```
10
100
500
0

```

Sample Output 1

```
67
13015
442011

```

Sample Input 2

```
2
3
4
5
6
7
8
0

```

Sample Output 2

```
1
3
7
11
20
26
38
```

Euclidean algorithm

```c
#include <stdio.h>

int gcd(int a, int b)
{
  int tmp;
  while (b != 0)
  {
    tmp = b;
    b = a % b;
    a = tmp;
  }
  
  return a;
}

int main()
{
  while (1)
  {
    int n;
    scanf("%d", &n);
    if (n == 0) break;
    
    int g = 0;
    for (int i = 1; i < n; i++)
    {
      for (int j = i+1; j <= n; j++)
      {
        g += gcd(i, j);
      }
    }
    
    printf("%d\n", g);
  }

  return 0;
}

```