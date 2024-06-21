# Sales

Description

CozyWalk Co.的CEO Cooper先生自公司成立以來，每天都會收到一份日銷售報告。

自從公司成立的第二天開始，他在收到報告後會將其與之前的每個報告進行比較，以計算出銷售額小於或等於該報告的前幾天的數量。

在獲得這樣的天數後，他將其寫入一個列表中。

這個問題可以更正式地陳述如下。

設A= (a1, a2, . . . , an)表示每日銷售金額的列表。讓B= (b1, b2, . . . , bn−1)是由Cooper先生維護的另一個整數列表，每個值表示這樣的前一天的數量。

在第i天 (2 ≤ i ≤ n)，他計算bi−1，表示ak≤ai (1 ≤ k < i) 的數量。

例如，假設A= (20,43,57,43,20)。對於第四天的銷售金額，a4= 43，銷售金額小於或等於它的前一天的數量是2，因為a1 ≤ a4，a2 ≤ a4，而a3 > a4。因此，b3 = 2。類似地，可以得到b1、b2和b4，結果為B= (1,2,2,1)。

給定一個大小為n的每日銷售金額列表的數組，編寫一個程序，打印列表B中n−1個整數的總和。

- ------------------------------------------------------------------------------

Mr. Cooper, the CEO of CozyWalk Co., receives a report of daily sales every day since the company has been established.

Starting from the second day since its establishment, on receiving the report, he compares it with each of the previous reports in order to calculate the number of previous days whose sales amounts are less than or equal to it.

After obtaining the number of such days, he writes it in a list.

This problem can be stated more formally as follows.

Let A= (a1, a2, . . . , an) denote the list of daily sales amounts. And let B= (b1, b2, . . . , bn−1) be another integer list maintained by Mr. Cooper, each value representing the number of such previous days.

On the i-th day (2 ≤ i ≤ n), he calculatesbi−1, the number of ak’s such that ak ≤ ai(1 ≤ k < i).

For example, suppose that A= (20,43,57,43,20). For the fourth day’s sales amount, a4= 43, the number of previous days whose sales amounts are less than or equal to it is 2 since a1 ≤ a4, a2 ≤ a4, anda3 > a4. Therefore, b3 = 2. Similarly, b1, b2, and b4 can be obtained and it results in B= (1,2,2,1).

Given an array of size n for the list of daily sales amounts, write a program that prints the sum of the n−1 integers in the list B.

Input

您的程序需要從標準輸入中讀取輸入。輸入包含T組測試資料。

第一行輸入為測試案例數量 T。

每個測試用例以包含一個整數n(2 ≤ n ≤ 1,000)的行開始，該整數表示列表A的大小。

接下來的一行中，給出n個整數，每個整數表示測試用例中的每日銷售金額ai (1 ≤ ai ≤ 5,000 且 1 ≤ i ≤ n)。

- ------------------------------------------------------------------------------

Your program is to read the input from standard input. The input consists of T test cases.

The numberof test cases T is given in the first line of the input.

Each test case starts with a line containing aninteger n(2 ≤ n ≤ 1,000), which represents the size of the list A.

In the following line, n integers aregiven, each represents the daily sales amounts ai (1 ≤ ai ≤ 5,000 and 1 ≤ i ≤ n) for the test case.

Output

您的程序需要寫入標準輸出。對於每個測試用例，請打印從列表A獲取的列表B中n−1個整數的總和。

以下是兩個測試用例的示例輸入和輸出。

- ------------------------------------------------------------------------------

Your program is to write to standard output. For each test case, print the sum of then−1integers inthe list B which is obtained from the list A.

The following shows sample input and output for two test cases.

Sample Input 1

```
2
5
38 111 102 111 177
8
276 284 103 439 452 276 452 398

```

Sample Output 1

```
9
20

```

Sample Input 2

```
5
4
4 3 2 1
4
1 2 3 4
4
1 4 3 2
6
11 56 22 41 43 46
7
2 5 7 4 3 1 6

```

Sample Output 2

```
0
6
3
11
10
```

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main()
{
  int n, k;
  char str[105];

  scanf("%d", &n);
  while (n--)
  {
    int ans = 0;
    scanf("%d", &k);
    int a[k];

    for (int i = 0; i < k; i++)
      scanf("%d", &a[i]);

    for (int i = 1; i < k; i++)
    {
      for (int j = i-1; j >= 0; j--)
      {
        if (a[i] >= a[j]) ans++;
      }
    }

    printf("%d\n", ans);
  }

  return 0;
}
```