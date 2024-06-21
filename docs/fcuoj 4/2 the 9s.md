# 2 the 9s

Description

一個眾所周知的方法來判斷一個整數N是否是九的倍數，是計算其所有數字的總和S。

如果S是九的倍數，那麼N也是。這是一個遞迴的測試，獲得N的答案所需的遞迴深度被稱為N的九次方。

你的任務是，給定一個正數N，確定它是否是九的倍數，如果是的話，找出它的九次方。

- ------------------------------------------------------------------------------

A well-known trick to know if an integer N is a multiple of nine is to compute the sum S of its digits.

If S is a multiple of nine, then so is N. This is a recursive test, and the depth of the recursion needed to obtain the answer on N is called the 9-degree of N.

Your job is, given a positive number N, determine if it is a multiple of nine and, if it is, its 9-degree.

Input

輸入的文件每行包含一個正數。包含數字0的行是輸入的結束。

給定的數字最多可以包含1000位數。

- ------------------------------------------------------------------------------

The input is a file such that each line contains a positive number. A line containing the number 0 isthe end of the input.

The given numbers can contain up to 1000 digits.

Output

程式的輸出應該指示每個輸入數字是否為九的倍數，如果是的話，則顯示其九次方的值。

請參考示例輸出，了解輸出的期望格式。

- ------------------------------------------------------------------------------

The output of the program shall indicate, for each input number, if it is a multiple of nine, and in caseit is, the value of its nine-degree.

See the sample output for an example of the expected formatting ofthe output.

Sample Input 1

```
999999999999999999999
9
9999999999999999999999999999998
0

```

Sample Output 1

```
999999999999999999999 is a multiple of 9 and has 9-degree 3.
9 is a multiple of 9 and has 9-degree 1.
9999999999999999999999999999998 is not a multiple of 9.
```

Sample Input 2

```
1853020188851841
2147483647
0

```

Sample Output 2

```
1853020188851841 is a multiple of 9 and has 9-degree 2.
2147483647 is not a multiple of 9.
```

```c
#include <stdio.h>
#include <string.h>

int sumInt(int n)
{
  int sum = 0;
  while (n != 0)
  {
    sum +=  n % 10;
    n /= 10;
  }
  
  return sum;
}

int main()
{
  char s[1005];
  while (1)
  {
    // fgets(s, sizeof(s), stdin);
    scanf("%s", s);
    if (s[0] == '0' && strlen(s) == 1) break;
    // s[strcspn(s, "\n")] = '\0';
    int len = strlen(s);
    int sum = 0;
    for (int i = 0; i < len; i++)
      sum = sum + (s[i] - '0');
    
    int cnt = 1;
    if (sum % 9 != 0)
    {
      printf("%s is not a multiple of 9.\n", s);
      continue;
    }
    
    while (sum > 9)
    {
      sum = sumInt(sum);
      cnt++;
    }
    
    printf("%s is a multiple of 9 and has 9-degree %d.\n", s, cnt);
  }
}
```