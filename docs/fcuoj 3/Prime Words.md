# Prime Words

Description

質數是只有兩個因數的數字：它本身和數字一。質數的例子有：1、2、3、5、17、101和10007。

在這個問題中，你應該讀取一組單詞，每個單詞僅由範圍在a-z和A-Z之間的字母組成。

每個字母都有特定的值，字母a的值為1，字母b的值為2，依此類推，直到字母z的值為26。

同樣地，大寫字母A的值為27，字母B的值為28，大寫字母Z的值為52。你應該寫一個程式來判定一個單詞是否是一個質數單詞。

如果一個單詞的字母之和是一個質數，那麼它就是一個質數單詞。

- ------------------------------------------------------------------------------

A prime number is a number that has only two divisors: itself and the number one. Examples of primenumbers are: 1, 2, 3, 5, 17, 101 and 10007.

In this problem you should read a set of words, each word is composed only by letters in the rangea-z and A-Z.

Each letter has a specific value, the letter a is worth 1, letter b is worth 2 and so on untilletter z that is worth 26.

In the same way, letter A is worth 27, letter B is worth 28 and letter Z is worth52.You should write a program to determine if a word is a prime word or not.

A word is a prime wordif the sum of its letters is a prime number.

Input

輸入由一組單詞組成。每個單詞單獨一行，其中每個單詞包含L個字母，其中1 ≤ L ≤ 20。

輸入以文件結束符號（EOF）結束。

- ------------------------------------------------------------------------------

The input consists of a set of words. Each word is in a line by itself and has L letters, where1 ≤ L ≤ 20.

The input is terminated by end of file (EOF).

Output

對於每個單詞，如果該單詞的字母之和是一個質數，則應印出：“It is a prime word.”，否則應印出：“It is not a prime word.”。

- ------------------------------------------------------------------------------

For each word you should print: ‘It is a prime word.’, if the sum of the letters of the word is aprime number, otherwise you should print: ‘It is not a prime word.’.

Sample Input 1

```
UFRN
contest
AcM
```

Sample Output 1

```
It is a prime word.
It is not a prime word.
It is not a prime word.
```

Sample Input 2

```
a
```

Sample Output 2

```
It is a prime word.
```

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdbool.h>
#include <math.h>

bool isPrime(int n)
{
  if (n == 1)
    return true;
  
  for (int i = 2; i < n; i++)
  {
    if (n % i == 0) return false;
  }
  
  return true;
}

int main()
{
  char str[100];
  while (scanf("%s", str) != EOF)
  {
    int len = strlen(str);
    int sum = 0;
    for (int i = 0; i < len; i++)
    {
      if (str[i] >= 'a' && str[i] <= 'z')
      {
        sum += str[i] - 'a' + 1;
      }
      else if (str[i] >= 'A' && str[i] <= 'Z')
      {
        sum += str[i] - 'A' + 27;
      }
    }
    
    if (isPrime(sum))
      printf("It is a prime word.\n");
    else
      printf("It is not a prime word.\n");
  }
  
  return 0;
}
```