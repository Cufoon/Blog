---
title: "C++ Adding 1s, 2s, and 3s"
slug: "cpp-adding-1s-2s-and-3s"
date: 2019-08-07T15:15:15+08:00
draft: false
tags: ["CppProblems"]
---

# Adding 1s, 2s, and 3s

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

Integer 4 can be expressed as a sum of 1s, 2s, and 3s in seven different ways as follows:

    1+1+1+1, (1)
    1+1+2, (2)
    1+2+1, (3)
    2+1+1, (4)
    2+2, (5)
    1+3, (6)
    3+1. (7)

Write a program that determines the number of ways in which a given integer can be expressed as a sum of 1s, 2s, and 3s. You may assume that the integer is positive and less than 20.

### **Input**

The input consists of T test cases. The number of test cases (T) is given in the first line of the input file. Each test case consists of an integer written in a single line.

### **Output**

Print exactly one line for each test case. The line should contain an integer representing the number of ways.

### **Sample Input**

    3
    4
    7
    10

### **Sample Output**

    7
    47
    274

## **问题分析**

    从4开始 每一项的结果等于前三项的和

## AC 代码 C++

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int a[21];
int main() {
	a[1] = 1;
	a[2] = 2;
	a[3] = 4;
	int k = 3;
	int t;
	cin >> t;
	while (t--) {
		int n = 0;
		cin >> n;
		if (n > k) {
			for (int i = k + 1; i <= n; i++) a[i] = a[i - 1] + a[i - 2] + a[i - 3];
			k = n;
		}
		cout << a[n] << endl;
	}
	return 0;
}
```
