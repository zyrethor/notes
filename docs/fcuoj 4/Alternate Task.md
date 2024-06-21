# Alternate Task

Description

小哈桑喜歡和朋友們玩數字遊戲。

有一天，他們在玩一個遊戲，其中一個人會說出一個正數，其他人要說出這個數字的所有因數的總和。第一個正確說出的人獲勝。玩了一段時間後，他們覺得有些無聊，想嘗試不同的遊戲。

哈桑建議嘗試反過來的遊戲。也就是說，給定一個正數 S，他們要找到一個數字，其因數的總和等於 S。

意識到這個任務比原來的任務更難，哈桑來找你幫忙。幸運的是，哈桑擁有一個便攜式可編程裝置，而你決定為這個裝置寫一個程式。

給定 S 的值作為程式的輸入，程式將輸出一個因數總和等於 S 的數字。

- ------------------------------------------------------------------------------

Little Hasan loves to play number games with his friends.

One day they were playing a game whereone of them will speak out a positive number and the others have to tell the sum of its factors.

Thefirst one to say it correctly wins. After a while they got bored and wanted to try out a different game.

Hassan then suggested about trying the reverse. That is, given a positive number S, they have to finda number whose factors add up to S.

Realizing that this task is tougher than the original task, Hasancame to you for help. Luckily Hasan owns a portable programmable device and you have decided toburn a program to this device.

Given the value of S as input to the program, it will output a numberwhose sum of factors equal to S.

Input

每個輸入案例將由一個正整數 S 組成，且 S ≤ 1000。

最後一個案例後面會跟著一個值為 ‘0’。

- ------------------------------------------------------------------------------

Each case of input will consist of a positive integer S ≤ 1000.

The last case is followed by a value of ‘0’

Output

對於每個輸入案例，將有一行輸出。輸出將是一個正整數，其因數總和等於 S。

如果有多個這樣的整數，輸出其中最大的。如果不存在這樣的數字，輸出 ‘-1’。

請遵守範例輸出中顯示的格式。

- ------------------------------------------------------------------------------

For each case of input, there will be one line of output. It will be a positive integer whose sum of factorsis equal to S.

If there is more than one such integer, output the largest. If no such number exists,output ‘-1’.

Adhere to the format shown in sample output.

Sample Input 1

```
1
102
1000
0

```

Sample Output 1

```
Case 1: 1
Case 2: 101
Case 3: -1

```

Sample Input 2

```
2
4
12
24
9
15
39
0

```

Sample Output 2

```
Case 1: -1
Case 2: 3
Case 3: 11
Case 4: 23
Case 5: -1
Case 6: 8
Case 7: 18
```

```c
#include <stdio.h>
#include <stdbool.h>

int getfac(int n)
{
  int ans = 0;
  for (int i = 1; i <= n; i++)
  {
    if (n % i == 0)
      ans += i;
  }
  
  return ans;
}

int main()
{
  int n;
  int cnt = 1;
  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    
    bool flag = false;
    printf("Case %d: ", cnt++);
    for (int i = n; i >= 0; i--)
    {
      if (getfac(i) == n)
      {
        printf("%d\n", i);
        flag = true;
        break;
      }
    }
    
    if (!flag)
      printf("-1\n");
  }

  return 0;
}

```