# Die Game

Description

生活並不容易。有時候，情況超出你的控制。現在，作為ACM ICPC的參賽者，你可能正在嘗試生活的苦味。

但不要擔心！不要只看到生活的黑暗一面，也要看到光明的一面。

生活可能就像擲骰子的有趣遊戲一樣，做或死！最後，你可能能夠找到通向勝利的路。

這個問題來自一個使用骰子的遊戲。順便說一句，你知道什麼是骰子嗎？它與"死亡"沒有關係。

骰子是一個立方體物體，有六個面，每個面代表從一到六的不同數字，並標有相應數量的點。

由於骰子通常成對使用，"一個骰子"是一個很少使用的詞。你可能聽過一句著名的話"骰子已擲"。

遊戲開始時，莊家將骰子放在平坦的桌子上。在遊戲過程中，莊家會將骰子向各個方向滾動。

如果你能預測骰子停止滾動時頂部面所顯示的數字，你將贏得遊戲。

現在，請你寫一個模擬擲骰子的程序。

為了簡單起見，我們假設骰子既不滑動也不跳躍，而只是在桌子上四個方向滾動，即北、東、南和西。

在每場遊戲開始時，莊家將骰子放在桌子中央，並調整其方向，使得頂部、北部和西部分別顯示數字一、二和三。

對於其他三個面，我們沒有明確指定任何東西，但告訴你一個黃金法則：任何對立面上的數字之和始終為七。

你的程序應該接受一系列指令，每個指令都可以是"north"、"east"、"south"或"west"。一個"north"指令將骰子向北滾動，即頂部變為新的北部，北部變為新的底部，依此類推。

更確切地說，骰子以北部底部邊緣為軸向北方旋轉，旋轉角度為90度。

其他指令也將相應地將骰子滾動到各自的方向。

你的程序應該計算在序列中執行指令後最終顯示在頂部的數字。請注意，桌子非常大，遊戲過程中骰子不會掉落。

![https://oj.fcu.edu.tw/public/upload/bf26234208.png](https://oj.fcu.edu.tw/public/upload/bf26234208.png)

- ------------------------------------------------------------------------------

Life is not easy. Sometimes it is beyond your control. Now, as contestants of ACM ICPC, you might be just tasting the bitter of life.

But don’t worry! Do not look only on the dark side of life, but look also on the bright side.

Life may be an enjoyable game of chance, like throwing dice. Do or die! Then, at last, you might be able to find the route to victory.

This problem comes from a game using a die. By the way, do you know a die? It has nothing to do with ”death.”

A die is a cubic object with six faces, each of which represents a different number from one to six and is marked with the corresponding number of spots.

Since it is usually used in pair, ”a die” is a rarely used word. You might have heard a famous phrase ”the die is cast,” though.

When a game starts, a die stands still on a flat table. During the game, the die is tumbled in all directions by the dealer.

You will win the game if you can predict the number seen on the top face at the time when the die stops tumbling.

Now you are requested to write a program that simulates the rolling of a die.

For simplicity, we assume that the die neither slips nor jumps but just rolls on the table in four directions, that is, north, east, south, and west.

At the beginning of every game, the dealer puts the die at the center of the table and adjusts its direction so that the numbers one, two, and three are seen on the top, north, and west faces, respectively.

For the other three faces, we do not explicitly specify anything but tell you the golden rule: the sum of the numbers on any pair of opposite faces is always seven.

Your program should accept a sequence of commands, each of which is either “north”, “east”, “south”, or “west”. A “north” command tumbles the die down to north, that is, the top face becomes the new north, the north becomes the new bottom, and so on.

More precisely, the die is rotated around its north bottom edge to the north direction and the rotation angle is 90 degrees.

Other commands also tumble the die accordingly to their own directions.

Your program should calculate the number finally shown on the top after performing the commands in the sequence. Note that the table is sufficientlylarge and the die never falls off during the game.

![https://oj.fcu.edu.tw/public/upload/eb09055a57.png](https://oj.fcu.edu.tw/public/upload/eb09055a57.png)

Input

輸入包含一個或多個命令序列，每個序列對應一場遊戲。

命令序列的第一行包含一個正整數，表示序列中接下來的命令行數量。

您可以假設這個數字小於或等於1024。包含零的一行表示輸入的結束。

每個命令行包括一個命令，其中之一為 'north'、'east'、'south' 和 'west'。您可以假設任何行中都不會出現空白字符。

- ------------------------------------------------------------------------------

The input consists of one or more command sequences, each of which corresponds to a single game.

The first line of a command sequence contains a positive integer, representing the number of the following command lines in the sequence.

You may assume that this number is less than or equal to 1024. A line containing a zero indicates the end of the input.

Each command line includes a command that is one of ‘north’, ‘east’, ‘south’, and ‘west’. You may assume that no white space occurs in any lines.

Output

對於每個命令序列，輸出一行，僅包含遊戲結束時頂面的數字。

- ------------------------------------------------------------------------------

For each command sequence, output one line containing solely the number on the top face at the timewhen the game is finished.

Sample Input 1

```
1
north
3
north
east
south
0

```

Sample Output 1

```
5
1
```

Sample Input 2

```
1
east
1
south
1
west
5
north
south
east
west
south
0

```

Sample Output 2

```
3
2
4
2
```

```c
#include <stdio.h>

int main()
{
  
  int n;
  int tmp;
  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    
    int num[6] = {1, 2, 3, 6, 5, 4};
    char side[10];
    while (n--)
    {
      scanf("%s", side);
      if (strcmp(side, "north") == 0)
      {
        tmp = num[1];
        num[1] = num[0];
        num[0] = num[4];
        num[4] = num[3];
        num[3] = tmp;
      }
      
      if (strcmp(side, "south") == 0)
      {
        tmp = num[0];
        num[0] = num[1];
        num[1] = num[3];
        num[3] = num[4];
        num[4] = tmp;
      }
      
      if (strcmp(side, "east") == 0)
      {
        tmp = num[0];
        num[0] = num[2];
        num[2] = num[3];
        num[3] = num[5];
        num[5] = tmp;
      }
      
      if (strcmp(side, "west") == 0)
      {
        tmp = num[5];
        num[5] = num[3];
        num[3] = num[2];
        num[2] = num[0];
        num[0] = tmp;
      }
    }
    
    printf("%d\n", num[0]);
  }

  return 0;
}

```