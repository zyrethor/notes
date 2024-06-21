# Can You Solve It?

Description

首先，看一下以下的圖片。在這張圖片中，每個圓都有一個根據笛卡兒座標系統的座標。

你可以沿著由向前箭頭符號表示的路徑從一個圓移到另一個圓。要從來源圓到目的地圓，

所需的總步數 = 你經過的中間圓的數量 + 1

例如，從 (0,3) 到 (3,0) 你必須經過兩個中間圓 (1,2) 和 (2,1)。

所以，在這個情況下，所需的總步數是 2 + 1 = 3。在這個問題中，你要計算給定來源圓和目的地圓之間所需的步數。

你可以假設，不能使用箭頭的反向方向返回。

![https://oj.fcu.edu.tw/public/upload/cf4ad471bc.png](https://oj.fcu.edu.tw/public/upload/cf4ad471bc.png)

- ------------------------------------------------------------------------------

First take a look at the following picture.In this picture, each circle has a coordinate according toCartesian Coordinate System.

You can move from one circle to another following the path denoted byforward arrow symbols. To go from a source circle to a destination circle,

total_number_of_step(s)_needed=number_of_intermediate_circles_you_pass+ 1

For example, to go from(0,3)to(3,0)you have to pass two intermediate circles(1,2)and(2,1).

So,in this case, total number of steps needed is2 + 1 = 3. In this problem, you are to calculate number ofstep(s) needed for a given source circle and a destination circle.

You can assume that, it is not possibleto go back using the reverse direction of the arrows.

![https://oj.fcu.edu.tw/public/upload/cf4ad471bc.png](https://oj.fcu.edu.tw/public/upload/cf4ad471bc.png)

Input

輸入的第一行是要處理的測試案例數量 n（0 < n ≤ 500）。

接下來有 n 行，每行包含四個整數（0 ≤ 每個整數 ≤ 100000），其中前兩個表示來源圓的座標，後兩個表示目的地圓的座標。

座標以 (x, y) 的形式列出。

- ------------------------------------------------------------------------------

The first line in the input is the number of test cases n(0< n≤500) to handle.

Following there are n lines each containing four integers (0 ≤ each_integer ≤ 100000) the first pair of which represents the coordinates of the source circle and the other represents that of the destination circle.

The coordinates are listed in a form(x, y).

Output

對於每一對整數，你的程式應該先輸出案例編號，然後輸出從來源到目的地的步數。

你可以假設從來源圓到目的地圓總是可以到達的。

- ------------------------------------------------------------------------------

For each pair of integers your program should output the case number first and then the number of step(s) to reach the destination from the source.

You may assume that it is always possible to reach the destination circle from the source circle.

Sample Input 1

```
3
0 0 0 1
0 0 1 0
0 0 0 2

```

Sample Output 1

```
Case 1: 1
Case 2: 2
Case 3: 3

```

Sample Input 2

```
4
1 2 2 1
3 0 0 4
0 3 4 0
1 0 0 4

```

Sample Output 2

```
Case 1: 1
Case 2: 1
Case 3: 8
Case 4: 8
```

```c
#include <stdio.h>

#define ll long long

int main()
{
  int a[2], b[2];
  int n;
  scanf("%d", &n);
  for (int z = 1; z <= n; z++)
  {
    scanf("%d %d %d %d", &a[0], &a[1], &b[0], &b[1]);
    
    ll sum1 = a[0] + a[1];
    ll sum2 = b[0] + b[1];
    ll mid = 0;
    for (int i = sum1; i <= sum2; i++)
      mid += i + 1;
    ll v1 = a[0] - 0;
    ll v2 = sum2 - b[0];
    // printf("%d %d %d", mid, v1, v2);
    ll ans = mid - v1 - v2 - 1;
    
    printf("Case %d: %lld\n", z, ans);
  }

  return 0;
}

```

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

#define ll long long

int main()
{
	int x1, y1, x2, y2;
	int n;
	scanf("%d", &n);
	for (int z = 1; z <= n; z++)
	{
		scanf("%d %d %d %d", &x1, &y1, &x2, &y2);
		ll s1 = (ll)x1 + (ll)((x1+y1)*(x1+y1+1)/2);
		ll s2 = (ll)x2 + (ll)((x2+y2)*(x2+y2+1)/2);
		
		if (s1 > s2)
			printf("Case %d: %lld\n", z, s1-s2);
		else
			printf("Case %d: %lld\n", z, s2-s1);
	}

	return 0;
}
```