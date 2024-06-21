# Continued Fractions

Description

讓b0、b1、b2、...、bn為整數，其中對於k>0，bk>0。以係數b1、b2、...、bn和初始項b0定義為n階連分數，可以表示為下列表達式，可以簡寫為[b0;b1, . . . , bn]。

![https://oj.fcu.edu.tw/public/upload/40b4d2e319.png](https://oj.fcu.edu.tw/public/upload/40b4d2e319.png)

一個n=3階連分數的例子是[2; 3, 1, 4]。這等價於

![https://oj.fcu.edu.tw/public/upload/c5fd46c540.png](https://oj.fcu.edu.tw/public/upload/c5fd46c540.png)

撰寫一個程式，將給定的有理數展開為連分數。

為確保唯一性，使bn > 1。

- ------------------------------------------------------------------------------

Letb0, b1, b2, . . . , bnbe integers withbk>0fork >0. The continued fraction of ordern with coeficientsb1, b2, . . . , bn and the initial termb0is defined by the following expressionwhich can be abbreviated as[b0;b1, . . . , bn].

![https://oj.fcu.edu.tw/public/upload/40b4d2e319.png](https://oj.fcu.edu.tw/public/upload/40b4d2e319.png)

An example of a continued fraction of order n= 3is[2; 3,1,4]. This is equivalent to

![https://oj.fcu.edu.tw/public/upload/c5fd46c540.png](https://oj.fcu.edu.tw/public/upload/c5fd46c540.png)

Write a program that determines the expansion of a given rational number as a continued fraction.

To ensure uniqueness, make bn > 1.

Input

輸入包含未確定數量的有理數。

每個有理數由兩個整數，即分子和分母來定義。

- ------------------------------------------------------------------------------

The input consists of an undetermined number of rational numbers.

Each rational number is defined by two integers, numerator and denominator.

Output

對於輸入中給定的每個有理數，您應該輸出相應的連分數。

- ------------------------------------------------------------------------------

For each rational number given in the input, you should output the corresponding continued fraction.

Sample Input 1

```
43 19
1 2

```

Sample Output 1

```
[2;3,1,4]
[0;2]

```

Sample Input 2

```
3 5
5 3
9 6
6 9
19 9

```

Sample Output 2

```
[0;1,1,2]
[1;1,2]
[1;2]
[0;1,2]
[2;9]
```

```c
#include <stdio.h>
#include <string.h>

int main()
{
  int a, b, c;
  
  while(scanf("%d %d", &a, &b) != EOF)
  {
    c = a / b;
    printf("[%d;", c);
    while (1)
    {
      int tmp = a;
      a = b;
      b = tmp % b;
      
      if (b == 1)
      {
        c = a / b;
        printf("%d]", c);
        break;
      }
      else if (b == 0)
      {
        printf("]");
        break;
      }
      else
      {
        c = a / b;
        if (a % b == 0)
          printf("%d", c);
        else
          printf("%d,", c);
      }
    }
    printf("\n");
  }
  
  
  return 0;
}
```