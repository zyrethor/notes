# Shopaholic

Description

Lindsay是一個購物狂。每當有類似於買三件物品只需付兩件錢的折扣時，她就完全瘋狂了，感覺必須買下店裡的所有物品。

你已經放棄治療她這種疾病，但試圖限制對她錢包的影響。

你已經意識到，提供這些優惠的商店在選擇哪些物品免費時相當挑剔；它總是選擇最便宜的那些。

例如，當你的朋友帶著七件物品來到櫃檯，價值分別為400、350、300、250、200、150和100美元時，她將支付1500美元。

在這種情況下，她獲得了250美元的折扣。你意識到，如果她三次去櫃檯，她可能會獲得更大的折扣。

例如，如果她帶著價值400、300和250美元的物品，她將在第一輪獲得250美元的折扣。

接下來一輪，她帶來了價值150美元的物品，沒有額外的折扣，但第三輪，她帶走了價值350、200和100美元的最後一批物品，額外獲得100美元的折扣，總計折扣為350美元。

你的任務是找到 Lindsay 可以獲得的最大折扣。

![https://oj.fcu.edu.tw/public/upload/863254c54f.png](https://oj.fcu.edu.tw/public/upload/863254c54f.png)

- ------------------------------------------------------------------------------

Lindsay is a shopaholic.

Whenever there is a discountof the kind where you can buy three items and onlypay for two, she goes completely mad and feels a needto buy all items in the store.

You have given up oncuring her for this disease, but try to limit its effecton her wallet.

You have realized that the stores coming withthese offers are quite selective when it comes to which items you get for free; it is always the cheapestones.

As an example, when your friend comes to the counter with seven items, costing 400, 350, 300,250, 200, 150, and 100 dollars, she will have to pay 1500 dollars.

In this case she got a discount of 250dollars. You realize that if she goes to the counter three times, she might get a bigger discount.

E.g. ifshe goes with the items that costs 400, 300 and 250, she will get a discount of 250 the first round.

Thenext round she brings the item that costs 150 giving no extra discount, but the third round she takesthe last items that costs 350, 200 and 100 giving a discount of an additional 100 dollars, adding up toa total discount of 350.

Your job is to find the maximum discount Lindsay can get.

![https://oj.fcu.edu.tw/public/upload/863254c54f.png](https://oj.fcu.edu.tw/public/upload/863254c54f.png)

Input

輸入的第一行給出測試情境的數量，1 ≤ t ≤ 20。每個情境包括兩行輸入。

第一行給出 Lindsay 要購買的物品數量，1 ≤ n ≤ 20000。接下來的一行給出這些物品的價格，1 ≤ pi ≤ 20000。

- ------------------------------------------------------------------------------

The first line of input gives the number of test scenarios,1 ≤ t ≤ 20.Each scenario consists of twolines of input.

The first gives the number of items Lindsay is buying,1≤n≤20000. The next linegives the prices of these items,1≤pi≤20000.

Output

對於每種情況，輸出一行，給出 Lindsay 可以通過選擇哪些物品一次性帶到櫃檯上以獲得的最大折扣。

- ------------------------------------------------------------------------------

For each scenario, output one line giving the maximum discount Lindsay can get by selectively choosing which items she brings to the counter at the same time.

Sample Input 1

```
1
6
400 100 200 350 300 250
```

Sample Output 1

```
400
```

Sample Input 2

```
2
7
984 476 900 316 376 513 355
19
757 828 535 706 735 71 986 687 748 130 7 529 278 520 315 563 466 86 46
```

Sample Output 2

```
868
2640
```

```c
#include <stdio.h>
#include <stdlib.h>

void bubble(int* a, int n)
{
  for (int i = 0; i < n; i++)
  {
    for (int j = 0; j < n-1-i; j++)
    {
      if (*(a+j) < *(a+j+1))
      {
        int tmp = *(a+j);
        *(a+j) = *(a+j+1);
        *(a+j+1) = tmp;
      }
    }
  }
}

int main()
{
  int z;
  scanf("%d", &z);
  
  while (z--)
  {
    int n;
    scanf("%d", &n);
    int a[n];
    for (int i = 0; i < n; i++)
      scanf("%d", &a[i]);
    
    bubble(a, n);
    
    int ans = 0;
    for (int i = 2; i < n; i+=3)
      ans += a[i];
    
    printf("%d\n", ans);
  }
  
  return 0;
}
```

```c
#include <stdio.h>
#include <stdlib.h>

void bubble(int* a, int n)
{
  for (int i = 0; i < n; i++)
  {
    for (int j = 0; j < n-1-i; j++)
    {
      if (*(a+j) < *(a+j+1))
      {
        int tmp;
        int *ptmp = &tmp;
        *ptmp = *(a+j);
        *(a+j) = *(a+j+1);
        *(a+j+1) = *ptmp;
      }
    }
  }
}

int main()
{
  int z;
  int *pz = &z;
  scanf("%d", pz);
  
  while ((*pz)--)
  {
    int n;
    int *pn = &n;
    scanf("%d", pn);
    int a[n];
    int *pa = &a;
    for (int i = 0; i < n; i++)
      scanf("%d", a+i);
    
    bubble(pa, *pn);
    
    int ans = 0;
    int *pans = &ans;
    for (int i = 2; i < *pn; i+=3)
      *pans += *(a+i);
    
    printf("%d\n", *pans);
  }
  
  return 0;
}
```