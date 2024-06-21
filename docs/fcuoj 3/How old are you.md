# How old are you?

Description

...

- 這裡是填好的表格。
- 謝謝。讓我檢查一下...嗯...好的，好的，好的...等等，你多大了？
- 20歲。我是不是忘了填寫？
- 不是的。這裡寫著你下個月才出生！年份是錯誤的...
- 哦...抱歉！

這個過程將是自動的，為了避免一些人為的錯誤，將有一個根據當前日期和提供的出生日期計算年齡的字段。

這是你的任務，計算年齡，或者說是否有錯誤。

- ------------------------------------------------------------------------------

...

- Here are the filled form.
- Thank you. Let me check... hum... OK, OK, OK... Wait, how old are you?
- 20. Did I forget to fill it?
- No. It says here that you'll be born next month! The year is wrong...
- Oh... Sorry!

The process is going to be automatic and to avoid some human errors there will be a calculated field that informs the age based in the current date and the birth date given.

This is your task, calculatethe age, or say if there’s something wrong.

Input

輸入的第一行給出了案例數 T（1 ≤ T ≤ 200）。

T個測試案例如下。每個測試案例都以一個空行開始，然後分別是當前日期和出生日期的2行。

日期的格式為DD/MM/YYYY，其中DD是日，MM是月，YYYY是年。所有日期都將是有效的。

- ------------------------------------------------------------------------------

The first line of input gives the number of cases, T(1 ≤ T ≤ 200).

T test cases follow. Each test casestarts with a blank line, then you will have 2 lines corresponding to the current date and the birth date,respectively.

The dates are in the formatDD/MM/YYYY, whereDDis the day,MMthe monthandYYYYthe year. All dates will be valid.

Output

輸出由每個輸入資料集的一行組成，應該如下（引號僅用於澄清）：

“Case #N: AGE”，其中N是當前測試案例的編號，AGE是以下3個選項之一：

- 如果計算的年齡不可能（尚未出生），則為“無效的出生日期”。
- 如果計算的年齡超過130歲，則為“檢查出生日期”。
- 否則，為計算的年齡（僅以年為單位）。
- 如果兩個日期相同，則輸出應為“0”。
- ------------------------------------------------------------------------------

The output is comprised of one line for each input data set and should be as follow (quotes for clarifyingonly):

‘Case #N: AGE’, where N is the number of the current test case and AGE is one of the 3 followingoptions:

- ‘Invalid birth date’, if the calculated age is impossible (still going to be born).
- ‘Check birth date’, if the calculated age is more than 130.
- the calculated age(years old only), otherwise.
- If the two dates are the same, the output should be ‘0’.

Sample Input 1

```
4

01/01/2007
10/02/2007

09/06/2007
28/02/1871

12/11/2007
01/01/1984

28/02/2005
29/02/2004

```

Sample Output 1

```
Case #1: Invalid birth date
Case #2: Check birth date
Case #3: 23
Case #4: 0

```

Sample Input 2

```
5

02/01/2130
01/01/2000

01/01/2031
02/01/1900

27/02/2005
27/02/2004

01/01/2000
01/01/2001

01/01/2131
01/01/2000

```

Sample Output 2

```
Case #1: 130
Case #2: 130
Case #3: 1
Case #4: Invalid birth date
Case #5: Check birth date
```

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main()
{
  int n;
  char str[105];

  scanf("%d", &n);
  for (int z = 1; z <= n; z++)
  {
    printf("Case #%d: ", z);
    int d1, m1, y1, d2, m2, y2;
    getchar();
    scanf("%d/%d/%d", &d1, &m1, &y1);
    scanf("%d/%d/%d", &d2, &m2, &y2);

    if (y1 < y2 || (y1 == y2 && m1 < m2) || (y1 == y2 && m1 == m2 && d1 < d2))
    {
      printf("Invalid birth date\n");
      continue;
    }

    int age = 0;

    if (m1 > m2 || (m1 >= m2 && d1 >= d2))
      age = y1 - y2;
    else
      age = y1 - y2 - 1;
    
    if (age > 130)
    {
      printf("Check birth date\n");
    }
    else if (age == 0)
    {
      printf("0\n");
    }
    else
    {
      printf("%d\n", age);
    }
  }

  return 0;
}
```