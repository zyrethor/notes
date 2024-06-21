# Fibonaccimal Base

Description

著名的費波那契數列是通過從 0 和 1 開始，然後將最後兩個數相加以獲得下一個數。

例如，數列中的第三個數是 1（1=1+0），第四個是 2（2=1+1），第五個是 3（3=2+1），依此類推。

![https://oj.fcu.edu.tw/public/upload/d0e5a67aa0.png](https://oj.fcu.edu.tw/public/upload/d0e5a67aa0.png)

這個數列在我們生活中的許多事物中都出現，也在自然界中具有重大意義。

除其他之外，你知道所有正整數都可以表示為費波那契數列中數字的和嗎？

更甚者，所有正整數都可以表示為一組費波那契數的和，即數列中的數字，不重複使用。

例如：13可以是集合{13}，{5,8}或{2,3,8}的和，而17則表示為{1,3,13}或{1,3,5,8}。

由於所有數字都具有此特性（你想試著自己證明嗎？），這個集合可以作為表示數字的一種很好的方式。

但是，正如我們所見，一些數字有多個集合，它們的和是該數字。

我們怎麼解決這個問題呢？很簡單！如果我們添加了一個限制，即集合不能包含兩個連續的費波那契數，那麼對於每個數字我們就有了唯一的表示！

這個限制是因為任何兩個連續的費波那契的和就是下一個費波那契數。

現在我們知道了所有這些，我們可以準備一種很好的方法來表示任何正整數。

我們將使用一個二進制序列（只有零和一）來做到這一點。例如，17 = 1 + 3 + 13（請記住不能使用兩個連續的費波那契數）。

讓我們為每個未使用的費波那契數寫一個零，對於每個使用的費波那契數寫一個一，從右邊開始。然後，17 = 100101。

請參見圖2以獲得詳細解釋。在這種表示法中，我們不應該在左邊有零，也就是說，我們應該從第一個一開始寫。

為了讓你更好地理解，請注意，在這個方案中，不使用兩個連續的費波那契數意味著二進制序列不會有兩個連續的一。

當我們將此表示法用於一個數字時，我們說我們正在使用費波那契進制，並將其寫為17 = 100101（fib）。

![https://oj.fcu.edu.tw/public/upload/70f5ac2e60.png](https://oj.fcu.edu.tw/public/upload/70f5ac2e60.png)

給定一組十進制基數的數字，你的任務是將它們寫成費波那契進制。

- ------------------------------------------------------------------------------

The well known Fibonacci sequence is obtained by starting with 0 and 1 and then adding the two lastnumbers to get the next one.

For example the third number in the sequence is 1 (1=1+0), the forth is2 (2=1+1), the fifth is 3 (3=2+1) and so on.

![https://oj.fcu.edu.tw/public/upload/d0e5a67aa0.png](https://oj.fcu.edu.tw/public/upload/d0e5a67aa0.png)

The sequence appears on many things in our life, in nature, and has a great significance.

Amongother things, do you know that all positive integer numbers can be represented as a sum of numbers inthe Fibonacci sequence?

More than that, all positive integers can be represented as a sum of a set ofFibonacci numbers, that is, numbers from the sequence, without repetition.

For example:13can be thesum of the sets{13},{5,8}or{2,3,8}and17is represented by{1,3,13}or{1,3,5,8}.

Since all numbershave this property (do you want to try to prove this for yourself?) this set could be a nice way to use as

a"base"to represent the number. But, as we have seen, some numbers have more than one set whosesum is the number.

How can we solve that?Simple!If we add the constraint that the sets cannothave two consecutive Fibonacci numbers, than we have a unique representation for each number!

Thisrestriction is because the sum of any two consecutive Fibonacci numbers is just the following Fibonaccinumber.

Now that we know all this we can prepare a nice way to represent any positive integer.

We will usea binary sequence (just zeros and ones) to do that. For example,17 = 1 + 3 + 13(remember that notwo consecutive Fibonacci numbers can be used).

Let’s write a zero for each Fibonacci number that isnot used and one for each one that is used, starting at the right. Then,17 = 100101.

See figure 2 for adetailed explanation. In this representation we should not have zeros at the left, this is, we should onlywrite starting with the first one.

In order for you to understand better, note that in this scheme, notusing two consecutive Fibonacci numbers means that the binary sequence will not have two consecutiveones.

When we use this representation for a number we say that we are using the Fibonaccimal base,and we write it like17 = 100101 (fib).

![https://oj.fcu.edu.tw/public/upload/70f5ac2e60.png](https://oj.fcu.edu.tw/public/upload/70f5ac2e60.png)

Given a set of numbers in decimal base, your task is to write them in the Fibonaccimal base.

Input

輸入的第一行包含一個數字 N，代表接下來的數字數量（1 ≤ N ≤ 500）。

接著是確切的 N 行，每行包含一個小於 100,000,000 的正整數。

這些數字可以以任何順序出現。

- ------------------------------------------------------------------------------

The first line of input contains a single number N, representing the quantity of numbers that follow(1 ≤ N ≤ 500).

Than follow exactly N lines, each one containing a single positive integer smaller than 100 000 000.

These numbers can come in any order.

Output

你應該對輸入中的每個 N 個整數輸出一行，格式為 'DEC_BASE = FIB_BASE (fib)'。

DEC_BASE 是十進制中的原始數字，而 FIB_BASE 則是其在費波那契進制中的表示。

請參考示例輸出以了解。

- ------------------------------------------------------------------------------

You should output a single line for each of the N integers in the input, with the format ‘DEC_BASE = FIB_BASE(fib)’.

DEC_BASE is the original number in decimal base and FIB_BASE is its representation in Fibonaccimal base.

See the sample output for an example.

Sample Input 1

```
10
1
2
3
4
5
6
7
8
9
10

```

Sample Output 1

```
1 = 1 (fib)
2 = 10 (fib)
3 = 100 (fib)
4 = 101 (fib)
5 = 1000 (fib)
6 = 1001 (fib)
7 = 1010 (fib)
8 = 10000 (fib)
9 = 10001 (fib)
10 = 10010 (fib)

```

Sample Input 2

```
4
13
17
100
1234

```

Sample Output 2

```
13 = 100000 (fib)
17 = 100101 (fib)
100 = 1000010100 (fib)
1234 = 100100000100001 (fib)
```

```c
#include <stdio.h>
#include <stdbool.h>

int main()
{
	int fib[40] = {0, 1};
	for (int i = 2; i < 40; i++)
		fib[i] = fib[i - 1] + fib[i - 2];
		
	int t;
	scanf ("%d", &t);
	while (t--)
	{
		int n;
		scanf ("%d", &n);
		printf ("%d = ", n);
		
		bool flag = false;
		for (int i = 39; i >= 2; i--)
		{
			if (n >= fib[i])
			{
				n -= fib[i];
				flag = true;
				printf ("1");
			}
			else if (flag)
				printf ("0");
		}
		printf (" (fib)\n");
	}
	return 0;
}

```