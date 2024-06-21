# Rotating Sentences

Description

在“旋轉句子”中，你需要將一系列輸入的句子順時針旋轉90度。

因此，程式不會將輸入的句子從左到右、從上到下顯示，而是會從上到下、從右到左顯示。

- ------------------------------------------------------------------------------

In “Rotating Sentences,” you are asked to rotate a series of input sentences 90 degrees clockwise.

Soinstead of displaying the input sentences from left to right and top to bottom, your program will displaythem from top to bottom and right to left.

Input

作為程式的輸入，你將收到最多100個句子，每個句子不超過100個字符長。

合法字符包括：換行符、空格、任何標點符號、數字以及小寫或大寫的英文字母。（注意：Tabs不是合法字符。）

- ------------------------------------------------------------------------------

As input to your program, you will be given a maximum of 100 sentences, each not exceeding 100characters long.

Legal characters include: newline, space, any punctuation characters, digits, and lowercase or upper case English letters. (NOTE: Tabs are not legal characters.)

Output

程式的輸出應該將最後一個句子以垂直方式顯示在最左邊的列；

而輸入的第一個句子則最終出現在最右邊的列。

- ------------------------------------------------------------------------------

The output of the program should have the last sentence printed out vertically in the leftmost column;

the first sentence of the input would subsequently end up at the rightmost column.

Sample Input 1

```
Rene Decartes once said,
"I think, therefore I am."

```

Sample Output 1

```
"R
Ie
 n
te
h
iD
ne
kc
,a
 r
tt
he
es
r
eo
fn
oc
re
e
 s
Ia
 i
ad
m,
.
"
```

```c
#include <stdio.h>
#include <string.h>

int main()
{
  char str[105][105];
  int index = 0;
  int max = 0;

  while (fgets(str[index], 105, stdin))
  {
    str[index][strcspn(str[index], "\n")] = '\0';
    int len = strlen(str[index]);
    if (max < len)
      max = len;

    index++;
  }

  int i, j;
  for (i = 0; i < max; i++)
  {
    for (j = index - 1; j >= 0; j--)
    {
      if (strlen(str[j]) > i)
        printf("%c", str[j][i]);
      else
        printf(" ");
    }
    printf("\n");
  }

  return 0;
}

```