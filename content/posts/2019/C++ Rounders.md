---
title: "C++ Rounders"
slug: "cpp-rounders"
date: 2019-08-07T15:15:21+08:00
draft: false
tags: ["CppProblems"]
---

# Rounders

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

For a given number, if greater than ten, round it to the nearest ten, then (if that result is greater than 100) take the result and round it to the nearest hundred, then (if that result is greater than 1000) take that number and round it to the nearest thousand, and so on ... 

### **Input**

Input to this problem will begin with a line containing a single integer n indicating the number of integers to round. The next n lines each contain a single integer x (0 <= x <= 99999999).

### **Output**

For each integer in the input, display the rounded integer on its own line. 

Note: Round up on fives.

### **Sample Input**
    9
    15
    14
    4
    5
    99
    12345678
    44444445
    1445
    446
### **Sample Output**
    20
    10
    4
    5
    100
    10000000
    50000000
    2000
    500
## **问题分析**
    题目的意思就是从个位开始一位一位的往高位进行四舍五入
## AC代码 C++

```cpp
#include <iostream>
using namespace std;
int main() {
	int t = 0;
	cin >> t;
	while (t--) {
		string s;
		cin >> s;
		int len = s.length();
		for (int i = len - 1; i > 0; i--) {
			if (s[i] >= 53) s[i - 1]++;
			s[i] = '0';
		}
		if (s[0] > 57) {
			s[0] = '0';
			cout << "1" << s;
		} else cout << s;
		cout << endl;
	}
	return 0;
}
```