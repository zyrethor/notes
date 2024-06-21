# Age Sort

Description

您獲得了一個國家中所有至少1歲以上人們的年齡（以年為單位）。

您知道該國沒有任何人的壽命會達到或超過100歲。

現在，您的任務非常簡單，就是將所有的年齡按照升序排列。

- ------------------------------------------------------------------------------

You are given the ages (in years) of all people of a country with at least 1 year of age.

You know that no individual in that country lives for 100 or more years.

Now, you are given a very simple task of sorting all the ages in ascending order.

Input

輸入檔案中有多個測試案例。

每個案例開始於一個整數 n（0 < n ≤ 2000000），代表人數總數。

在下一行中，有 n 個整數表示年齡。

當遇到 n = 0 的情況時，輸入終止。這個情況不應該被處理。

- ------------------------------------------------------------------------------

There are multiple test cases in the input file.

Each case starts with an integer n (0< n ≤ 2000000), the total number of people.

In the next line, there are n integers indicating the ages.

Input is terminated with a case where n = 0.This case should not be processed.

Output

對於每個案例，請輸出一行包含 n 個用空格分隔的整數。這些整數是該國人民的年齡，並且已按升序排序。

- ------------------------------------------------------------------------------

For each case, print a line with n space separated integers. These integers are the ages of that country sorted in ascending order.

Sample Input 1

```
5
3 4 2 1 5
5
2 3 2 3 1
0
```

Sample Output 1

```
1 2 3 4 5
1 2 2 3 3
```

```c
#include <stdio.h>

void bubble(int a[], int n)
{
  for (int i = 0; i < n; i++)
  {
    for (int j = 0; j < n-1-i; j++)
    {
      if (a[j] > a[j+1])
      {
        int tmp = a[j];
        a[j] = a[j+1];
        a[j+1] = tmp;
      }
    }
  }
}

int main()
{
  int a[2000005] = {};
  int n;
  
  while (1)
  {
    scanf("%d", &n);
    if (n == 0) break;
    for (int i = 0; i < n; i++)
      scanf("%d", &a[i]);
      
    bubble(a, n);
    
    for (int i = 0; i < n; i++)
      printf("%d%s", a[i], i == n-1 ? "\n" : " ");
  }

  return 0;
}
```