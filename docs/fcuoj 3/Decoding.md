# Decoding

Description

編碼是將信息從一種格式轉換為另一種格式的過程。

存在幾種不同類型的編碼方案。在這個問題中，我們將討論一種非常簡單的編碼技術；稱為 Run-Length Encoding。

Run-Length Encoding 是一種非常簡單和易於理解的資料壓縮形式，其中相同字符的連續出現被替換為一個字符後跟其頻率。

例如，字符串 'AABBBDAA' 將被編碼為 'A2B4D1A2'，引號用於澄清。

在這個問題中，我們感興趣的是解碼使用上述程序編碼的字符串。

- ------------------------------------------------------------------------------

Encoding is the process of transforming information from one format into another.

There exist severaldifferent types of encoding scheme. In this problem we will talk about a very simple encoding technique;Run-Length Encoding.

Run-length encoding is a very simple and easy form of data compression in which consecutiveoccurrences of the same characters are replaced by a single character followed by its frequency.

As anexample, the string `AABBBBDAA' would be encoded to `A2B4D1A2', quotes for clarity.

In this problem, we are interested in decoding strings that were encoded using the above procedure.

Input

輸入的第一行是一個整數 T（T < 50），表示測試案例的數量。

每個案例是一行包含編碼字符串的行。該字符串將僅包含數字 [0-9] 和字母 [A-Z]。

每個輸入的字符串都將是有效的。也就是說，每個字母後面都會跟著一個或多個數字。

- ------------------------------------------------------------------------------

The first line of input is an integer T(T <50) that indicates the number of test cases.

Each case isa line consisting of an encoded string. The string will contain only digits [0-9] and letters [A-Z].

Everyinputted string will be valid. That is, every letter will be followed by 1 or more digits.

Output

對於每個案例，輸出案例編號，後跟解碼後的字符串。請按照示例的精確格式進行操作。

您可以假設解碼後的字符串長度不會超過 200，並且它只會包含大寫字母。

- ------------------------------------------------------------------------------

For each case, output the case number followed by the decoded string. Adhere to the sample for exactformat.

You may assume the decoded string wont have a length greater than 200 and it will only consist ofupper case alphabets.

Sample Input 1

```
3
A2B4D1A2
A12
A1B1C1D1
```

Sample Output 1

```
Case 1: AABBBBDAA
Case 2: AAAAAAAAAAAA
Case 3: ABCD
```

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>
#include <math.h>

int main()
{
  int cs;
  scanf("%d", &cs);
  getchar();
  char str[10000];
  
  for (int z = 1; z <= cs; z++)
  {
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';
    int len = strlen(str);
    
    int num = 0;
    printf("Case %d: ", z);
    for (int i = 0; i < len; i++)
    {
      char ch;
      if (isalpha(str[i]))
        ch = str[i];
      
      if (isdigit(str[i]))
      {
        if (num > 0)
          num = num * 10 + (str[i] - '0');
        else
          num = (str[i] - '0');
      }
      
      if (isdigit(str[i]) && !isdigit(str[i+1]))
      {
        for (int j = 0; j < num; j++)
          printf("%c", ch);
        num = 0;
      }
    }
    
    printf("\n");
    
  }
  
  return 0;
}

```

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>
#include <stdbool.h>
#include <ctype.h>

int main()
{
	char str[205];
	int n;
	int cnt;
	scanf("%d", &n);
	for (int z=1; z<=n; z++)
	{
		scanf("%s", str);
		printf("Case %d: ", z);
		int len = strlen(str);
		for (int i = 0; i < len; i++)
		{
			if (isalpha(str[i]))
			{
				char ch = str[i];
				cnt = 0;

				while (isdigit(str[++i]))
				{
					cnt = 10 * cnt + (str[i] - '0');
				}
				i--;

				for (int j = 0; j < cnt; j++)
					printf("%c", ch);
			}
		}
		printf("\n");
	}
	
	return 0;
}
```