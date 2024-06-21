# WERTYU

Description

常見的打字錯誤是將雙手放在鍵盤上，位置比正確位置向右偏移一排。所以「Q」被打成「W」，「J」被打成「K」，依此類推。你需要解碼以這種方式打成的訊息。

![https://oj.fcu.edu.tw/public/upload/7c5d267f3a.png](https://oj.fcu.edu.tw/public/upload/7c5d267f3a.png)

- ------------------------------------------------------------------------------

A common typing error is to place the hands on the keyboard one row to the right of the correct position. So ‘Q’ is typed as ‘W’ and ‘J’ is typed as ‘K’ and so on. You are to decode a message typed in this manner.

![https://oj.fcu.edu.tw/public/upload/e14749f78e.png](https://oj.fcu.edu.tw/public/upload/e14749f78e.png)

Input

輸入包含多行文字。每行可能包含數字、空格、大寫字母（但不包括 Q、A、Z）或上面顯示的標點符號[除了反引號（`）]。標有單字的按鍵[Tab、BackSp、Control 等]不在輸入中表示。

- ------------------------------------------------------------------------------

Input consists of several lines of text. Each line may contain digits, spaces, upper case letters (except Q, A, Z), or punctuation shown above [except back-quote (`)]. Keys labelled with words [Tab, BackSp, Control, etc.] are not represented in the input.

Output

你要將上方顯示的“QWERTY”鍵盤中的每個字母或標點符號替換為其左邊的字母或符號。輸入中的空格應在輸出中顯示。

- ------------------------------------------------------------------------------

You are to replace each letter or punction symbol by the one immediately to its left on the ‘QWERTY’ keyboard shown above. Spaces in the input should be echoed in the output.

Sample Input 1

```
O S, GOMR YPFSU/
HX\]= O8 89GD4'\P52MV,\;2EKHEPS;ISJ6L9GMBYDYPP,N9VMKIE'LT
```

Sample Output 1

```
I AM FINE TODAY.
GZ][- I7 78FS3;]O41NCM]L1WJGWOALUAH5K8FNVTSTOOMB8CNJUW;KR
```

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>

int main()
{
  char str[10000];
  char hash[50] = "`1234567890-=qwertyuiop[]\\asdfghjkl;'zxcvbnm,./";
  while (fgets(str, sizeof(str), stdin) != NULL)
  {
    str[strcspn(str, "\n")] = '\0';
    int len = strlen(str);
    for (int i = 0; i < len; i++)
    {
      int len_hash = strlen(hash);
      for (int j = 0; j < len_hash; j++)
      {
        if (isspace(str[i]))
        {
          printf(" ");
          break;
        }
        if (tolower(str[i]) == hash[j])
        {
          printf("%c", toupper(hash[j-1]));
          break;
        }
      }
    }
    
    printf("\n");
  }

  return 0;
}

```