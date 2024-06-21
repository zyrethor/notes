# Optimal Parking

Description

當在 Long Street 上購物時，Michael 通常會將他的車停在某個隨機位置，然後步行前往他需要的商店。

你能幫助 Michael 選擇一個停車位置，以最小化他在購物過程中需要步行的距離嗎？

Long Street 是一條直線，其中所有位置都是整數。你需要支付在特定插槽停車，該插槽是 Long Street 上的一個整數位置。

Michael 不想支付超過一個停車位的費用。他非常強壯，不介意攜帶所有的購物袋。

![https://oj.fcu.edu.tw/public/upload/afa4d4b8eb.png](https://oj.fcu.edu.tw/public/upload/afa4d4b8eb.png)

- ------------------------------------------------------------------------------

When shopping on Long Street, Michael usually parks his car at some randomlocation, and then walks to the stores he needs.

Can you help Michael choosea place to park which minimises the distance he needs to walk on his shopping round?

Long Street is a straight line, where all positions are integer. You pay forparking in a specific slot, which is an integer position on Long Street.

Michaeldoes not want to pay for more than one parking though. He is very strong,and does not mind carrying all the bags around.

![https://oj.fcu.edu.tw/public/upload/70247a81b9.png](https://oj.fcu.edu.tw/public/upload/70247a81b9.png)

Input

輸入的第一行給出測試案例的數量，1 ≤ t ≤ 100。每個測試案例有兩行。

第一行給出 Michael 想要拜訪的商店數量，1 ≤ n ≤ 20；第二行給出這些商店在 Long Street 上的整數位置，0 ≤ xi ≤ 99。

- ------------------------------------------------------------------------------

The first line of input gives the number of test cases,1 ≤ t ≤ 100. There are two lines for each testcase.

The first gives the number of stores Michael wants to visit,1≤n≤20, and the second gives theirninteger positions on Long Street,0≤xi≤99.

Output

對於每個測試案例，輸出一行，其中包含 Michael 必須步行的最小距離，假設他選擇最佳停車位置。

- ------------------------------------------------------------------------------

Output for each test case a line with the minimal distance Michael must walk given optimal parking.

Sample Input 1

```
2
4
24 13 89 37
6
7 30 41 14 39 42
```

Sample Output 1

```
152
70
```

Sample Input 2

```
3
1
50
4
35 22 68 0
20
34 1 28 49 99 3 45 11 26 55 89 76 32 67 44 91 39 0 47 23
```

Sample Output 2

```
0
136
198
```

```c
#include <stdio.h>
#include <stdlib.h>

int compare(const void* a, const void* b)
{
  return (*(int*)a - *(int*)b);
}

int main()
{
  int z;
  scanf("%d", &z);
  while (z--)
  {
    int n;
    scanf("%d", &n);
    
    int a[n];
    for (int i = 0; i < n; i++)
      scanf("%d", &a[i]);
      
    qsort(a, n, sizeof(int), compare);
    
    int ans = 0;
    ans = (a[n-1] - a[0]) * 2;
    
    printf("%d\n", ans);
  }

  return 0;
}
```

```c
#include <stdio.h>
#include <stdlib.h>

int compare(const void* a, const void* b)
{
  return (*(int*)a - *(int*)b);
}

int main()
{
  int z;
  int *pz = &z;
  scanf("%d", pz);
  while ((*pz)--)
  {
    int n;
    int *pn = &n;
    scanf("%d", pn);
    
    int a[n];
    int *pa = &a;
    for (int i = 0; i < *pn; i++)
      scanf("%d", a+i);
      
    qsort(pa, n, sizeof(int), compare);
    
    int ans = 0;
    int *pans = &ans;
    *pans = (*(pa+n-1) - *(pa)) * 2;
    
    printf("%d\n", *pans);
  }

  return 0;
}
```