# Parity

Description

我們定義一個整數 n 的奇偶性為其二進制表示中位元的總和模 2 的計算結果。

例如，數字 21 = 10101₂ 在其二進制表示中有三個 1，所以它的奇偶性為 3 (mod 2)，即 1。

在這個問題中，你需要計算一個整數 1 ≤ n ≤ 2147483647 的奇偶性。

- ------------------------------------------------------------------------------

We define the parity of an integer n as the sum of the bits in binary representation computed modulotwo.

As an example, the number 21 =10101₂has three 1s in its binary representation so it has parity3(mod2), or 1.

In this problem you have to calculate the parity of an integer1 ≤ I ≤ 2147483647.

Input

輸入的每一行都有一個整數 I，輸入的結束由 I=0 的一行表示，該行不應被處理。

- ------------------------------------------------------------------------------

Each line of the input has an integer Iand the end of the input is indicated by a line where I=0 thatshould not be processed.

Output

對於輸入中的每個整數 I，應該輸出一行‘The parity of B is P(mod 2).’，其中 B 是 I 的二進制表示。

- ------------------------------------------------------------------------------

For each integer I in the input t you should print a line ‘The parity of B is P(mod 2).’, where Bis the binary representation of I.

Sample Input 1

```
1
2
10
21
0

```

Sample Output 1

```
The parity of 1 is 1 (mod 2).
The parity of 10 is 1 (mod 2).
The parity of 1010 is 2 (mod 2).
The parity of 10101 is 3 (mod 2).

```

Sample Input 2

```
3
4
5
6
16
0

```

Sample Output 2

```
The parity of 11 is 2 (mod 2).
The parity of 100 is 1 (mod 2).
The parity of 101 is 2 (mod 2).
The parity of 110 is 2 (mod 2).
The parity of 10000 is 1 (mod 2).
```

```c
#include <stdio.h>

int main()
{
  int n;
  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    
    int a[50] = {};
    int cnt = 0;
    int mod_cnt = 0;
    while (n > 0)
    {
      if (n % 2 == 1) mod_cnt++;
      a[cnt++] = '0' + n % 2;
      n /= 2;
    }
    
    printf("The parity of ");
    for (int i = cnt-1; i >= 0; i--)
      printf("%c", a[i]);
    printf(" is %d (mod 2).\n", mod_cnt);
  }
  
  return 0;
}

```