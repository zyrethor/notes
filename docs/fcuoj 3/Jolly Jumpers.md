# Jolly Jumpers

Description

一個由 n > 0 個整數組成的序列被稱為歡樂跳躍者，如果連續元素之間的差的絕對值可以取遍 1 到 n−1 的所有值。例如，

1 4 2 3

是一個歡樂跳躍者，因為差的絕對值分別是 3、2 和 1。這個定義意味著任何只包含單一整數的序列都是歡樂跳躍者。你需要寫一個程序來判斷一系列的序列是否為歡樂跳躍者。

- ------------------------------------------------------------------------------

A sequence of n >0 integers is called a jolly jumper if the absolute values of the difference between successive elements take on all the values 1 throughn−1. For instance,

1 4 2 3

is a jolly jumper, because the absolutes differences are 3, 2, and 1 respectively. The definition implies that any sequence of a single integer is a jolly jumper. You are to write a program to determine whether or not each of a number of sequences is a jolly jumper.

Input

每一行輸入包含一個整數 n ≤ 3000，後面跟著 n 個整數代表序列。

- ------------------------------------------------------------------------------

Each line of input contains an integer n ≤ 3000 followed by n integers representing the sequence.

Output

對於每一行輸入，生成一行輸出，表示為「Jolly」或「Not jolly」。

- ------------------------------------------------------------------------------

For each line of input, generate a line of output saying `Jolly' or `Not jolly'.

Sample Input 1

```
4 1 4 2 3
5 1 4 2 -1 6
```

Sample Output 1

```
Jolly
Not jolly
```

Sample Input 2

```
1 1
2 1 2
2 1 3
3 2 1 3
```

Sample Output 2

```
Jolly
Jolly
Not jolly
Jolly
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

void bubble(int a[], int n)
{
  for (int i = 0; i < n; i++)
  {
    for (int j = 0; j < n-1-i; j++)
    {
      if (a[j] > a[j+1])
      {
        int tmp = a[j];
        a[j] = a[j+1];
        a[j+1] = tmp;
      }
    }
  }
}

int main()
{
  int a[3005] = {};
  int b[3005] = {};
  int n;
  while (scanf("%d", &n) != EOF)
  {
    for (int i = 0; i < n; i++)
      scanf("%d", &a[i]);
    
    for (int i = 0; i < n-1; i++)
      b[i] = abs(a[i] - a[i+1]);
    
    bubble(b, n-1);
    bool flag = true;
    for (int i = 0; i < n-1; i++)
    {
      if (b[i] != i+1)
      {
        flag = false;
        break;
      }
    }
    
    if (flag)
      printf("Jolly\n");
    else
      printf("Not jolly\n");
  }

  return 0;
}
```