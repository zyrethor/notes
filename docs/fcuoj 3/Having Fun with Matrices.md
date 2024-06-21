# Having Fun with Matrices

Description

我們有一個大小為 N x N 的矩陣。矩陣中的每個值佔據範圍 [0, 9] 內的整數。

將對這個矩陣進行一些操作。我們想知道在這些操作按順序執行後，矩陣的樣子如何。

可能有五種不同類型的操作。

row a b

在此操作中，將第 a 列與第 b 列互換。

col a b

在此操作中，將第 a 行與第 b 行互換。

inc

在此操作中，每個單元格的值增加 1（取模 10）。也就是說，如果增加 1 後，單元格的值變為 10，我們將其改為 0。

dec

在此操作中，每個單元格的值減少 1（取模 10）。也就是說，如果減去 1 後，單元格的值變為 -1，我們將其改為 9。

transpose

在此操作中，我們只是將矩陣進行轉置。轉置一個矩陣，表示將給定矩陣的所有列變為行，反之亦然。

範例：

1 2 3             1 4 7

4 5 6 轉置後 2 5 8

7 8 9             3 6 9

- ------------------------------------------------------------------------------

We have a matrix of size N x N. Each value of the matrix occupies an integer from[0,9].

A few operations are going to be performed on this matrix. We would like to know how the matrix looks like after these operations are performed sequentially.

There could be five different types of operations.

row a b

In this operation, row a is interchanged with row b.

col a b

In this operation, column a is interchanged with column b.

inc

In this operation, every cell value is increased by 1 (modulo 10). That is, if after adding 1, a cellvalue becomes 10 we change it to 0.

dec

In this operation, every cell value is decreased by 1 (modulo 10). That is, if after subtracting 1, acell value becomes -1 we change it to 9.

transpose

In this operation, we simply transpose the matrix. Transposing a matrix, denoted by AT, meansturning all the rows of the given matrix into columns and vice-versa.

Example:

1 2 3                             1 4 7

4 5 6 after transposing 2 5 8

7 8 9                             3 6 9

Input

輸入文件以一個整數 T (T < 50) 開始，表示測試案例的數量。

每個案例以一個正整數 N (N < 10) 開始，表示矩陣的大小。

接下來的 N 行包含 N 個整數，每個整數的值在範圍 [0, 9] 內。

接下來是一行包含一個整數 M (M < 50)。接下來的 M 行包含每個操作。

如果命令是 'row a b' 或 'col a b'，則可以假設 1 ≤ a, b ≤ N，且 a ≠ b。

- ------------------------------------------------------------------------------

The input file starts with an integer T(T <50)that indicates the number of test cases.

Each case starts with a positive integer N(N <10)that represents the size of the matrix.

The next N lines contain N integers each. The value of each integer is in the range[0,9].

Next there is a line with an integer M(M <50). Each of the next M lines contain an operation each.

If the command is ‘row a b’ or ‘col a b’, then you can assume1≤a, b≤N and a̸= b.

Output

對於每個案例，請在第一行輸出案例編號。然後在接下來的N行中輸出最終矩陣的內容。

在每個案例之後請打印一個空行（即使在最後一個案例之後也要如此）。

- ------------------------------------------------------------------------------

For each case, output the case number on the first line. Then on the next N lines output the contentof the final matrix.

Print a blank line after each case (even after the very last one).

Sample Input 1

```
2
4
1234
5678
1234
5678
1
transpose
3
000
111
000
2
row 1 2
inc
```

Sample Output 1

```
Case #1
1515
2626
3737
4848

Case #2
222
111
111
```

```c
#include <stdio.h>
#include <string.h>

int main()
{
  int cs;
  int *pcs = &cs;
  scanf("%d", pcs);

  for (int z = 1;  z <= *pcs; z++)
  {
    int n;
    int *pn = &n;
    scanf("%d", pn);
    int mat[*pn][*pn];
    int (*pmat)[*pn] = mat;

    char str[20];
    char *pstr = str;

    for (int i = 0; i < *pn; i++)
    {
      scanf("%s", pstr);
      for (int j = 0; j < strlen(pstr); j++)
      {
        if (*(pstr+j) >= '0' && *(pstr+j) <= '9')
          *(*(pmat + i) + j) = *(pstr+j) - '0';
      }
    }

    int ops;
    int *pops = &ops;
    scanf("%d", pops);
    getchar();
    
    // puts("Original:");
    // for (int i = 0; i < n; i++)
    // {
    //   for (int j = 0; j < n; j++)
    //     printf("%d ", *(*(pmat + i) + j));
    //   printf("\n");
    // }
    // puts("");

    while ((*pops)--)
    {
      char op[20];
      char *pop = op;
      fgets(pop, 20, stdin);
      *(pop + strcspn(pop, "\n")) = '\0';

      int tmp;
      int *ptmp = &tmp;
      if (strcmp(pop, "transpose") == 0)
      {
        for (int i = 0; i < *pn; i++)
        {
          for (int j = i+1; j < *pn; j++)
          {
            *ptmp = *(*(mat + i) + j);
            *(*(mat + i) + j) = *(*(mat + j) + i);
            *(*(mat + j) + i) = *ptmp;
          }
        }
      }

      if (strcmp(pop, "inc") == 0)
      {
        for (int i = 0; i < *pn; i++)
        {
          for (int j = 0; j < *pn; j++)
            *(*(mat + i) + j) = (*(*(mat + i) + j) + 1) % 10;
        }
      }
      
      if (strcmp(pop, "dec") == 0)
      {
        for (int i = 0; i < *pn; i++)
        {
          for (int j = 0; j < *pn; j++)
          {
            *(*(mat + i) + j) -= 1;
            if (*(*(mat + i) + j) == -1)
              *(*(mat + i) + j) = 9;
          }
        }
      }

      int a, b;
      int *pa = &a, *pb = &b;
      if (sscanf(pop, "row %d %d", pa, pb))
      {
        (*pa)--;
        (*pb)--;
        for (int i = 0; i < *pn; i++)
        {
          *ptmp = *(*(mat + a) + i);
          *(*(mat + a) + i) = *(*(mat  + b) + i);
          *(*(mat + b) + i) = *ptmp;
        }
      }
      
      if (sscanf(pop, "col %d %d", pa, pb))
      {
        (*pa)--;
        (*pb)--;
        for (int i = 0; i < *pn; i++)
        {
          *ptmp = *(*(mat + i) + a);
          *(*(mat + i) + a) = *(*(mat  + i) + b);
          *(*(mat + i) + b) = *ptmp;
        }
      }
    }

    printf("Case #%d\n", z);
    for (int i = 0; i < n; i++)
    {
      for (int j = 0; j < n; j++)
        printf("%d", *(*(pmat + i) + j));
      printf("\n");
    }
    printf("\n");
  }
  

  return 0;
}

```