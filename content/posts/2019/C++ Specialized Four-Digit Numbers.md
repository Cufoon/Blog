---
title: "C++ Specialized Four-Digit Numbers"
slug: "cpp-specialized-four-digit-numbers"
date: 2019-08-07T15:15:22+08:00
draft: false
tags: ["CppProblems"]
---

# Specialized Four-Digit Numbers

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:65536KB

### **Problem description**

Find and list all four-digit numbers in decimal notation that have the property that the sum of its four digits equals the sum of its digits when represented in hexadecimal (base 16) notation and also equals the sum of its digits when represented in duodecimal (base 12) notation. 
For example, the number 2991 has the sum of (decimal) digits 2+9+9+1 = 21. Since 2991 = 1 * 1728 + 8 * 144 + 9 * 12 + 3, its duodecimal representation is 189312, and these digits also sum up to 21. But in hexadecimal 2991 is BAF16, and 11+10+15 = 36, so 2991 should be rejected by your program. 
The next number (2992), however, has digits that sum to 22 in all three representations (including BB016), so 2992 should be on the listed output. (We don't want decimal numbers with fewer than four digits -- excluding leading zeroes -- so that 2992 is the first correct answer.) 

### **Input**

There is no input for this problem

### **Output**

Your output is to be 2992 and all larger four-digit numbers that satisfy the requirements (in strictly increasing order), each on a separate line with no leading or trailing blanks, ending with a new-line character. There are to be no blank lines in the output. The first few lines of the output are shown below. 

### **Sample Input**
    There is no input for this problem
### **Sample Output**
    2992
    2993
    2994
    2995
    2996
    2997
    2998
    2999
    ...
## **问题分析**
	看似很复杂，实际很简单
## AC代码 C++

```cpp
#include <iostream>
using namespace std;

int addDigit(int n, int binStep){ //10进制的数转化成任意进制的数 n为10进制的数 
	int sum = 0;
	while (n != 0) {
		sum += n % binStep;
		n /= binStep;
	}
	return sum;
}
int main() {
	int s10 = 0, s12 = 0, s16 = 0;
	for (int i = 2992; i <= 9999; i++) {
		s10 = addDigit(i, 10);
		s12 = addDigit(i, 12);
		s16 = addDigit(i, 16);
		if (s10 == s12 && s10 == s16) cout << i << endl;
	}
	return 0;
}
```