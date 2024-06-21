# Power Strings

Description

給定兩個字串 a 和 b，我們將它們的串聯定義為 a∗b。

例如，如果 a = 'abc' 而 b = 'def'，則 a∗b = 'abcdef'。

如果我們將串聯看作是乘法，則非負整數的指數是按照正常方式定義的：a^0 = ''（空字串），並且 a^(n+1) = a∗(a^n)。

- ------------------------------------------------------------------------------

Given two strings a and b we define a∗b to be their concatenation.

For example, if a= ‘abc’ and b= ‘def’ then a∗b= ‘abcdef’.

If we think of concatenation as multiplication, exponentiation by a non-negative integer is defined in the normal way: a^0= ‘’ (the empty string) and a^(n+1)=a∗(a^n).

Input

每個測試案例都是一行輸入，s代表可打印字元的字串。

s 的長度至少為 1，並且不會超過一萬個字元。最後一個測試案例後會跟隨一行包含句號的字符。

- ------------------------------------------------------------------------------

Each test case is a line of input representing s, a string of printable characters.

The length of s will be at least 1 and will not exceed 10 thousand characters. Aline containing a period follows the last test case.

Output

對於每個 s，您應該印出最大的 n，使得 s = a^n，其中 a 是某個字串。

- ------------------------------------------------------------------------------

For each s you should print the largest n such that s=a^n for some string a.

Sample Input 1

```
abcd
aaaa
ababab
.

```

Sample Output 1

```
1
4
3

```

Sample Input 2

```
lrbblrbblrbblrbblrbblrbblrbb
bhcdarzbhcdarzbhcdarz
kkyhidd
cdx
ybldbefybldbef
rcbynecdyrcbynecdyrcbynecdyrcbynecdyrcbynecdy
xxxxxxx
klorelklorelklorelklorelklorelklorel
mpapmpapmpapmpapmpapmpapmpapmpap
.

```

Sample Output 2

```
7
3
1
1
2
5
7
6
8
```

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <stdbool.h>

bool check(char *s, int n)
{
  int len = strlen(s);
  for (int i = n; i < len; i++)
  {
    if (*(s+i) != *(s+i-n)) return false;
  }

  return true;
}

int main()
{
  char s[1000];
  while(scanf("%s", s))
  {
    if (strcmp(s, ".") == 0) break;
    int len = strlen(s);
    for (int i = 1; i <= len; i++)
    {
      if (len % i == 0 && check(s, i))
      {
        printf("%d\n", len / i);
        break;
      }
    }
  }
  return 0;
}
```