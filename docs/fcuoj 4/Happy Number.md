# Happy Number

Description

將一個正整數S0的每個數字的平方和表示為S1。

以類似的方式，將S1的每個數字的平方和表示為S2，依此類推。如果對於某些i ≥ 1，Si = 1，則原始整數S0被稱為快樂數。

一個不是快樂數的數字被稱為不快樂數。

例如，7是一個快樂數，因為7→49→97→130→10→1，而4是一個不快樂數，因為4→16→37→58→89→145→42→20→4。

- ------------------------------------------------------------------------------

Let the sum of the square of the digits of a positive integerS0be represented byS1.

In a similar way, let the sum of the squares of the digits ofS1be represented byS2and so on. If Si= 1for some i ≥ 1, then the original integer S0 is said to be Happy number.

A number, which is not happy, is called Unhappy number.

For example 7 is a Happy number since 7→49→97→130→10→1 and 4 is an Unhappynumber since4→16→37→58→89→145→42→20→4.

Input

輸入由多個測試案例組成，其數量在輸入的第一行給出。

每個測試案例由一行組成，其中包含一個小於10^9的正整數N。

- ------------------------------------------------------------------------------

The input consists of several test cases, the number of which you are given in the first line of the input.

Each test case consists of one line containing a single positive integer N smaller than10^9.

Output

對於每個測試案例，您必須印出以下訊息之一：

Case #p:N is a Happy number.

Case #p:N is an Unhappy number.

- ------------------------------------------------------------------------------

For each test case, you must print one of the following messages:

Case #p:Nis a Happy number.

Case #p:Nis an Unhappy number.

Sample Input 1

```
3
7
4
13

```

Sample Output 1

```
Case #1: 7 is a Happy number.
Case #2: 4 is an Unhappy number.
Case #3: 13 is a Happy number.

```

Sample Input 2

```
4
14
65
68
70

```

Sample Output 2

```
Case #1: 14 is an Unhappy number.
Case #2: 65 is an Unhappy number.
Case #3: 68 is a Happy number.
Case #4: 70 is a Happy number.
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
#include <stdbool.h>

bool ishappy(int n)
{
  int* a = (int*)malloc(sizeof(int) * 1000);
  int len = 0;
  while (1)
  {
    for (int i = 0; i < len; i++)
    {
      if (a[i] == n)
        return false;
    }
    a[len++] = n;
    
    int sum = 0;
    while (n > 0)
    {
      int digit = n % 10;
      sum += digit * digit;
      n /= 10;
    }
    n = sum;
    if (n == 1)
      return true;
  }
}

int main()
{
  int n;
  scanf("%d", &n);
  for (int z = 1; z <= n; z++)
  {
    int t;
    scanf("%d", &t);
    
    printf("Case #%d: ", z);
    if (ishappy(t))
      printf("%d is a Happy number.\n", t);
    else
      printf("%d is an Unhappy number.\n", t);
  }

  return 0;
}

```

Floyd’s Cycle detection algorithm

```c
#include <stdio.h>
#include <stdbool.h>

int sum_squares(int n)
{
  int sum = 0;
  while (n > 0)
  {
    int digit = n % 10;
    sum += digit * digit;
    n /= 10;
  }
  
  return sum;
}

bool ishappy(int n)
{
  int slow = n, fast = n;
  do {
    slow = sum_squares(slow);
    fast = sum_squares((sum_squares(fast)));
  } while (slow != fast);
  
  return slow == 1;
}

int main()
{
  int n;
  scanf("%d", &n);
  for (int z = 1; z <= n; z++)
  {
    int t;
    scanf("%d", &t);
    
    printf("Case #%d: ", z);
    if (ishappy(t))
      printf("%d is a Happy number.\n", t);
    else
      printf("%d is an Unhappy number.\n", t);
  }

  return 0;
}

```