# Credit Check

Description

如今，在網路上使用信用卡進行購物已成為司空見慣的事情。

然而，由於信用卡號碼相對較長，很容易在輸入時出錯。

為了快速識別類似錯誤和打字錯誤，大多數電子商務網站使用檢查總和算法來驗證信用卡號碼。

其中一個流行的檢查總和算法是Luhn算法，它可以檢測到任何單個數字錯誤以及許多常見的多位數字錯誤：

1. 從倒數第二個數字開始，每隔一個數字加倍以獲得數字列表。
2. 將這些數字的各個位數相加，然後將原始數字中未加倍的數字相加。將兩個結果相加。
3. 如果總和以0結尾，則信用卡號碼有效，否則無效。

例如，使用號碼5181 2710 9900 0012：

1. 將適當的數字加倍（**5**1**8**1**2**7**1**0**9**9**0**0**0**0**1**2）以獲得值：10、16、4、2、18、0、0、2。
2. 將這些值的各個位數相加，獲得（1+0）+（1+6）+ 4 + 2 +（1+8）+ 0 + 0 + 2 = 25。未加倍的數字的和是1+1+7+0+9+0+0+2 = 20，因此總和為20+25=45。
3. 45不以0結尾，因此此信用卡號碼無效。

對於這個問題，您必須編寫一個程式，根據Luhn算法檢查信用卡號碼的有效性。

- ------------------------------------------------------------------------------

These days, it has become commonplace to make purchases over the internet using a credit card.

However, because credit card numbers are relatively long, it is easy to make a mistake while typing them in.

In order to quickly identify errors like typos, most e-commerce websites use a check sum algorithm to verify credit card numbers.

One popular checksum algorithm is the Luhn algorithm, which can detect any single-digit error as well as many common multiple-digit errors:

1. Starting with the second-last digit and moving backwards, double every other digit to obtain a list of numbers.

2. Add up the digits of these numbers, then add the undoubled digits from the original number. Sum the two results.

3. If the total ends in a 0, the credit card number is valid, and it is invalid otherwise.

For example, using the number5181 2710 9900 0012:

1. Double the appropriate digits (**5**1**8**1**2**7**1**0**9**9**0**0**0**0**1**2) to obtain the values: 10, 16, 4, 2, 18, 0, 0,2.

2. Add up the digits of these values to get (1+0) + (1+6) + 4 + 2 + (1+8) + 0 + 0 + 2 = 25.Thesum of the undoubled digits is 1+1+7+0+9+0+0+2 = 20, so the total is 20+25=45.

3. 45 does not end in a 0, so this credit card number is invalid.

For this problem, you must write a program that checks the validity of credit card numbers according to the Luhn algorithm.

![https://oj.fcu.edu.tw/public/upload/de8e5faa04.png](https://oj.fcu.edu.tw/public/upload/de8e5faa04.png)

Input

輸入以單獨一行的數字 N 開始，接著是 N 行，每行包含一個信用卡號碼。

每個信用卡號碼由十六個十進制數字組成，每四個數字以單個空格分隔。

- ------------------------------------------------------------------------------

The input begins with a number N on a single line, followed by N lines each containing a single credit card number.

Each credit card number consists of 16 decimal digits in groups of four separated by single spaces.

Output

輸出包含每個輸入信用卡號碼的一行。

如果信用卡號碼有效，此行將包含字串「Valid」，否則為「Invalid」。

- ------------------------------------------------------------------------------

The output consists of one line for each input credit card number.

If the credit card number is valid, this line consists of the string ‘Valid’, otherwise it reads ‘Invalid’.

Sample Input 1

```
2
5181 2710 9900 0012
5181 2710 9900 0017
```

Sample Output 1

```
Invalid
Valid
```

Sample Input 2

```
9
9999 9999 9999 9999
0000 0000 0000 0000
5050 5050 5050 5050
1234 5678 1234 5678
8931 7853 8957 2362
1000 0000 1001 1009
8326 1829 0478 7841
8626 1020 0070 7050
8726 1020 0070 7050
```

Sample Output 2

```
Invalid
Valid
Invalid
Invalid
Invalid
Invalid
Invalid
Valid
Invalid
```

```c
#include <stdio.h>

int main()
{
  int n;
  int *pn = &n;
  int a[4] = {};
  int *pa = a;
  scanf("%d", pn);
  while ((*pn)--)
  {
    for (int i = 0; i < 4; i++)
      scanf("%d", pa+i);
      
    int tmp[8] = {};
    int *ptmp = tmp;
    
    int add2 = 0;
    int *padd2 = &add2;
    for (int i = 0; i < 4; i++)
    {
      *padd2 += *(pa+i) % 10;
      *(pa+i) /= 10;
      *(ptmp+i*2) = 2 * (*(pa+i) % 10);
      *(pa+i) /= 10;
      *padd2 += *(pa+i) % 10;
      *(pa+i) /= 10;
      *(ptmp+i*2+1) = 2 * (*(pa+i));
    }
    
    
    int add = 0;
    int *padd = &add;
    for (int i = 0; i < 8; i++)
    {
      *padd += *(ptmp+i) % 10;
      *(ptmp+i) /= 10;
      *padd += *(ptmp+i) % 10;
    }
    
    int total = 0;
    int *ptotal = &total;
    *ptotal = *padd + *padd2;
    
    if (*ptotal % 10 == 0)
      printf("Valid\n");
    else
      printf("Invalid\n");
    
  }

  return 0;
}
```

```c
#include <stdio.h>
#include <string.h>

int calculateLuhn(char *cardNumber) {
    int nDigits = strlen(cardNumber);
    int sum = 0, isSecond = 0;
    
    for (int i = nDigits - 1; i >= 0; i--) {
        // Skip spaces
        if (cardNumber[i] == ' ') continue;

        int digit = cardNumber[i] - '0';

        if (isSecond == 1)
            digit = digit * 2;

        // Add the two digits to handle cases like 10, 18, etc.
        sum += digit / 10;
        sum += digit % 10;

        isSecond = !isSecond;
    }
    return (sum % 10 == 0);
}

int main() {
    int N;
    scanf("%d", &N);
    char cardNumber[20]; // Includes space for spaces and null terminator

    // Consume the newline character after the number N
    getchar();

    for (int i = 0; i < N; i++) {
        fgets(cardNumber, sizeof(cardNumber), stdin); // Read the card number
        cardNumber[strcspn(cardNumber, "\n")] = 0; // Remove newline character

        if (calculateLuhn(cardNumber))
            printf("Valid\n");
        else
            printf("Invalid\n");
    }

    return 0;
}

```