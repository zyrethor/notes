# Zapping

Description

我是一個喜歡看電視的人。然而，我不喜歡看單一頻道；我經常在不同的頻道之間切換。

我的狗嘗試吃掉我的遙控器，不幸的是，它部分損壞了。

我以前用來快速切換頻道的數字按鈕不再起作用了。

現在，我只有兩個按鈕可以切換頻道：一個是向上切換到下一個頻道（△ 按鈕），另一個是向下切換到上一個頻道（▽ 按鈕）。

這非常令人煩惱，因為如果我正在看第 3 頻道，想要切換到第 9 頻道，我必須按 6 次 △ 按鈕！

我的電視有 100 個頻道，方便地編號從 0 到 99。它們是循環的，這意味著如果我在第 99 頻道，按 △ 我會切換到第 0 頻道。

同樣地，如果我在第 0 頻道，按 ▽ 我會切換到第 99 頻道。

我想要一個程序，根據我目前觀看的頻道和我想要切換到的頻道，告訴我到達該頻道所需的最少按鈕按下次數。

- **------------------------------------------------------------------------------**

I’m a big fan of watching TV. However, I don’t like to watch a single channel; I’m constantly zapping between different channels.

My dog tried to eat my remote controller and unfortunately he partially destroyed it.

The numeric buttons I used to press to quickly change channels are not working anymore.

Now, I only have available two buttons to change channels: one to go up to the next channel (the △ button) and one to go down to the previous channel (the ▽ button).

This is very annoying because if I’m watching channel 3 and want to change to channel 9 I have to press the △ button 6 times!

My TV has 100 channels conveniently numbered 0 through 99. They are cyclic, in the sense that if I’m on channel 99 and press △ I’ll go to channel 0.

Similarly, if I’m on channel 0 and press ▽ I’ll change to channel 99.

I would like a program that, given the channel I’m currently watching and the channel I would like to change to, tells me the minimum number of button presses I need to reach that channel.

Input

輸入包含多個測試案例（最多 200 個）。

每個測試案例由一行中的兩個整數 a 和 b 描述。

a 是我目前觀看的頻道，b 是我想要切換到的頻道（0 ≤ a, b ≤ 99）。

輸入的最後一行包含兩個 '-1'，不應該進行處理。

- **------------------------------------------------------------------------------**

The input contains several test cases (at most 200).

Each test case is described by two integers a and b in a single line.

a is the channel I’m currently watching and b is the channel I would like to go to (0≤a, b≤99).

The last line of the input contains two ‘-1’s and should not be processed.

Output

對於每個測試案例，在單獨的一行上輸出一個整數

達到新頻道所需的最少按鈕按下次數（請記住，我只有 △ 和 ▽ 兩個可用的按鈕）。

- **------------------------------------------------------------------------------**

For each test case, output a single integer on a single line

the minimum number of button presses needed to reach the new channel (Remember, the only two buttons I have available are △ and ▽).

Sample Input 1

```
3 9
0 99
12 27
-1 -1
```

Sample Output 1

```
6
1
15
```

Sample Input 2

```
19 42
12 74
0 0
99 38
-1 -1
```

Sample Output 2

```
23
38
0
39
```

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
  int a, b;
  int *pa = &a, *pb = &b;
  while (scanf("%d %d", pa, pb))
  {
    if (*pa == -1 && *pb == -1) break;
    
    int pos = 0, neg = 0;
    int *ppos = &pos, *pneg = &neg;
    *ppos = abs(*pa - *pb);
    *pneg = 100 - abs(*pa - *pb);
    
    if (*pneg >= 0 && *pneg <= *ppos)
      printf("%d\n", *pneg);
    else if (*ppos >= 0 && *ppos <= *pneg)
      printf("%d\n", *ppos);
  }
  
  return 0;
}

```