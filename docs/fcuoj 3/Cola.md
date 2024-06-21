# Cola

Description

你看到便利商店推出了以下特價優惠：

「每歸還3個空瓶，可換取一瓶巧克力口味可樂」

現在你決定從店裡購買一些（假設N瓶）可樂。你想知道如何從店裡獲得最多的可樂。

以下圖案展示了當N=8時的情況。方法1是標準的方式：在喝完你的8瓶可樂後，你有8個空瓶。

你拿走其中6個，你就能獲得2瓶新的可樂。現在在喝完它們後，你有4個空瓶，所以你拿走其中3個以再次獲得一瓶新的可樂。最後，你只剩下2瓶，所以你無法再獲得新的可樂了。

因此，你享受了8 + 2 + 1 = 11瓶可樂。

實際上，你可以做得更好！在方法2中，你先向你的朋友（？！或店主？？）借了一個空瓶，然後你就可以享受8 + 3 + 1 = 12瓶可樂！

當然，你將不得不將你剩下的空瓶歸還給你的朋友。

![https://oj.fcu.edu.tw/public/upload/33fb064710.png](https://oj.fcu.edu.tw/public/upload/33fb064710.png)

- ------------------------------------------------------------------------------

You see the following special offer by the convenience store:

“A bottle of Choco Cola for every 3 empty bottles returned”

Now you decide to buy some (say N) bottles of cola from the store. You would like to know how you can get the most cola from them.

The figure below shows the case where N= 8. Method 1 is the standard way: after finishing your 8bottles of cola, you have 8 empty bottles.

Take 6 of them and you get 2 new bottles of cola. Now after drinking them you have 4 empty bottles, so you take 3 of them to get yet another new cola. Finally, you have only 2 bottles in hand, so you cannot get new cola any more.

Hence, you have enjoyed 8 + 2+ 1 = 11 bottles of cola.

You can actually do better! In Method 2, you first borrow an empty bottle from your friend (?! Or the storekeeper??), then you can enjoy 8 + 3 + 1 = 12 bottles of cola!

Of course, you will have to return your remaining empty bottle back to your friend.

![https://oj.fcu.edu.tw/public/upload/4f36123d74.png](https://oj.fcu.edu.tw/public/upload/4f36123d74.png)

Input

輸入包含多行，每行包含一個整數N（1 ≤ N ≤ 200）。

- ------------------------------------------------------------------------------

Input consists of several lines, each containing an integer N(1 ≤ N ≤ 200).

Output

對於每個情況，您的程式應該輸出您可以享受的可樂瓶的最大數量。

您可以向他人借空瓶，但如果這樣做，請確保在歸還之後您有足夠的瓶子。

注意：喝太多的可樂對健康不利，所以...在家裡不要嘗試這樣做!! :-)

- ------------------------------------------------------------------------------

For each case, your program should output the maximum number of bottles of cola you can enjoy.

You may borrow empty bottles from others, but if you do that, make sure that you have enough bottles after wards to return to them.

Note: Drinking too much cola is bad for your health, so... don’t try this at home!! :-)

Sample Input 1

```
8
```

Sample Output 1

```
12
```

Sample Input 2

```
1
2
3
4
5
6
7
8
9
10
```

Sample Output 2

```
1
3
4
6
7
9
10
12
13
15
```

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
  int n;
  int *pn = &n;
  while (scanf("%d", pn) != EOF)
  {
    int ans = 0;
    int *pans = &ans;
    *pans = *pn;

    while (*pn >= 3)
    {
      *pans += *pn / 3;
      *pn = *pn / 3 + *pn % 3;
    }
    
    *pans += *pn / 2;
    
    printf("%d\n", *pans);
  }
  
  return 0;
}
```