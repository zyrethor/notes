# What is the Median?

Description

中位數在統計學中扮演著重要的角色。根據定義，它是將數組分成兩個相等部分的值。

在這個問題中，您需要確定一些長整數的當前中位數。假設我們有五個數字 {1,3,6,2,7}。

在這種情況下，3 是中位數，因為它的兩邊分別有兩個數字。{1,2} 和 {6,7}。

如果值的數量是偶數，如 {1,3,6,2,7,8}，只有一個值無法將這個數組分成兩個相等的部分，所以我們考慮中間值的平均值 {3,6}。

因此，中位數將是 (3+6) / 2 = 4.5。根據這個問題，您只需要打印整數部分，而不是小數部分。

因此，根據這個問題，中位數將是 4！

- **------------------------------------------------------------------------------**

Median plays an important role in the world of statistics. By definition, it is a value which divides an array into two equal parts.

In this problem you are to determine the current median of some long integers. Suppose, we have five numbers {1,3,6,2,7}.

In this case, 3 is the median as it has exactly two numbers on its each side. {1,2} and {6,7}.

If there are even number of values like {1,3,6,2,7,8}, only one value cannot split this array into equal two parts, so we consider the average of the middle values{3,6}.

Thus, the median will be (3+6) / 2 = 4.5.In this problem, you have to print only the integer part, not the fractional.

As a result, according to this problem, the median will be 4 !

Input

輸入文件包含一系列整數 X（0 ≤ X < 2^31），並且整數的總數 N 少於 10000。

輸入以 End of File (EOF) 結束。

- **------------------------------------------------------------------------------**

The input file consists of series of integers X (0 ≤ X < 2^31) and total number of integers N is less than10000.

Inputis terminated byEOF.

Output

對於每個輸入，請打印當前中位數的值。

- **------------------------------------------------------------------------------**

For each input print the current value of the median.

Sample Input 1

```
1
3
4
60
70
50
2
```

Sample Output 1

```
1
2
3
3
4
27
4
```

```c
#include <stdio.h>
#include <stdlib.h>

#define ll long long

int cmp (const void* a, const void* b)
{
  return (*(int*)a - *(int*)b);
}

int main()
{
  int a[1005] = {};
  int n = 0;
  while (scanf("%d", &a[n]) != EOF)
  {
    int len = n+1;
    ll mode = 0;
    qsort(a, len, sizeof(int), cmp);
    if (len % 2 == 1)
      mode = a[len/2];
    else
    {
      ll tmp1 = a[len/2-1];
      ll tmp2 = a[len/2];
      mode = (tmp1 + tmp2) / 2;
      // mode = (a[len/2-1] + a[len/2]) / 2;
    }
    
    printf("%lld\n", mode);
    
    n++;
  }
  
  return 0;
}

```