# Marvelous Mazes

Description

如果你決定接受，你的任務是創建一個迷宮繪製程序。迷宮將由字母 A-Z、星號（*）和空格組成。

- ------------------------------------------------------------------------------

Your mission, if you decide to accept it, is to create a maze drawing program. A maze will consist of the alphabetic characters A-Z,*(asterisk), and spaces.

Input

你的程式將從輸入文件中獲取迷宮的信息。該文件將包含一系列字符行，你的程式必須解釋這些行以繪製一個迷宮。

迷宮的每一行將由一系列數字和字符描述，其中數字表示該字符將被使用的次數。

如果在字符前面有多個數字，則該字符重複的次數將是該字符前面數字的總和。

小寫字母 'b' 將在輸入文件中用於表示迷宮中的空格。

迷宮中不同行的描述將由驚嘆號（!）或行尾分隔。

不同迷宮的描述將由一個空行分隔。輸入文件將以文件結尾結束。

- ------------------------------------------------------------------------------

Your program will get the information for the mazes from the input file. This file will contain lines ofcharacters which your program must interpret to draw a maze.

Each row of the maze will be describedby a series of numbers and characters, where the numbers before a character tell how many times thatcharacter will be used.

If there are multiple digits in a number before a character, then the number oftimes to repeat the character is the sum of the digits before that character.

The lowercase letter ‘b’ will be used in the input file to represent spaces in the maze.

The descriptionsfor different rows in the maze will be separated by an exclamation point (!), or by an end of line.

Descriptions for different mazes will be separated by a blank line. The input file will be terminatedby an end of file.

Output

對於輸入文件中的每個描述，請根據下面的示例輸出繪製相應的迷宮。

迷宮中的行數或文件中的迷宮數量沒有限制，但是沒有一行會包含超過 132 個字符。在兩個連續的迷宮之間打印一個空行。

祝你玩得開心！

- ------------------------------------------------------------------------------

For each description in the input file, draw the corresponding maze as it is shown in the sample outputbelow.

There is no limit to the number of rows in a maze or the number of mazes in a file, though norow will contain more than 132 characters.Print a blank line between two consecutive mazes.

Happy mazing!

Sample Input 1

```
1T1b5T!1T2b1T1b2T!1T1b1T2b2T!1T3b1T1b1T!3T3b1T!1T3b1T1b1T!5T1*1T

11X21b1X
4X1b1X
```

Sample Output 1

```
T TTTTT
T  T TT
T T  TT
T   T T
TTT   T
T   T T
TTTTT*T

XX   X
XXXX X

```

Sample Input 2

```
1111111111111111111111111111111111111111X

```

Sample Output 2

```
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
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
    int len = strlen(str);
    
    int num = 0;
    for (int i = 0; i < len; i++)
    {
      if (str[i] == '!' || str[i] == '\n')
      {
        printf("\n");
        continue;
      }
      
      char ch;
      if (isalpha(str[i]))
        ch = str[i];
      
      if (str[i] == 'b')
        ch = ' ';
      
      if (str[i] == '*')
      {
        ch = '*';
      }
      
      if (isdigit(str[i]))
      {
        num += (str[i] - '0');
      }
      
      if ((isalpha(str[i]) || str[i] == '*') && !isalpha(str[i+1]))
      {
        for (int j = 0; j < num; j++)
          printf("%c", ch);
        num = 0;
      }
    }
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
	char str[200];
	while (fgets(str, sizeof(str), stdin) != NULL)
	{
		str[strcspn(str, "\n")] = '\0';
		int len = strlen(str);
		
		int n = 0;

		for (int i = 0; i < len; i++)
		{
			if (isdigit(str[i]))
				 n += str[i] - '0';
			else if (str[i] == '!')
				printf("\n");
			else if (str[i] == 'b')
			{
				for (int j = 0; j < n; j++)
					printf(" ");
				n = 0;
			}
			else if (isalpha(str[i]) || str[i] == '*')
			{
				for (int j = 0; j < n; j++)
					printf("%c", str[i]);
				n = 0;
			}
		}

		printf("\n");
	}
	
	return 0;
}
```