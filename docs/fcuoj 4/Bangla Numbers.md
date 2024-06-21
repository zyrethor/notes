# Bangla Numbers

Description

您將撰寫一個程序，使用“kuti”（10000000）、“lakh”（100000）、“hajar”（1000）、“shata”（100）來展開並將給定的數字轉換為文本。

- ------------------------------------------------------------------------------

Bangla numbers normally use ’kuti’ (10000000), ’lakh’ (100000), ’hajar’ (1000), ’shata’ (100) whileexpanding and converting to text.

You are going to write a program to convert a given number to textwith them.

Input

輸入文件可能包含多個測試案例。

每個案例將包含一個非負數字≤ 999999999999999。

- ------------------------------------------------------------------------------

The input file may contain several test cases.

Each case will contain a non-negative number≤ 999999999999999.

Output

對於每個輸入案例，您必須輸出以四位數調整開始的行，後跟轉換後的文本。

- ------------------------------------------------------------------------------

For each case of input, you have to output a line starting with the case number with four digitsadjustment followed by the converted text.

Sample Input 1

```
23764
45897458973958

```

Sample Output 1

```
   1. 23 hajar 7 shata 64
   2. 45 lakh 89 hajar 7 shata 45 kuti 89 lakh 73 hajar 9 shata 58
```

Sample Input 2

```
0
20000000000000
761000000000000
234000000003400
123456789012345
999999999999999

```

Sample Output 2

```
   1. 0
   2. 20 lakh kuti
   3. 7 kuti 61 lakh kuti
   4. 2 kuti 34 lakh kuti 3 hajar 4 shata
   5. 1 kuti 23 lakh 45 hajar 6 shata 78 kuti 90 lakh 12 hajar 3 shata 45
   6. 9 kuti 99 lakh 99 hajar 9 shata 99 kuti 99 lakh 99 hajar 9 shata 99
```

```c
#include <stdio.h>
#include <string.h>

#define ll long long

void printB(ll n)
{
  if (n >= 10000000)
  {
    printB(n/10000000);
    printf(" kuti");
    n %= 10000000;
  }
  if (n >= 100000)
  {
    printB(n/100000);
    printf(" lakh");
    n %= 100000;
  }
  if (n >= 1000)
  {
    printB(n/1000);
    printf(" hajar");
    n %= 1000;
  }
  if (n >= 100)
  {
    printB(n/100);
    printf(" shata");
    n %= 100;
  }
  if (n)
    printf(" %d", n);
}

int main()
{
  ll n;
  int k = 1;
  while(scanf("%lld", &n) != EOF)
  {
    printf("%4d.", k++);
    if (n)
      printB(n);
    else
      printf(" 0");
    printf("\n");
  }
  
  return 0;
}

```