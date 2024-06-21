# You can say 11

Description

您的工作是，給定一個正數 N，判斷它是否是十一的倍數。

- ------------------------------------------------------------------------------

Your job is, given a positive number N, determine if it is a multiple of eleven.

Input

輸入是一個文件，每一行包含一個正數。一行包含數字 '0' 標誌著輸入的結束。給定的數字可能包含多達 1000 位數字。

- ------------------------------------------------------------------------------

The input is a file such that each line contains a positive number. A line containing the number ‘0’ isthe end of the input. The given numbers can contain up to 1000 digits.

Output

程式的輸出應該指示對於每個輸入數字，它是否是十一的倍數。

- ------------------------------------------------------------------------------

The output of the program shall indicate, for each input number, if it is a multiple of eleven or not.

Sample Input 1

```
112233
30800
2937
323455693
5038297
112234
0
```

Sample Output 1

```
112233 is a multiple of 11.
30800 is a multiple of 11.
2937 is a multiple of 11.
323455693 is a multiple of 11.
5038297 is a multiple of 11.
112234 is not a multiple of 11.
```

Sample Input 2

```
0011
00011
030800
0
```

Sample Output 2

```
0011 is a multiple of 11.
00011 is a multiple of 11.
030800 is a multiple of 11.
```

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

int main()
{
  char str[1200];
  
  while (1)
  {
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';
    int len = strlen(str);
    if (len == 1 && str[0] == '0') break;
    
    int sum1 = 0;
    int sum2 = 0;
    for (int i = 0; i < len; i+=2)
    {
      sum1 += str[i] - '0';
    }
    
    for (int i = 1; i < len; i+=2)
    {
      sum2 += str[i] - '0';
    }
    
    int total = abs(sum1 - sum2);
    const char* s = str;
    if (total % 11 == 0)
      printf("%s is a multiple of 11.\n", s);
    else
      printf("%s is not a multiple of 11.\n", s);
      
  }
  
  return 0;
}

```