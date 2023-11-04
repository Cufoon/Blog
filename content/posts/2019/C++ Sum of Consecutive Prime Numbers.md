---
title: "C++ Sum of Consecutive Prime Numbers"
slug: "cpp-sum-of-consecutive-prime-numbers"
date: 2019-08-07T15:15:23+08:00
draft: false
tags: ["CppProblems"]
---

# Sum of Consecutive Prime Numbers

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

Some positive integers can be represented by a sum of one or more consecutive prime numbers. How many such representations does a given positive integer have? For example, the integer 53 has two representations 5 + 7 + 11 + 13 + 17 and 53. The integer 41 has three representations 2+3+5+7+11+13, 11+13+17, and 41. The integer 3 has only one representation, which is 3. The integer 20 has no such representations. Note that summands must be consecutive prime 
numbers, so neither 7 + 13 nor 3 + 5 + 5 + 7 is a valid representation for the integer 20. 

Your mission is to write a program that reports the number of representations for the given positive integer.

### **Input**

The input is a sequence of positive integers each in a separate line. The integers are between 2 and 10 000, inclusive. The end of the input is indicated by a zero.

### **Output**

The output should be composed of lines each corresponding to an input line except the last zero. An output line includes the number of representations for the input integer as the sum of one or more consecutive prime numbers. No other characters should be inserted in the output.

### **Sample Input**
    2
    3
    17
    41
    20
    666
    12
    53
    0
### **Sample Output**
    1
    1
    2
    3
    0
    0
    1
    2
## **问题分析**
	先生成素数表 再循环
## AC代码 C++

```cpp
#include <iostream>
#include <vector>
#include <cstring>
using namespace std;

vector<int> primes;
bool ismarked[10001];

int main() {
	memset(ismarked, false, sizeof(ismarked)); //将ismarked数组都初始化为false
	for (int i = 2; i <= 10000; i++) { //利用筛法生成素数表
		if (!ismarked[i]) {
			primes.push_back(i);
			for (int j = i * 2; j <= 10000; j += i) ismarked[j] = true;
		}
	}
	while (1) {
		int n;
		cin >> n;
		if (n == 0) break;
		int result = 0;
		vector<int>:: iterator begin, it;
		for (begin = primes.begin(); begin != primes.end(); begin++) {
			int sum = 0;
			for (it = begin; it != primes.end(); it++) {
				sum +=* it;
				if (sum > n) break;
				else if (sum == n) {
					result++;
					break;
				}
			}
		}
		cout << result << endl;
	}
	return 0;
}
```