# Jumping Mario

Description

馬力歐現在在最後的城堡裡。他現在需要跳過幾道牆壁，然後進入庫巴的房間，他必須打敗怪物才能拯救公主。

對於這個問題，我們只關心"跳過牆壁"這部分。你會得到從左到右的 N 個牆壁的高度。

馬力歐目前站在第一道牆上。他必須一個接一個地跳到相鄰的牆壁，直到他到達最後一道牆。

這意味著，他會跳 (N−1) 次。高跳是指馬力歐必須跳到比較高的牆壁上，同樣地，低跳是指馬力歐必須跳到比較矮的牆壁上。

你能找出馬力歐必須進行的總高跳和總低跳的次數嗎？

![https://oj.fcu.edu.tw/public/upload/ac754bc70c.png](https://oj.fcu.edu.tw/public/upload/ac754bc70c.png)

- **------------------------------------------------------------------------------**

Mario is in the final castle. He now needs to jump over few walls and then enter the Koopa’s Chamber where he has to defeat the monster in order to save the princess.

For this problem, we are only concerned with the “jumping over the wall” part. You will be given the heights of N walls from left to right.

Mario is currently standing on the first wall. He has to jump to the adjacent walls one after another until he reaches the last one.

That means, he will make (N−1) jumps. Ahigh jump is one where Mario has to jump to a taller wall, and similarly, a low jump is one where Mario has to jump to a shorter wall.

Can you find out the total number of high jumps and low jumps Mario has to make?

![https://oj.fcu.edu.tw/public/upload/335297d41c.png](https://oj.fcu.edu.tw/public/upload/335297d41c.png)

Input

輸入的第一行是一個整數 T（T < 30），表示測試案例的數量。

每個案例以一個整數 N（0 < N < 50）開始，該整數表示牆壁的數量。

接下來一行給出了從左到右 N 個牆壁的高度。每個高度都是不超過 10 的正整數。

- **------------------------------------------------------------------------------**

The first line of input is an integer T(T <30) that indicates the number of test cases.

Each case starts with an integer N(0< N <50) that determines the number of walls.

The next line gives the height of the N walls from left to right. Each height is a positive integer not exceeding 10.

Output

對於每個案例，輸出案例編號，後跟2個整數，分別表示總高跳和總低跳。

請參考範例以確定格式。

- **------------------------------------------------------------------------------**

For each case, output the case number followed by 2 integers, total high jumps and total low jumps, respectively.

Look at the sample for exact format.

Sample Input 1

```
3
8
1 4 2 2 3 5 3 4
1
9
5
1 2 3 4 5
```

Sample Output 1

```
Case 1: 4 2
Case 2: 0 0
Case 3: 4 0
```

```c
#include <stdio.h>

int main()
{
  int t, n;
  int a[55] = {};
  scanf("%d", &t);
  
  for (int z = 1; z <= t; z++)
  {
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
      scanf("%d", &a[i]);
    
    int high = 0;
    int low = 0;
    for (int i = 0; i < n; i++)
    {
      if (i == n-1) break;
      if (a[i+1] > a[i])
        high++;
      else if (a[i+1] < a[i])
        low++;
    }
    
    
    printf("Case %d: %d %d\n", z, high, low);
  }
  

  return 0;
}

```