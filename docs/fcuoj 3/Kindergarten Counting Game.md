# Kindergarten Counting Game

Description

每個人都坐在圓圈裡。好的。仔細聽我說。

"Woooooo, you scwewy wabbit!"

現在，有人可以告訴我我剛才說了多少個單詞嗎？

- ------------------------------------------------------------------------------

Everybody sit down in a circle. Ok. Listen to me carefully.

“Woooooo, you scwewy wabbit!”

Now, could someone tell me how many words I just said?

Input

你的程式的輸入將包含一系列行，每行包含多個單詞（至少一個）。

「單詞」被定義為一系列連續的字母（大寫 和/或 小寫）。

- ------------------------------------------------------------------------------

Input to your program will consist of a series of lines, each line containing multiple words (at least one).

A “word” is defined as a consecutive sequence of letters (upper and/or lower case).

Output

你的程式應該輸出每行輸入的單詞計數。每個單詞計數應該印在一行上。

- ------------------------------------------------------------------------------

Your program should output a word count for each line of input. Each word count should be printedon a separate line.

Sample Input 1

```
Meep Meep!
I tot I taw a putty tat.
I did! I did! I did taw a putty tat.
Shsssssssssh ... I am hunting wabbits. Heh Heh Heh Heh ...
```

Sample Output 1

```
2
7
10
9
```

Sample Input 2

```
`Tomorrow' is another day!
Are you serious?? No, I'm kidding.
Here comes a creeper. Ssssss ... BOOM!!
Note: I love Collegiate Programming Examination (CPE).
42 -- The answer to life, the universe and everything.
One

```

Sample Output 2

```
4
7
6
7
8
1
```

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

int main()
{
  char str[10000];
  while (fgets(str, sizeof(str), stdin) != NULL)
  {
    //str[strcspn(str, "\n")] = '\0';
    int len = strlen(str);
    int cnt = 0;
    
    int flag = 0; 
    for (int i = 0; i < len; i++)
    {
      if (isalpha(str[i]) && !isalpha(str[i+1]))
        cnt++;
    }
    
    printf("%d\n", cnt);
  }
  
  return 0;
}

```