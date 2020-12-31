---
title:  "Challenge! programming 1_Q1"
excerpt: "print decimal number as hexadecimal number"

categories:
  - Passion C

last_modified_at: 2020-12-31
---

## Challenge! programming 1_Q1

#### print decimal number as hexadecimal number

If you know well about Conversion specifier, this problem is easy to solve

''' c

#include <stdio.h>

int main(void) 
{
	int num;
	printf("input decimal number: ");
	scanf("%d", &num);
	
	printf("print by hexadecimal: %#x", num);
	return 0;
}

'''

Below is about Conversion specifier in C Lang

| Conv specifier         |  Output target   |      Output form       |
| :--------------------- | :--------------: | ---------------------: |
| &#37;d                 | char, short, int | signed decimal number  |
| &#37;ld                | long             | signed decimal number  |
| &#37;lld               | long long        | signed decimal number  |
| &#37;u                 | unsigned int     | unsigned decimal number|
| &#37;o or &#37;&#35;o  | unsigned int     | unsigned octal number  |
| &#37;x or &#37;&#35;x  | unsigned int     | unsigned hexa number   |
| &#37;f                 | float, double    | decimal float          |
| &#37;Lf                | long, double     | decimal float          |
| &#37;e or &#37;E       | float, double    | e or E float           |
| &#37;g                 | float, double    | select &#37;f or &#37;e|
| &#37;c                 | char, short, int | character              |
| &#37;s                 | char*            | string                 |
| &#37;p                 | void*            | address of pointer     |

