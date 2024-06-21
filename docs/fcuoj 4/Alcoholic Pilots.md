# Alcoholic Pilots

Description

在一次旅行中，艾德先生登上一架飛機，機長說話的方式……嗯，就像他完全喝醉了一樣。

「我想向這裡的一位非常特別的人致意，他一直是我們生活的一部分。他的妻子從控制塔說她愛你。」機長說道。

當然，艾德先生真的很害怕，怎麼會有酒精中毒的飛行員駕駛這麼多人的飛機呢？

但這還不是最糟糕的部分，我們的朋友注意到這些喝醉的飛行員喜歡互相賽車！

靠近機長艙，艾德先生聽到另一名飛行員（果然也是喝醉了）通過無線電與機長討論。

他們都分享了他們的飛行速度和到最近機場的距離。

「如果我先到達機場，你就欠我一杯啤酒。」機長吹噓道，然後飛機開始突然移動。

當然，艾德先生活了下來，否則他就不能告訴我們這個故事了。

但奇怪的是，你想知道這兩個飛行員之間誰贏得了比賽，以及他們的平均到達時間，所以你問了他們飛行速度和到機場的距離。

假設飛機在降落時保持速度不變。

- ------------------------------------------------------------------------------

In one of his many trips, Mr. Ed boarded an airplane where the captain talked like... well, like he wascompletely drunk.

“I would like to greet a very special person here, which has been part of our lives forso much time. His wife says from the control tower that she loves you” — the captain said.

Of course,Mr. Ed was really scared, how can alcoholic pilots flight with so many people on their hands?

But thatwas not the worst part, our friend noticed that these drunken pilots like to race between them!

By getting close to the captain’s cabin, Mr. Ed could hear another pilot (drunk, as expected)discussing with the captain by radio.

Both of them shared information about how fast they weretravelling and how far they were to the nearest airport.

“If I arrive earlier to the airport, you will oweme a beer” — the captain bragged, then the airplane started to move abruptly.

Of course Mr. Ed survived, if not, he could not tell us this story.

But weirdly, you are wonderingwho won the race between the pilots and their average arrival time, so you asked the velocity anddistance to the airport of both planes.

Assume that the planes maintained their velocity even whenlanding.

Input

輸入包含多組測試案例。

每個測試案例的唯一一行包含四個用空格分隔的整數 v1、d1、v2 和 d2（1 ≤ v1, d1, v2, d2 ≤ 10^9）：

分別是艾德先生所乘坐的飛機的速度和到機場的距離，以及機長競賽的飛機的速度和到機場的距離。

速度以每小時英里表示，距離以英里表示。

最後一組測試案例之後，會有一行包含四個零。

- ------------------------------------------------------------------------------

The input will contain several test cases.

The only line of each test case contains 4 space-separatedintegersv1,d1,v2 and d2(1≤v1, d1, v2, d2 ≤ 10^9):

the velocity and distance to the airport of the planeMr. Ed and the captain were and the velocity and distance to the airport of the plane the captain wascompeting with.

Velocities are expressed in miles per hour and distances in miles.

The last test case is followed by a single line containing 4 zeroes.

Output

對於每個測試案例，輸出兩行。第一行應該打印「You owe me a beer!」如果機長贏得比賽，或者打印「No beer for the captain.」如果另一架飛機贏得比賽。

你可以放心地假設在任何測試案例中都不會有平局。

在第二行，打印「Avg. arrival time: 」後跟兩架飛機的平均到達時間（以小時為單位），表達為簡化的分數形式「x/y」，其中x和y是整數。

如果分數結果是整數，則打印整數結果。請參見下面的格式以獲取更多詳細信息。

- ------------------------------------------------------------------------------

Print 2 lines for each test case. In the first one, you should print ‘You owe me a beer!’ if the captainwon the race or ‘No beer for the captain.’

if the other airplane won the race.

You can safely assume there will be no draws in any test case.

In the second line, print ‘Avg. arrival time: ’followed by the average arrival time (in hours)of both airplanes expressed as a simplified fraction of the form ‘x/y’, being x and y integers.

If thefraction has an integer result, print the result of the division. See format below for more details.

Sample Input 1

```
2 4 1 3
1 3 2 4
4 7 4 9
0 0 0 0

```

Sample Output 1

```
Case #1: You owe me a beer!
Avg. arrival time: 5/2
Case #2: No beer for the captain.
Avg. arrival time: 5/2
Case #3: You owe me a beer!
Avg. arrival time: 2

```

Sample Input 2

```
2 4 3 12
3 5 5 3
7 3 3 7
12 7 8 9
0 0 0 0

```

Sample Output 2

```
Case #1: You owe me a beer!
Avg. arrival time: 3
Case #2: No beer for the captain.
Avg. arrival time: 17/15
Case #3: You owe me a beer!
Avg. arrival time: 29/21
Case #4: You owe me a beer!
Avg. arrival time: 41/48
```

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

#define ull unsigned long long

ull gcd(ull a, ull b)
{
  if (a == 0)
    return b;
  
  return gcd(b%a, a);
}

int main()
{
  ull v1, d1, v2, d2;
  int z = 1;
  while (1)
  {
    scanf("%llu %llu %llu %llu", &v1, &d1, &v2, &d2);
    if (v1 == 0 && d1 == 0 && v2 == 0 && d2 == 0) break;
    
    
    ull num = v1 * d2 + v2 * d1;
    ull deno = v1 * v2 * 2;
    ull g = gcd(num, deno);
    num /= g;
    deno /= g;
      
    printf("Case #%d: ", z++);
    ull a = d1 * v2;
    ull b = d2 * v1;
    if (a < b)
      printf("You owe me a beer!\n");
    else
      printf("No beer for the captain.\n");
    
    if (num % deno == 0)
      printf("Avg. arrival time: %llu\n", num/deno);
    else
      printf("Avg. arrival time: %llu/%llu\n", num, deno);
  }
  
  return 0;
}

```