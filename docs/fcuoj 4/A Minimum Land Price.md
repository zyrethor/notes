# A Minimum Land Price

Description

ACM-ICPC 泰國比賽理事會的經理計劃在普吉島購買土地，以建造國家程式設計技能營和程式設計比賽的辦公大樓，未來將定期在普吉島舉行。

普吉島的地價每年都在變得越來越貴。地價會以年度的指數增長曲線增加。

如果地塊 𝑖 的初始價格為 𝐿𝑖，在 𝑡 年後購買，其價格將是2×(𝐿𝑖)^𝑡。所有地塊價格各不相同。

ACM-ICPC 每年只能購買一塊土地。你需要幫助經理在5,000,000百萬泰銖的預算內，以最低價格購買這些土地。

例如，如果我們希望在連續的三年中購買三塊地，其成本分別為7、2和10，總價格將如下計算：

(2×7) + (2×2^2) + (2×10^3) = 2022百萬泰銖

- ------------------------------------------------------------------------------

Manager of ACM-ICPC Thailand Contest Council is planning to buy lands in Phuket to build the officebuilding for national programming skill camp and programming contest that will be held on Phuketregularly in the future.

The land price in Phuket is becoming more expensive in every year. The pricein creases in the exponential growth curves by a factor of year.

If the land𝑖whose initial cost is𝐿𝑖bought in𝑡years from now, its price will be2×(𝐿𝑖)^𝑡. All land prices are different.

ACM-ICPC canbuy only one land per year. You have to help the manager to buy the lands at lowest price within thebudget of 5,000,000 millions baht.

For example, if we want to buy 3 lands with costs 7, 2 and 10 in 3 consecutive years, the total pricewill be calculated as follow.

(2×7) + (2×2^2) + (2×10^3) = 2022millions baht

Input

輸入的第一行包含一個整數 𝑇（1 ≤ 𝑇 ≤ 10），表示測試案例的數量。

每個測試案例包含多個整數 𝐿𝑖，表示每塊土地的價格，以百萬泰銖計算。每個測試案例中有少於40塊土地。

每行包含一個‘0’（零）表示該測試案例的結束。

- ------------------------------------------------------------------------------

First line of the input contains an integer𝑇(1 ≤ T ≤ 10), the number of test cases.

Each test casecontains integer𝐿𝑖which is the cost of land in million baht. There are less than 40 lands in each testcase.

The line contains ‘0’ (zero) indicates the end of each test case.

Output

對於每個測試案例，輸出購買所有土地的最低價格。

如果總價格超過預算（5,000,000 百萬泰銖），則輸出「Too expensive」。

- ------------------------------------------------------------------------------

For each test case, print out the minimum price for purchasing all lands.

If the total price exceeds thebudget (5,000,000 millions baht), print out ‘Too expensive’.

Sample Input 1

```
3
7
2
10
0
20
29
31
0
42
41
40
37
20
0

```

Sample Output 1

```
134
17744
Too expensive

```

Sample Input 2

```
3
2
3
1
0
1
4
1
5
0
300000
200000
0

```

Sample Output 2

```
16
46
Too expensive
```

```c
#include <stdio.h>
#include <math.h>

#define ll long long

void bubble(int arr[], int n)
{
  for (int i = 0; i < n; i++)
  {
    for (int j = 0; j < n-i-1; j++)
    {
      if (arr[j] < arr[j+1])
      {
        int tmp = arr[j];
        arr[j] = arr[j+1];
        arr[j+1] = tmp;
      }
    }
  }
}

int main()
{
  int n, k;
  scanf("%d", &n);
  while (n--)
  {
    ll ans = 0;
    int cnt = 0;
    int a[45] = {};
    while (1)
    {
      scanf("%d", &k);
      if (k == 0) break;
      
      a[cnt++] = k;
    }
    bubble(a, cnt);
    
    for (int i = 0; i < cnt; i++)
      ans += 2 * (ll)pow(a[i], i+1);
    
    if (ans > 5000000)
      printf("Too expensive\n");
    else
      printf("%lld\n", ans);
  }
  
  return 0;
}

```