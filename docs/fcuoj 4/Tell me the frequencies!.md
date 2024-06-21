# Tell me the frequencies!

Description

給定一行文字，你需要找出其中ASCII字元的頻率。

給定的行不包含前32個或最後128個ASCII字元中的任何一個。

當然，行可能以\n和\r結尾，但始終不考慮這些字元。

- ------------------------------------------------------------------------------

Given a line of text you will have to find out the frequencies of the ASCII characters present in it.

The given lines will contain none of the first 32 or last 128 ASCII characters.

Of course lines may end with\n and \r but always keep those out of consideration.

Input

給定多行文字作為輸入。

每一行文字都被視為單獨的輸入。

每行文字的最大長度為1000。

- ------------------------------------------------------------------------------

Several lines of text are given as input.

Each line of text is considered as a single input.

Maximum length of each line is 1000.

Output

請按照以下格式輸出ASCII字元的ASCII值及其頻率。

每組輸出之間應有一個空行。

按照它們的頻率按升序印出ASCII字元。

如果兩個字元出現次數相同，請先印出ASCII值較高的字元的訊息。

輸入以文件結束為止。

- ------------------------------------------------------------------------------

Print the ASCII value of the ASCII characters which are present and their frequency according to thegiven format below.

A blank line should separate each set of output.

Print the ASCII characters in the ascending order of their frequencies.

If two characters are present the same time print the information of the ASCII character with higher ASCII value first.

Input is terminated by end of file.

Sample Input 1

```
AAABBC
122333

```

Sample Output 1

```
67 1
66 2
65 3

49 1
50 2
51 3

```

Sample Input 2

```
CPE test is good.
9B&*^Q6lndk5y7`8`1c3

```

Sample Output 2

```
105 1
103 1
101 1
100 1
80 1
69 1
67 1
46 1
116 2
115 2
111 2
32 3

121 1
110 1
108 1
107 1
100 1
99 1
94 1
81 1
66 1
57 1
56 1
55 1
54 1
53 1
51 1
49 1
42 1
38 1
96 2
```

```c
#include <stdio.h>
#include <string.h>

int main()
{
  char s[1005];
  while (fgets(s, sizeof(s), stdin) != NULL)
  {
    s[strcspn(s, "\n")] = '\0';
    int len = strlen(s);
    int a[128] = {0};
    for (int i = 0; i < len; i++)
    {
      a[s[i]]++;
    }
    
    for (int i = 1; i <= len; i++)
    {
      for (int j = 127; j >= 32; j--)
      {
        if (a[j] == i)
          printf("%d %d\n", j, i);
      }
      
    }
    
    printf("\n");
    
  }

  return 0;
}

```