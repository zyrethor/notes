# Reverse and Add

Description

「反轉和相加」的方法很簡單：選擇一個數字，將其數字反轉並加到原始數字上。

如果這個和不是回文數（意思是，它不是從左到右和從右到左都相同的數字），則重複這個過程。

例如：

195 初始數字

591 反轉後的數字

—–

786 相加的和

687 反轉後的數字

—–

1473 相加的和

3741 反轉後的數字

—–

5214 相加的和

4125 反轉後的數字

—–

9339 最終的回文數

在這個例子中，回文數「9339」在第 4 次相加後出現。

這種方法對於幾乎所有的整數都能在幾步內得到回文數。

但是也有一些有趣的例外。196 是第一個尚未找到回文數的數字。然而，尚未證明不存在這樣的回文數。

你必須編寫一個程序，給出結果回文數和計算該回文數所需的迭代（相加）次數。

你可以假設本問題中的所有測試資料：

- 都會有答案，
- 都能在少於 1000 次迭代（相加）內計算出來，
- 都會產生不大於 4,294,967,295 的回文數。
- ------------------------------------------------------------------------------

The “reverse and add” method is simple: choose a number, reverse its digits and add it to the original.

If the sum is not a palindrome (which means, it is not the same number from left to right and right toleft), repeat this procedure.

For example:

195Initial number

591

—–

786

687

—–

1473

3741

—–

5214

4125

—–

9339 Resulting palindrome

In this particular case the palindrome ‘9339’ appeared after the 4th addition.

This method leadsto palindromes in a few step for almost all of the integers.

But there are interesting exceptions. 196is the first number for which no palindrome has been found. It is not proven though, that there is nosuch a palindrome.

You must write a program that give the resulting palindrome and the number of iterations (additions) to compute the palindrome.

You might assume that all tests data on this problem:

- will have an answer,
- will be computable with less than 1000 iterations (additions),
- will yield a palindrome that is not greater than 4,294,967,295.

Input

第一行將有一個數字 N（0 < N ≤ 100），表示測試案例的數量。接下來的 N 行將有一個數字 P，用來計算其回文數。

- ------------------------------------------------------------------------------

The first line will have a number N(0< N ≤ 100) with the number of test cases, the next N lines willhave a number P to compute its palindrome.

Output

對於每個 N 個測試，你需要寫一行包含以下資料：

到達回文數所需的最少迭代（相加）次數和得到的回文數，中間用一個空格分隔。

- ------------------------------------------------------------------------------

For each of the N tests you will have to write a line with the following data :

minimum number of iterations(additions) to get to the palindrome and there sulting palindrome itself separated by one space.

Sample Input 1

```
3
195
265
750

```

Sample Output 1

```
4 9339
5 45254
3 6666

```

Sample Input 2

```
5
5780
11
23365
20074
8735

```

Sample Output 2

```
2 12221
1 22
1 79697
1 67076
2 45254
```

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

#define ll long long

bool isPalin(ll n)
{
  char s[20];
  for (int i = 0; i < 20; i++)
    s[i] = '\0';
  
  int k = 0;
  bool flag = true;
  while (n != 0)
  {
    s[k++] = '0' + n % 10;
    n /= 10;
  }
  
  int len = strlen(s);
  int tmp = len / 2;
  for (int i = 0; i <= tmp; i++)
  {
    if (s[i] != s[len-i-1])
    {
      flag = false;
      break;
    }
  }
  
  return flag;
}

ll rev(ll n)
{
  ll ans = 0;
  while (n != 0)
  {
    ans = 10 * ans + n % 10;
    n /= 10;
  }
  
  return ans;
}

int main()
{
  int t;
  ll n;
  scanf("%d", &t);
  while (t--)
  {
    scanf("%lld", &n);
    int cnt = 0;
    do {
      n += rev(n);
      cnt++;
    } while (!isPalin(n));
    
    printf("%d %d\n", cnt, n);
  }

  return 0;
}
```