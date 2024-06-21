# Strategy Game

Description

一個有 J 名玩家參與的策略遊戲圍繞著桌子進行。玩家按編號從 1 到 J 標識，總共將進行 R 回合。

在每個回合中，每個玩家都會依照其編號順序輪流進行遊戲；也就是說，玩家 1 會先進行，玩家 2 接著進行，以此類推。

當玩家 J 完成遊戲後，該回合結束，並開始下一回合。

每位玩家每次進行遊戲時都會獲得一定數量的勝利點數。

當所有回合結束後，每位玩家的總點數將計算為每回合中獲得的勝利點數的總和。

獲得最高點數的玩家將成為勝利者；如果有平手情況，則最後一個獲得最高點數的玩家將成為勝利者。

給定玩家數量、回合數量以及按照獲得順序排列的勝利點數列表，你必須確定哪位玩家是勝利者。

- ------------------------------------------------------------------------------

A strategy game with J players is played around a table. Players are identified by numbers from 1 to J and will play a total of R rounds.

At each round each player will play once, in the order of their identifiers; that is, player 1 will play first, player 2 will play second, and so on.

Once player J plays, the round is complete, and a next round starts.

A player earns a certain amount of Victory Points every time she or he plays.

After all rounds are finished the total points of each player is computed as the sum of Victory Points the player earned on each round.

The winner is the player with the maximum number of points; in case of a tie the winner is the player who earned the maximum number of points and played last.

Given the number of players, the number of rounds and a list describing the Victory Points in the order they were obtained, you must determine which player is the winner.

Input

輸入包含若干個測試案例。在每個測試案例中，第一行包含兩個整數 J 和 R，分別表示玩家數量和回合數量（1 ≤ J, R ≤ 500）。

第二行包含 J * R 個整數，表示每位玩家在每回合中獲得的勝利點數，按順序排列。

每次回合中獲得的勝利點數將始終是 0 到 100 之間的整數。如果 J 和 R 都為零，則輸入結束。

- ------------------------------------------------------------------------------

Theinputcontainsseveraltestcases.Ineachtestcase,thefirstlinecontainstwointegersJandR,respectivelythenumberofplayer sandthenumberofturns(1≤J,R≤5 00).

ThesecondlinecontainsJ∗Rintegers,representingtheVictoryPointsearnedbyeachplayerineachturn,intheordertheyhappened.

TheVictoryPointsobtainedineachturnwillbealwaysintegernumbersbetween0and100,inclusive.If both J and R are of values zero, then the input ends.

Output

對於輸入中的每個測試案例，你的程式必須輸出一行，包含一個整數，表示勝利者的編號。

- ------------------------------------------------------------------------------

For each test case in the input, your program must produce one single line, containing the integerrepresenting the winner.

Sample Input 1

```
3 3
1 1 1 1 2 2 2 3 3
2 3
0 0 1 0 2 0
0 0

```

Sample Output 1

```
3
1

```

Sample Input 2

```
4 3
1 2 3 4 5 6 7 8 9 10 11 12
4 5
1 2 3 4 1 2 3 4 1 2 3 4 1 2 3 4 1 2 3 4
8 1
5 3 29 99 75 57 92 5
0 0

```

Sample Output 2

```
4
4
4
```

```c
#include <stdio.h>

int main()
{
  int m, n, k;
  while (1)
  {
    scanf("%d %d", &m, &n);
    if (m == 0 && n == 0) break;
    
    int a[m];
    for (int i = 0; i < m; i++)
    {
      a[i] = 0;
    }
    
    for (int i = 0; i < n; i++)
    {
      for (int j = 0; j < m; j++)
      {
        scanf("%d", &k);
        a[j] += k;
      }
    }
    
    int max = 0, max_idx = 0;
    for (int i = 0; i < m; i++)
    {
      if (a[i] >= max)
      {
        max = a[i];
        max_idx = i + 1;
      }
    }
    
    printf("%d\n", max_idx);
  }

  return 0;
}

```