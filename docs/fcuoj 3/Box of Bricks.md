# Box of Bricks

Description

小Bob喜歡玩他的積木盒子。他將積木一層一層地放在一起，建造了不同高度的堆疊。

「看，我建了一堵牆！」，他告訴他的姐姐愛麗絲。

「不，你應該讓所有的堆疊高度都一樣。那樣你才會有一堵真正的牆。」，她反駁道。

經過一番考慮，Bob 發現她是對的。所以他開始重新安排積木，一塊一塊地移動，使得之後所有的堆疊高度都相同。

但由於 Bob 很懶，他想用最少數量的積木移動來完成這個任務。你能幫忙嗎？

![https://oj.fcu.edu.tw/public/upload/106d9a3c93.png](https://oj.fcu.edu.tw/public/upload/106d9a3c93.png)

- ------------------------------------------------------------------------------

Little Bob likes playing with his box of bricks. He puts the bricks one upon another and builds stacksof different height.

“Look, I’ve built a wall!”, he tells his older sister Alice.

“Nah, you should make allstacks the same height.Then you would have a real wall.”, she retorts.

After a little consideration,Bob sees that she is right. So he sets out to rearrange the bricks, one by one, such that all stacks arethe same height afterwards.

But since Bob is lazy he wants to do this with the minimum number ofbricks moved. Can you help?

![https://oj.fcu.edu.tw/public/upload/106d9a3c93.png](https://oj.fcu.edu.tw/public/upload/106d9a3c93.png)

Input

輸入包含多個資料集。每個資料集以一行開始，包含 Bob 堆疊的數量 n。

接下來一行包含 n 個數字，即 n 堆疊的高度 hi。您可以假設 1 ≤ n ≤ 50 和 1 ≤ hi ≤ 100。

積木的總數將被堆疊的數量整除。因此，始終可以重新排列積木，使所有堆疊的高度相同。

輸入以n=0開始的集合為終止標記，該集合不應進行處理。

- ------------------------------------------------------------------------------

The input consists of several data sets. Each set begins with a line containing the number n of stacksBob has built.

The next line contains n numbers, the heights hi of then stacks. You may assume1 ≤ n ≤ 50and1 ≤h i ≤ 100.

The total number of bricks will be divisible by the number of stacks. Thus, it is always possible torearrange the bricks such that all stacks have the same height.

The input is terminated by a set starting with n= 0. This set should not be processed.

Output

對於每個集合，首先按照範例輸出印出集合的編號。

然後印出一行'The minimum number of moves is k.'，其中 k 是必須移動的最小積木數量，以使所有堆疊的高度相同。

在每個集合後輸出一個空行。

- ------------------------------------------------------------------------------

For each set, first print the number of the set, as shown in the sample output.

Then print the line ‘Theminimum number of moves is k.’, where k is the minimum number of bricks that have to be movedin order to make all the stacks the same height.

Output a blank line after each set.

Sample Input 1

```
6
5 2 4 1 7 5
0
```

Sample Output 1

```
Set #1
The minimum number of moves is 5.
```

Sample Input 2

```
6
5 2 4 1 7 5
8
26 75 46 10 40 88 31 84
14
7 38 25 97 29 28 43 54 71 55 98 58 41 14
0
```

Sample Output 2

```
Set #1
The minimum number of moves is 5.

Set #2
The minimum number of moves is 97.

Set #3
The minimum number of moves is 151.
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
  int n;
  int cs = 1;
  
  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    
    int a[n];
    int sum = 0;
    for (int i = 0; i < n; i++)
    {
      scanf("%d", &a[i]);
      sum += a[i];
    }
    
    int mean = sum / n;
    int move = 0;
    
    for (int i = 0; i < n; i++)
    {
      if (a[i] > mean)
      {
        move += a[i] - mean;
      }
    }
    
    printf("Set #%d\n", cs++);
    printf("The minimum number of moves is %d.\n\n", move);
  }
  
  return 0;
}

```