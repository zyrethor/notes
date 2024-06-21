# Lumberjack Sequencing

Description

又是一個關於伐木工的故事嗎？讓我們來看看……

伐木工是粗魯的、有鬍子的工人，而工頭則往往專橫且思想簡單。

工頭喜歡騷擾伐木工，讓他們按鬍鬚的長度排成十人一組。

伐木工因身高不同，會變換排列方式以迷惑工頭。

因此，工頭必須實際測量鬍鬚的長度（以公分計），以確認每個人是否按順序排列。

您的任務是編寫一個程序，以協助工頭判斷伐木工是否正確排列，不論是從最短到最長的鬍鬚，還是從最長到最短的鬍鬚。

- ------------------------------------------------------------------------------

Another tale of lumberjacks?. Let see . . .

The lumberjacks are rude, bearded workers, while foremen tend to be bossy and simpleminded.

The foremen like to harass the lumberjacks by making them line up in groups of ten, ordered by the length of their beards.

The lumberjacks, being of different physical heights, vary their arrangements to confuse the foremen.

Therefore, the foremen must actually measure the beards in centimeters to see if everyone is lined up in order.

Your task is to write a program to assist the foremen in determining whether or not the lumberjacks are lined up properly, either from shortest to longest beard or from longest to shortest.

Input

輸入從一行開始，包含一個單一整數 N，0 < N < 20，這是要處理的組別數量。

接下來有 N 行，每行包含十個不同的小於 100 的正整數。

- ------------------------------------------------------------------------------

The input starts with line containing a single integer N, 0< N <20, which is the number of groups to process.

Following this are N lines, each containing ten distinct positive integers less than 100.

Output

有一個標題行，然後每組鬍鬚長度占一行。請參考範例輸出以確認大小寫和標點符號。

- ------------------------------------------------------------------------------

There is a title line, then one line per set of beard lengths. See the sample output for capitalization and punctuation.

Sample Input 1

```
3
13 25 39 40 55 62 68 77 88 95
88 62 77 20 40 10 99 56 45 36
91 78 61 59 54 49 43 33 26 18
```

Sample Output 1

```
Lumberjacks:
Ordered
Unordered
Ordered
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

int cmp1 (const void* a, const void* b)
{
  return (*(int*)a - *(int*)b);
}

int cmp2 (const void* a, const void* b)
{
  return (*(int*)b - *(int*)a);
}

int main()
{
  int n;
  scanf("%d", &n);
  printf("Lumberjacks:\n");
  
  while (n--)
  {
    int a[10] = {};
    int b[10] = {};
    int flag = true;
    
    for (int i = 0; i < 10; i++)
    {
      scanf("%d", &a[i]);
      b[i] = a[i];
    }
    
    qsort(b, 10, sizeof(int), cmp1);
    for (int i = 0; i < 10; i++)
    {
      if (a[i] != b[i])
        flag = false;
    }
    qsort(b, 10, sizeof(int), cmp2);
    if (!flag)
    {
      for (int i = 0; i < 10; i++)
      {
        if (a[i] == b[i])
          flag = true;
        else
          flag = false;
      }
    }
    
    if (flag)
      printf("Ordered\n");
    else
      printf("Unordered\n");
  }

  return 0;
}
```