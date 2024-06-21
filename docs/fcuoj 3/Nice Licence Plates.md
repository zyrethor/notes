# Nice Licence Plates

Description

阿爾伯塔省的車牌目前的格式是ABC-0123（三個字母後跟四個數字）。

如果第一部分的值和第二部分的值的絕對差至多為100，我們說這個車牌是“nice”。

第一部分的值是以26進制數字計算的（其中數字位於[A..Z]之間）。

例如，如果第一部分是“ABC”，其值為28（0∗26^2+ 1∗26^1+ 2∗26^0）。所以，車牌“ABC-0123”是好的，因為|28−123|  ≤ 100。

給定車牌號碼的列表，您的程序應該確定該車牌是否是nice。

![https://oj.fcu.edu.tw/public/upload/4b1089e0d3.png](https://oj.fcu.edu.tw/public/upload/4b1089e0d3.png)

- ------------------------------------------------------------------------------

Alberta licence plates currently have a format ofABC-0123 (three letters followed by four digits).

We say that the licence plate is “nice” if the absolute difference between the value of the first part andthe value of the second part is at most 100.

The value of the first part is calculated as the value of base-26 number (where digits are in [A..Z]).

For instance, if the first part is “ABC”, its value is 28(0∗26^2+ 1∗26^1+ 2∗26^0). So, the plate “ABC-0123”is nice, because|28−123| ≤100.

Given the list of licence plate numbers, your program should determine if the plate is nice or not.

![https://oj.fcu.edu.tw/public/upload/4b1089e0d3.png](https://oj.fcu.edu.tw/public/upload/4b1089e0d3.png)

Input

輸入的第一行包含一個整數N（1 ≤ N ≤ 100），表示車牌號碼的數量。

接下來是N行，每行包含一個以格式‘LLL-DDDD’表示的車牌。

- ------------------------------------------------------------------------------

First line of the input contains an integer N(1 ≤ N ≤ 100), the number of licence plate numbers.

Then follow N lines, each containing a licence plate in the format ‘LLL-DDDD’.

Output

對於每個車牌，根據問題描述中所述的車牌是否為好的，請在一行中印出“nice”或“not nice”（不帶引號）。

- ------------------------------------------------------------------------------

For each licence plate print on a line ‘nice’ or ‘not nice’ (without quotes) depending on the platenumber being nice as described in the probem statement.

Sample Input 1

```
2
ABC-0123
AAA-9999

```

Sample Output 1

```
nice
not nice

```

Sample Input 2

```
5
APA-0963
BYC-0187
BPD-1674
BAI-1179
BBZ-0430

```

Sample Output 2

```
not nice
not nice
not nice
not nice
not nice
```

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main()
{
  int n;
  char str[105];
  scanf("%d", &n);

  while (n--)
  {
    char s1[100];
    char s2[100];
    scanf("%s", str);
    sscanf(str, "%[^-]-%[^-]", s1, s2);
    
    int n1 = 0, n2 = 0;
    int len = strlen(s1);
    for (int i = 0; i < len; i++)
    {
      n1 += (s1[i] - 'A') * pow(26, len-1-i);
    }

    n2 += atoi(s2);

    if (abs(n1 - n2) <= 100)
      printf("nice\n");
    else
      printf("not nice\n");
  }

  return 0;
}
```