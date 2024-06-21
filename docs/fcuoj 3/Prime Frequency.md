# Prime Frequency

Description

給定一個只包含字母數字（0-9、A-Z 和 a-z）的字串，你需要計算所有字元的出現頻率（即該字元出現的次數），並輸出只有出現頻率是質數的字元。

質數是一個僅能被兩個不同整數整除的數字。一些質數的例子有2、3、5、7、11等。

![https://oj.fcu.edu.tw/public/upload/79a9b10fe9.png](https://oj.fcu.edu.tw/public/upload/79a9b10fe9.png)

- ------------------------------------------------------------------------------

Given a string containing only alpha-numerals (0-9,A-Zand a-z) you have to count the frequency (the number of times the character is present) of all the characters and report only those characters whose frequency is a prime number.

A prime number is a number, which is divisible by exactly two different integers. Some examples of prime numbers are2,3,5,7,11etc.

![https://oj.fcu.edu.tw/public/upload/ee3545f121.png](https://oj.fcu.edu.tw/public/upload/ee3545f121.png)

Input

輸入的第一行是一個整數 T（0 < T < 201），表示有多少組輸入。

接下來的每一行（共 T 行）包含一組輸入。

每個測試集的輸入是一個僅包含字母數字的字串。

這個字串的長度為正數，小於 2001。

- ------------------------------------------------------------------------------

The first line of the input is an integer T(0< T <201)that indicates how many sets of inputs are there.

Each of the next T lines contains a single set of input.

The input of each test set is a string consisting alpha-numerals only.

The length of this string is positive and less than 2001.

Output

對於每組輸入，產生一行輸出。這一行包含輸出的序號，後面跟著在輸入字串中頻率是質數的字元。

這些字元應按字母表順序升序排列。這裡的「字母表升序」指的是按ASCII值升序排列。

請參考示例輸入的輸出以獲取詳細信息。如果沒有字元的頻率是質數，則應該打印“empty”（不帶引號）。

- ------------------------------------------------------------------------------

For each set of input produce one line of output. This line contains the serial of output followed by thecharacters whose frequency in the input string is a prime number.

These characters are to be sorted inlexicographically ascending order. Here “lexicographically ascending” means ascending in terms of theASCII values.

Look at the output for sample input for details. If none of the character frequency is aprime number, you should print ‘empty’ (without the quotes) instead.

Sample Input 1

```
3
ABCC
AABBBBDDDDD
ABCDFFFF

```

Sample Output 1

```
Case 1: C
Case 2: AD
Case 3: empty
```

Sample Input 2

```
3
AABBabba
10223782327absasAABBCDDD
1282sasAAB3921299972

```

Sample Output 2

```
Case 1: ABab
Case 2: 37ABDas
Case 3: 12As
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
#include <stdbool.h>

bool isPrime(int n)
{
  if (n <= 1)
    return false;
    
  int sqrtN = sqrt(n);
  for (int i = 2; i <= sqrtN; i++)
  {
    if (n % i == 0)
      return false;
  }
  
  return true;
}

int main()
{
  
  int n;
  scanf("%d", &n);
  char str[2005];
  
  for (int z = 1; z <= n; z++)
  {
    // 10 + 26 + 26
    int a[62] = {};
    
    scanf("%s", str);
    
    int len = strlen(str);
    for (int i = 0; i < len; i++)
    {
      if (isdigit(str[i]))
      {
        //printf("(%c)", str[i]);
        a[str[i] - '0']++;
      }
      
      if (str[i] >= 'A' && str[i] <= 'Z')
      {
        a[str[i] - 'A' + 10]++;
      }
      
      if (str[i] >= 'a' && str[i] <= 'z')
      {
        a[str[i] - 'a' + 36]++;
      }
    }
    
    /*
    for (int i = 0; i < 62; i++)
      printf("%d ", a[i]);
    */
    
    printf("Case %d: ", z);
    
    int cnt = 0;
    for (int i = 0; i < 62; i++)
    {
      if (isPrime(a[i]))
      {
        //printf("(%d, %d)", i, a[i]);
        cnt++;
        if (i <= 9)
          printf("%d", i);
          
        if (i >= 10 && i < 36)
        {
          printf("%c", 'A' + i - 10);
        }
        
        if (i >= 36 && i < 62)
        {
          printf("%c", 'a' + i - 36);
        }
      }
    }
    
    if (cnt == 0)
      printf("empty");
    
    printf("\n");
  }
  
  return 0;
}

```