# swap(指標)

Description

請撰寫一個交換函式(swap)，交換兩個整數值。

此交換函式請使用傳址呼叫（Pass by Reference）的方式來實現數值的交換。

- ------------------------------------------------------------------------------

Please write a swap function that exchanges the values of two integers.

This swap function should implement the exchange of values using pass-by-reference.

Input

輸入兩個整數，直到兩個整數都為0終止程式。

- ------------------------------------------------------------------------------

Input two integers until both integers are 0 to terminate the program.

Output

輸出交換位置後的兩個整數。

- ------------------------------------------------------------------------------

Output the two integers with their positions swapped.

Sample Input 1

```
1 2
3 4
5 6
7 8
9 10
0 0
```

Sample Output 1

```
2 1
4 3
6 5
8 7
10 9
```

```c
#include <stdio.h>

void swap(int* a, int* b)
{
  int tmp = *a;
  *a = *b;
  *b = tmp;
}

int main()
{
  int a, b;
  while (1)
  {
    scanf("%d %d", &a, &b);
    if (a == 0 && b == 0) break;
    swap(&a, &b);
    printf("%d %d\n", a, b);
  }

  return 0;
}
```