# DPA Numbers I

Description

在數論中，一個正整數僅屬於以下類別之一：Deficient(不足), Perfect(完美) or Abundant(充足)（DPA）。

要確定正整數 n 的類別，首先您必須計算其所有真正的正因子的和。

如果結果小於 n，則 n 是一個不足數；

如果結果等於 n，則 n 是一個完美數；

如果結果大於 n，則 n 是一個充足數。

請記住，n 的真正的因子不包括 n 本身。

例如，數字 8 的真正因子是 1、2 和 4，它們的和為 7。因為 7 < 8，所以 8 是一個不足數。

數字 6 的真正因子是 1、2 和 3，它們的和為 6。因為 6 = 6，所以 6 是一個完美數。

數字 18 的真正因子是 1、2、3、6 和 9，它們的和為 21。因為 21 > 18，所以 18 是一個充足數。

任務是選擇正整數 n 的類別，作為一個不足、完美或充足數。

- ------------------------------------------------------------------------------

In number theory, a positive integer belongs to one and only one of the following categories: Deficient, Perfect or Abundant (DPA).

To decide the category of a positive integer n, first you have to calculate the sum of all its proper positive divisors.

If the result is less than n then n is a deficient number, if the result is equal to n then n is a perfect number and if the result is greater than n then n is an abundant number.

Remember that the proper divisors of n don’t include n itself.

For example, the proper divisors of the number 8 are 1, 2 and 4 which sum 7. Since 7 < 8 therefore8 is a deficient number.

The proper divisors of the number 6 are 1, 2 and 3 which sum 6. Since 6 = 6 therefore 6 is a perfect number.

The proper divisors of the number 18 are 1, 2, 3, 6 and 9 which sum21. Since 21 > 18 therefore 18 is an abundant number.

The task is to choose the category of a positive integer n as a deficient, perfect or abundant number.

Input

輸入以一個整數 t（1 ≤ t ≤ 500）開始，表示測試案例的數量，然後是 t 行，每行包含一個整數 n（2 ≤ n ≤ 10^3）。

- ------------------------------------------------------------------------------

Input begins with an integer t (1 ≤ t ≤ 500), the number of test cases, followed by t lines, each line containing an integer n (2 ≤ n ≤10^3).

Output

對於每個測試案例，您應該印出一行，其中包含單字‘deficient’、‘perfect’ 或 ‘abundant’，表示數字 n 的類別。

- ------------------------------------------------------------------------------

For each test case, you should print a single line containing the word ‘deficient’, ‘perfect’ or ‘abundant’ that representing the category of the number n.

Sample Input 1

```
10
5
6
16
18
21
28
29
30
40
43
```

Sample Output 1

```
deficient
perfect
deficient
abundant
deficient
perfect
deficient
abundant
abundant
deficient
```

```c
#include <stdio.h>
#include <stdlib.h>

int sum_factor(int *a)
{
  int sum = 0;
  int *psum = &sum;
  
  for (int i = 1; i < *a; i++)
  {
    if (*a % i == 0)
      *psum += i;
  }
  
  return *psum;
}

int main()
{
  int n;
  int *pn = &n;
  scanf("%d", pn);
  for (int i = 0; i < *pn; i++)
  {
    int a;
    int *pa = &a;
    scanf("%d", pa);
    
    if (sum_factor(pa) < *pa)
      printf("deficient\n");
    else if (sum_factor(pa) > *pa)
      printf("abundant\n");
    else
      printf("perfect\n");
  }
  
  
  return 0;
}

```