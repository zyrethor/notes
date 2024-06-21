# Decode the Mad man

Description

在BUET的某個時刻，一位老教授完全發瘋了。他開始用一些奇怪的詞語說話。

沒有人能理解他的言語和講座。最終，BUET當局陷入了極大的困境。

再也沒有辦法讓這個人繼續在大學工作了。突然間，一位學生（肯定是UVA ACM分會的註冊作者，並且在24小時線上法官中佔有一席之地）創造了一個能夠解碼那位教授言語的程序。

在他的發明之後，每個人都恢復了安寧，那位老師也像以前一樣開始了他的日常工作。

所以，如果你曾經訪問過BUET，看到一位教師用麥克風講話，該麥克風連接到一台裝有IBM電腦和語音識別軟件的電腦，學生們從電腦屏幕上聽講，不要感到震驚！

因為現在你的任務是寫一個相同的程序來解碼那位瘋狂教師的言語！

- ------------------------------------------------------------------------------

Once in BUET, an old professor had gone completely mad.He started talking with some peculiarwords.

Nobody could realize his speech and lectures. Finally the BUET authority fall in great trouble.

There was no way left to keep that man working in university. Suddenly a student (definitely he wasa registered author at UVA ACM Chapter and hold a good rank on 24 hour-Online Judge) createda program that was able to decode that professor’s speech.

After his invention, everyone got comfortagain and that old teacher started his everyday works as before.

So, if you ever visit BUET and see a teacher talking with a microphone, which is connected to a IBM computer equipped with a voice recognition software and students are taking their lecture from the computer screen, don’t get thundered!

Because now your job is to write the same program whichcan decode that mad teacher’s speech!

Input

輸入文件將只包含一個測試案例，即編碼的訊息。

測試案例包含一個或多個單詞。

- ------------------------------------------------------------------------------

The input file will contain only one test case i.e. the encoded message.

The test case consists of one or more words.

Output

對於給定的測試案例，請印出一行包含解碼後的詞語。

然而，將每個字母或標點符號替換為其標準鍵盤上左邊兩個字母的任務並不難。

- ------------------------------------------------------------------------------

For the given test case, print a line containing the decoded words.

However, it is not so hard task to replace each letter or punctuation symbol by the two immediately to its left alphabet on your standard keyboard.

Sample Input 1

```
k[r dyt I[o

```

Sample Output 1

```
how are you
```

Sample Input 2

```
J[[g .[Y,P,j
KT''[ R[Y'G
ertdFGcVb
ERTyUioP[]
dfGHjKl;'cVB
```

Sample Output 2

```
good morning
hello world
qweasdzxc
qwertyuiop
asdfghjklzxc
```

```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>

int main()
{
  char str[10000];
  char hash[50] = "1234567890-=qwertyuiop[]\\asdfghjkl;'zxcvbnm,./";
  while (fgets(str, sizeof(str), stdin) != NULL)
  {
    str[strcspn(str, "\n")] = '\0';
    int len = strlen(str);
    for (int i = 0; i < len; i++)
    {
      int len_hash = strlen(hash);
      for (int j = 0; j < len_hash; j++)
      {
        if (isspace(str[i]))
        {
          printf(" ");
          break;
        }
        if (tolower(str[i]) == hash[j])
        {
          printf("%c", hash[j-2]);
          break;
        }
      }
    }
    
    printf("\n");
  }

  return 0;
}

```