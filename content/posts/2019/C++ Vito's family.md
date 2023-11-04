---
title: "C++ Vito's family"
slug: "cpp-vito_s-family"
date: 2019-08-07T15:15:24+08:00
draft: false
tags: ["CppProblems"]
---

# Vito's family

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

The world-known gangster Vito Deadstone is moving to New York. He has a very big family there, all of them living in Lamafia Avenue. Since he will visit all his relatives very often, he is trying to find a house close to them.
Vito wants to minimize the total distance to all of them and has blackmailed you to write a program that solves his problem. 

### **Input**

The input consists of several test cases. The first line contains the number of test cases.
For each test case you will be given the integer number of relatives r ( 0 < r < 500) and the street numbers (also integers) (s<sub>1</sub>,s<sub>2</sub>,s<sub>3</sub>...,s<sub>n</sub>) where they live ( 0 < s<sub>i</sub> < 30000 ). Note that several relatives could live in the same street number. 

### **Output**

For each test case your program must write the minimal sum of distances from the optimal Vito's house to each one of his relatives. The distance between two street numbers s<sub>i</sub> and s<sub>j</sub> is d<sub>ij</sub>= |s<sub>i</sub>-s<sub>j</sub>|.

### **Sample Input**
    2
    2 2 4 
    3 2 4 6
### **Sample Output**
    2
    4
## **问题分析**
	一个点到一段线段两端点的距离和最小时，该点在这段线段上，且距离最小为线段的长
	本题依据该思想可以很快做出来
## AC代码 C++

```cpp
#include <iostream>
#include <cmath>
#include <algorithm>
using namespace std;

int main() {
	int t = 0;
	cin >> t;
	while (t--) {
		int n;
		cin >> n;
		int a[n];
		for (int i = 0; i < n; i++) cin >> a[i];
		sort(a, a + n); // 先排序 再计算
		int s = 0;
		int n_end = n / 2;
		for (int i = 0; i < n_end; i++) {
			s += a[n - 1 - i] - a[i];
		}
		cout << s << endl;
	}
	return 0;
}
```