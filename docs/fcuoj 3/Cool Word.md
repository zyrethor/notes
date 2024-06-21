# Cool Word

Description

一個單詞是由小寫字母組成的字串。一個「酷」的單字至少有兩個不同的字母，並且每個不同字母的出現次數都不相同。

以下是正式的定義。假設 w 是一個單字，S 是單字 w 中的字母集合，那麼當且僅當所有 f(c)（對於 S 中的每個字符 c）都是不同的時候，w 就是一個「酷」單詞。

這裡的 f(c) 意味著在 w 中 c 出現的次數。

例如，字串 "ada" 是酷炫的，因為 f(a) = 2，f(d) = 1，且它們是不同的。"banana" 也是酷炫的，因為 f(a) = 3，f(n) = 2，f(b) = 1。

但是字串 "bbacccd" 不是酷炫的，因為 f(a) = f(d) = 1。一些其他有趣的酷炫字包括：mammal、needed、papaya、referee、senselessness。

讀取一系列字並計算酷炫字的數量。

- ------------------------------------------------------------------------------

A word is a string of lower-case letters. A cool word has at least 2 different letters and the number of occurrences of each different letter is different.

Here is a formal definition. Let w be a word and S be the set of letters in word w, then w is cool if and only if all f(c) (for each character c in S) is all different.

Here f(c) means the number of occurrences of c in w.

For example, the word "ada" is cool because f(a) = 2, f(d) = 1, and they're different. "banana" is also cool because f(a) = 3,f(n) = 2,f(b) = 1.

But the word "bbacccd" is not cool because f(a) = f(d) = 1.Some other interesting cool words include: mammal, needed, papaya, referee, senselessness.

Read a list of words and count the number of cool words.

Input

每個測試案例最多有 30 個測試案例。每個案例以一個整數 n (1 ≤ n ≤ 10000) 開始，表示要檢查的字數。

接下來的每一行包含一個至少包含一個字母且最多包含 30 個字母的字串。

- ------------------------------------------------------------------------------

There will be at most 30 test cases. Each case begins with an integer n(1 ≤ n ≤ 10000), the number of words to check.

Each of the following n lines contains a word containing at least one and at most 30 letters.

Output

對於每個測試案例，請印出案例編號和酷炫字的數量。

- ------------------------------------------------------------------------------

For each test case, print the case number and the number of cool words.

Sample Input 1

```
2
ada
bbacccd
2
illness
a

```

Sample Output 1

```
Case 1: 1
Case 2: 0
```

Sample Input 2

```
5
mammal
needed
papaya
referee
senselessness
4
quit
akkfffzz
wksksgggg
kkkkkkkkkkkkkkkkkkkkkkkkkkk

```

Sample Output 2

```
Case 1: 5
Case 2: 0
```

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
  
  int n;
  char str[10005];
  
  int z = 1;
  while (scanf("%d", &n) != EOF)
  {
    int cnt = 0;
    while (n--)
    {
      scanf("%s", str);
      
      int a[26] = {};
      int len = strlen(str);
      for (int i = 0; i < len; i++)
      {
        a[str[i] - 'a']++;
      }
      
      /*
      for (int i = 0; i < 26; i++)
        printf("%d ", a[i]);
      
      puts("");
      */
      
      int num = 0;
      for (int i = 0; i < 26; i++)
      {
        int tmp = 0;
        if (a[i] != tmp)
        {
          num++;
          tmp = a[i];
        }
      }
      //printf("(%d)", num);
      
      int flag = 0;
      for (int i = 0; i < 25; i++)
      {
        for (int j = i+1; j < 26; j++)
        {
          if (a[i] > 0 && a[j] > 0 && a[i] == a[j])
          {
            //printf("(%d, %d, %d, %d)", i, j, a[i], a[j]);
            flag = 1;
          }
        }
      }
      
      if (!flag && num > 1)
        cnt++;
    }
    
    
    printf("Case %d: %d\n", z++, cnt);
    
  }
  
  return 0;
}

```