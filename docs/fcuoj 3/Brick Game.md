# Brick Game

Description

在孟加拉國的一個村莊裡，有一個非常受歡迎的磚塊遊戲。磚塊遊戲是一種團隊遊戲，每個團隊由奇數個玩家組成。

玩家數量必須大於 1，但不能超過 10。每個玩家的年齡必須在 11 到 20 歲之間。

沒有兩個玩家可以有相同的年齡。每個團隊都有一個隊長。

兩個玩家之間的溝通差距取決於他們的年齡差異，即年齡差異越大，溝通差距越大。

因此，他們選擇團隊的隊長，使得團隊中年齡比隊長小的玩家數量等於年齡比隊長大的玩家數量。

提供了團隊所有成員的年齡。您需要確定隊長的年齡。

- ------------------------------------------------------------------------------

There is a village in Bangladesh, where brick game is very popular. Brick game is a team game. Each team consists of odd number of players.

Number of players must be greater than 1 but cannot be greater than 10. Age of each player must be within 11 and 20.

No two players can have the same age. There is a captain for each team.

The communication gap between two players depends on their age difference, i.e. the communication gap is larger if the age difference is larger.

Hence they select the captain of a team in such a way so that the number of players in the team who are younger than that captain is equal to the number of players who are older than that captain.

Ages of all members of the team are provided. You have to determine the age of the captain.

Input

輸入以一個整數 T (T ≤ 100) 開始，表示測試案例的數量。

接下來的每個 T 行將以一個整數 N (1 < N < 11) 開頭，表示一個團隊成員的數量，接著是 N 個以空格分隔的整數，代表團隊成員的年齡。

這 N 個整數中的每個都會介於 11 到 20 之間（含 11 和 20）。請注意，年齡將以嚴格遞增或嚴格遞減的方式給出。

我們不會提及哪一種是遞增的，哪一種是遞減的，您必須足夠小心以處理這兩種情況。

- ------------------------------------------------------------------------------

Input starts with an integer T(T≤100), the number of test cases.

Each of the next T lines will start with an integer N(1< N <11), number of team membersfollowed by N space separated integers representing ages of all of the members of a team.

Each of theseN integers will be between 11 and 20 (inclusive). Note that, ages will be given in strictly increasing orderor strictly decreasing order.

We will not mention which one is increasing and which one is decreasing,you have to be careful enough to handle both situations.

Output

對於每個測試案例，輸出一行格式為'Case x: a'（引號僅為了清晰起見），其中 x 是案例編號，a 是隊長的年齡。

- ------------------------------------------------------------------------------

For each test case, output one line in the format ‘Case x: a’ (quotes for clarity), where x is the case number and a is the age of the captain.

Sample Input 1

```
2
5 19 17 16 14 12
5 12 14 16 17 18
```

Sample Output 1

```
Case 1: 16
Case 2: 16
```

Sample Input 2

```
5
5 20 18 17 14 12
5 11 12 14 18 19
5 20 16 13 12 11
5 12 13 14 17 19
5 20 19 16 15 13
```

Sample Output 2

```
Case 1: 17
Case 2: 14
Case 3: 13
Case 4: 14
Case 5: 16
```

```c
#include <stdio.h>
#include <stdlib.h>

int cmp(const void *a, const void *b)
{
  return (*(int*)a - *(int*)b);
}

int main()
{
  int z;
  scanf("%d", &z);
  
  for (int k = 1; k <= z; k++)
  {
    int n;
    scanf("%d", &n);
    int a[n];
    for (int i = 0; i < n; i++)
      scanf("%d", &a[i]);
      
    qsort(a, n, sizeof(int), cmp);
    int ans;
    ans = a[n/2];
    
    printf("Case %d: %d\n", k, ans);
  }

  return 0;
}

```