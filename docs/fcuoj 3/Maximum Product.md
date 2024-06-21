# Maximum Product

Description

給定一個整數序列 S = {S1, S2, . . . , Sn}，您應該確定涉及 S 連續項的最大正乘積的值。

如果找不到正的序列，您應該將最大乘積的值視為0。

- ------------------------------------------------------------------------------

Given a sequence of integers S = {S1, S2, . . . , Sn}, you should determine what is the value of themaximum positive product involving consecutive terms of S.

If you cannot find a positive sequence,you should consider 0 as the value of the maximum product.

Input

每個測試案例都以 1 ≤ N ≤ 18 開始，表示序列中元素的數量。每個元素 Si 都是整數，滿足 -10 ≤ Si ≤ 10。

接下來的一行將包含 N 個整數，代表序列中每個元素的值。

在每個測試案例之後會有一個空行。輸入以檔案結尾 (EOF) 為終止條件。

- ------------------------------------------------------------------------------

Each test case starts with1≤N≤18, the number of elements in a sequence. Each element Si is aninteger such that −10 ≤ Si ≤ 10.

Next line will have N integers, representing the value of each elementin the sequence.

There is a blank line after each test case. The input is terminated by end of file (EOF).

Output

每個測試案例您必須打印消息：“Case #M: 最大乘積為P。”，其中M是測試案例的編號，從1開始，而P是最大乘積的值。

在每個測試案例之後，您必須打印一個空行。

- ------------------------------------------------------------------------------

For each test case you must print the message: ‘Case #M:The maximum product is P.’, where Mis the number of the test case, starting from 1, and P is the value of the maximum product.

After each test case you must print a blank line.

Sample Input 1

```
3
2 4 -3

5
2 5 -1 2 -1
```

Sample Output 1

```
Case #1: The maximum product is 8.

Case #2: The maximum product is 20.
```

Sample Input 2

```
4
-1 0 0 0

1
0

1
1

1
-1
```

Sample Output 2

```
Case #1: The maximum product is 0.

Case #2: The maximum product is 0.

Case #3: The maximum product is 1.

Case #4: The maximum product is 0.
```

```c
#include <stdio.h>
#define ll long long

ll maxProduct(int *a, int n)
{
  int *pn = &n;
  ll max = 0, tmp;
  ll *pmax = &max, *ptmp = &tmp;
  
  for (int i = 0; i < *pn; i++)
  {
    *ptmp = 1;
    for (int j = i; j < *pn; j++)
    {
      *ptmp *= *(a+j);
      if (*ptmp > *pmax)
        *pmax = *ptmp;
    }
  }
  
  return *pmax;
}

int main()
{
  int n, cnt = 1;
  int *pn = &n, *pcnt = &cnt;
  
  while (scanf("%d", pn) != EOF)
  {
    int a[*pn];
    int *pa = a;
    for (int i = 0; i < *pn; i++)
      scanf("%d", pa+i);
    
    ll max;
    ll *pmax = &max;
    *pmax = maxProduct(pa, *pn);
    if (*pmax < 0)
      *pmax = 0;
    printf("Case #%d: The maximum product is %lld.\n\n", (*pcnt)++, *pmax);
  }
  
  return 0;
}
```