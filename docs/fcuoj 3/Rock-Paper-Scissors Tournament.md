# Rock-Paper-Scissors Tournament

Description

石頭、剪刀、布是一個兩個玩家的遊戲，分別是 A 和 B，他們每個人都獨立地選擇石頭、剪刀或布中的一個。

選擇布的玩家贏選擇石頭的玩家；選擇剪刀的玩家贏選擇布的玩家；選擇石頭的玩家贏選擇剪刀的玩家。選擇與對手相同的玩家既不贏也不輸。

一場錦標賽已經組織好了，其中每個玩家與其他玩家玩了 k 次石頭剪刀布遊戲 — 總共有 k ∗ n ∗ (n − 1) / 2 場比賽。

您的任務是計算每個玩家的平均勝率，定義為w / (w + l)，其中 w 是贏得的比賽數，l是輸掉的比賽數。

![https://oj.fcu.edu.tw/public/upload/72ffd09018.png](https://oj.fcu.edu.tw/public/upload/72ffd09018.png)

- ------------------------------------------------------------------------------

Rock-Paper-Scissors is game for two players, A and B, who each choose, independently of the other, one of rock, paper, or scissors.

A player chosing paper wins over a player chosing rock; a player chosing scissors wins over a player chosing paper;

a player chosing rock wins over a player chosing scissors. A player chosing the same thing as the other player neither wins nor loses.

A tournament has been organized in which each of n players plays k rock-scissors-paper games with each of the other players — k ∗ n ∗ (n − 1) / 2games in total.

Your job is to compute thew in average foreach player, defined as w / (w + l) where w is the number of games won, and l is the number of games lost, by the player.

![https://oj.fcu.edu.tw/public/upload/1463d226b9.png](https://oj.fcu.edu.tw/public/upload/1463d226b9.png)

Input

輸入包含多個測試案例。

每個案例的第一行包含1 ≤ n ≤ 100 和 1 ≤ k ≤ 100，如上所述。

對於每場比賽，接下來一行包含p1、m1、p2、m2。1 ≤ p1 ≤ n和1 ≤ p2 ≤ n是兩個玩家的不同整數標識；

m1 和 m2 是他們的各自動作（'rock'、'scissors' 或 'paper'）。最後一個測試案例之後跟著一行包含'0'。

- ------------------------------------------------------------------------------

Input consists of several test cases.

The first line of input for each case contains1 ≤ n ≤ 100 1 ≤ k ≤ 100as defined above.

For each game, a line follows containingp1, m1, p2, m2.1 ≤ p1 ≤ n and 1 ≤ p2 ≤ n are distinct integers identifying two players;

m1 and m2 are their respective moves (‘rock’, ‘scissors’, or ‘paper’). A line containing ‘0’ follows the last test case.

Output

輸出每個玩家的一行，從玩家1到玩家n，給出玩家的勝率，四捨五入到三位小數。

如果勝率未定義，輸出'-'。在測試案例之間輸出空行。

- ------------------------------------------------------------------------------

Output one line each for player 1, player 2, and so on, through player n, giving the player’s win averagerounded to three decimal places.

If the win average is undefined, output ‘-’.Output an empty linebetween cases.

Sample Input 1

```
2 4
1 rock 2 paper
1 scissors 2 paper
1 rock 2 rock
2 rock 1 scissors
2 1
1 rock 2 paper
0

```

Sample Output 1

```
0.333
0.667

0.000
1.000
```

Sample Input 2

```
4 1
2 rock 4 rock
3 paper 1 rock
3 paper 2 paper
2 scissors 1 scissors
1 scissors 4 paper
3 paper 4 scissors
0
```

Sample Output 2

```
0.500
-
0.500
0.500
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
  int n, k;
  char str[50];
  int x, y;
  char s1[10], s2[10];
  
  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    scanf("%d", &k);
    getchar();
    
    int cs = k * n * (n - 1) / 2;
    int tmp_cs = cs;
    int a[n];
    int plays[n];
    for (int i = 0; i < n; i++)
    {
      a[i] = 0;
      plays[i] = 0;
    }
    // printf("%d\n", cs);
    
    while (tmp_cs--)
    {
      fgets(str, sizeof(str), stdin);
      str[strcspn(str, "\n")] = '\0';
      int len = strlen(str);
      
      //printf("%s", str);
      sscanf(str, "%d %s %d %s", &x, s1, &y, s2);
      // printf("(%d %s %d %s)", x, s1, y, s2);
      x--;
      y--;
      
      if (strcmp(s1, "paper") == 0 && strcmp(s2, "rock") == 0)
      {
        a[x]++;
        plays[x]++;
        plays[y]++;
      }
      if (strcmp(s1, "paper") == 0 && strcmp(s2, "scissors") == 0)
      {
        a[y]++;
        plays[x]++;
        plays[y]++;
      }
      
      if (strcmp(s1, "rock") == 0 && strcmp(s2, "paper") == 0)
      {
        a[y]++;
        plays[x]++;
        plays[y]++;
      }
      if (strcmp(s1, "rock") == 0 && strcmp(s2, "scissors") == 0)
      {
        a[x]++;
        plays[x]++;
        plays[y]++;
      }
      
      if (strcmp(s1, "scissors") == 0 && strcmp(s2, "rock") == 0)
      {
        a[y]++;
        plays[x]++;
        plays[y]++;
      }
      if (strcmp(s1, "scissors") == 0 && strcmp(s2, "paper") == 0)
      {
        a[x]++;
        plays[x]++;
        plays[y]++;
      }
    }
    
    
    for (int i = 0; i < n; i++)
    {
      if (plays[i] == 0)
      {
        printf("-\n");
        continue;
      }
      printf("%.3f\n", (float)a[i] / plays[i]);
    }
    
    printf("\n");
  }
  
  return 0;
}
```