# Group Reverse

Description

將一個字符串進行分組反轉意味着將字符串按組進行反轉。例如，考慮一個字符串：

“**TOBENUMBERONEWEMEETAGAINANDAGAINUNDERBLUEICPCSKY**”

該字符串的長度為48。我們將其分成8個等長的組，因此每個組的長度為6。

現在，我們可以將這八個組中的每一個進行反轉，得到一個新的字符串：

“**UNEBOTNOREBMEEMEWENIAGATAGADNAEDNUNIIEULBRYKSCPC**”

給定字符串和其中的組數，您的程序將需要對其進行分組反轉。

- ------------------------------------------------------------------------------

Group reversing a string means reversing a string by groups. For example consider a string:

“**TOBENUMBERONEWEMEETAGAINANDAGAINUNDERBLUEICPCSKY**”

This string has length 48. We have divided into 8 groups of equal length and so the length of eachgroup is 6.

Now we can reverse each of these eight groups to get a new string:

“**UNEBOTNOREBMEEMEWENIAGATAGADNAEDNUNIIEULBRYKSCPC**”

Given the string and number of groups in it, your program will have to group reverse it.

Input

輸入文件包含最多101行輸入。

每行包含一個整數G（G < 10），表示組數，後跟一個字串，其長度是G的倍數。

字串的長度不大於100。

字串僅包含字母數字。

輸入以包含一個零的行結束。

- ------------------------------------------------------------------------------

The input file contains at most 101 lines of inputs.

Each line contains at integer G(G < 10) which denotes the number of groups followed by a string whose length is a multiple of G.

The length of the string is not greater than 100.

The string contains only alpha numerals.

Input is terminated by a line containing a single zero.

Output

對於每一行輸入，產生一行輸出，其中包含分組反轉後的字符串。

- ------------------------------------------------------------------------------

For each line of input produce one line of output which contains the group reversed string.

Sample Input 1

```
3 ABCEHSHSH
5 FA0ETASINAHGRI0NATWON0QA0NARI0
0

```

Sample Output 1

```
CBASHEHSH
ATE0AFGHANISTAN0IRAQ0NOW0IRAN0

```

Sample Input 2

```
1 A
8 EFUIEHVOAUCQWNCNWVBNXDAHCBWBGIWX
7 AAAAAAABBBBBBBCCCCCCCDDDDDDDEEEEEEE
9 ASDFASDFA
0

```

Sample Output 2

```
A
IUFEOVHEQCUANCNWNBVWHADXBWBCXWIG
AAAAABBBAACBBBBCCCCCDDDDCEEDDDEEEEE
ASDFASDFA
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

  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    scanf("%s", str);

    int len = strlen(str);
    int g = len / n;

    for (int i = 0; i < len; i+=g)
    {
      for (int j = i+g-1; j >= i; j--)
        printf("%c", str[j]);
    }

    printf("\n");
  }
  
  return 0;
}
```