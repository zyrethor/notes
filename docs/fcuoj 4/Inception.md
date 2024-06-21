# Inception

Description

Dom Cobb和他的搭檔Arthur進行非法活動，進入目標的潛意識中。他們使用兩層夢境內夢的策略來提取有價值的信息。

夢境者被突然的震驚（一種 “kick”）喚醒，或者他們可能在夢中死亡。

現在Dom需要你的幫助。因為他有一個很複雜的任務。他必須穿越許多人的夢境。

他從一個人的夢境到另一個人的夢境。他太沉迷於其中，以至於再也無法記住自己是清醒還是在別人的夢境中。

他將給你n個查詢要處理，每個查詢將以以下形式之一出現：

'SleepX' - 這意味著名為X的人將入睡，Dom將進入X的夢境，從前一個人的夢境（如果有的話）中。

'Kick' - 這意味著Dom進入的當前人物將醒來，Dom將返回到他從這個夢境來的前一個人的夢境。如果Dom不再在任何人的夢境中，請忽略此查詢。

'Test' - 這意味著Dom想知道他目前在誰的夢境中。你必須打印出這個人的名字。如果Dom目前不在任何人的夢境中，你必須印出“Not in adream”。

- ------------------------------------------------------------------------------

Dom Cobb and his partner Arthur perform illegal stuffs by entering the subconscious minds of their targets. They use two-level dream within a dream strategy to extract valuable information.

Dreamers are awakened either by a sudden shock (a “kick”), or they may die in the dream.

Now Dom wants your help. Because he has a complex assignment. He has to go through a lot of people’s dreams.

He travels from one person’s dream to another person’s dream. He is too consumed that he can no longer keep track whether he is awake or in someone else’s dream.

He will give you n queries to process, each of the queries will be in one of the following forms:

‘SleepX’— This means person named X will be sleeping and Dom is going into X’s dream, from the previous person’s dream (if any).

‘Kick’— This means the current person in whose dream Dom has entered, will be awaken, and Dom will return to the previous person’s dream from where he came to this dream. If Dom is not in anyone’s dream anymore, ignore this query.

‘Test’— This means Dom wants to know whose dream he is in at the moment. You have to print the person’s name. If Dom is not in anyone’s dream at the moment, you have to print ‘Not in adream’ (without the quotes).

Input

第一行將包含一個整數n（1 ≤ n ≤ 10000），表示查詢的數量。接下來的n行將包含上述三種查詢之一。

對於“Sleep X”查詢的情況，X將是一個由大寫或小寫字母組成且不超過15個字符長的字串。

- ------------------------------------------------------------------------------

First line will contain an integer n(1 ≤ n ≤ 10000), the number of queries. Each of the following n lines will contain one of the three queries mentioned above.

For the case of ‘Sleep X’ query, X will be a string composed of only uppercase or lowercase letters and no more than 15 characters long.

Output

對於每個 “Test” 查詢，輸出Dom目前所在夢境的人的名字，就像在輸入中出現的一樣。

如果Dom不在任何人的夢境中，輸出“Not in a dream”。詳細訊息請參考輸入樣本和輸出樣本。

- ------------------------------------------------------------------------------

For each of the ‘Test’ queries, print the name of the person whose dream Dom is in right now exactly as it appeared in the input.

If Dom is in no one’s dream, output the line ‘Not in a dream’. Check sample input and output for details.

Sample Input 1

```
20
Sleep Dom
Sleep Sakin
Test
Sleep Asif
Sleep Mushfiq
Test
Kick
Test
Sleep Shafi
Test
Kick
Test
Kick
Test
Kick
Test
Kick
Test
Kick
Test

```

Sample Output 1

```
Sakin
Mushfiq
Asif
Shafi
Asif
Sakin
Dom
Not in a dream
Not in a dream

```

Sample Input 2

```
16
Sleep Jack
Sleep John
Test
Kick
Test
Sleep Asif
Test
Test
Kick
Kick
Kick
Kick
Test
Kick
Kick
Test

```

Sample Output 2

```
John
Jack
Asif
Asif
Not in a dream
Not in a dream
```

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define LEN 16

int main() {
  int n;
  char cmd[LEN], name[LEN];
  char **stack;
  int top = -1; 

  scanf("%d", &n);
  stack = (char **) malloc(n * sizeof(char *));

  for (int i = 0; i < n; i++) {
    scanf("%s", cmd);

    if (cmd[0] == 'S') {
      scanf("%s", name);
      top++;
      stack[top] = (char *) malloc(LEN * sizeof(char));
      strcpy(stack[top], name);
    } else if (cmd[0] == 'K') {
      if (top >= 0) {
        free(stack[top]);
        top--;
      }
    } else {
      if (top == -1)
        puts("Not in a dream");
      else
        printf("%s\n", stack[top]);
    }
  }

  while (top >= 0) {
    free(stack[top]);
    top--;
  }
  free(stack);

  return 0;
}

```