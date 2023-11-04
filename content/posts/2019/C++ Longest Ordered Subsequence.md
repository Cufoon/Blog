---
title: "C++ Longest Ordered Subsequence"
slug: "cpp-longest-ordered-subsequence"
date: 2019-08-07T15:15:18+08:00
draft: false
tags: ["CppProblems"]
---

# Longest Ordered Subsequence

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

A numeric sequence of ai is ordered if a1 < a2 < ... < aN. Let the subsequence of the given numeric sequence (a1, a2, ..., aN) be any sequence (ai1, ai2, ..., aiK), where 1 <= i1 < i2 < ... < iK <= N. For example, sequence (1, 7, 3, 5, 9, 4, 8) has ordered subsequences, e. g., (1, 7), (3, 4, 8) and many others. All longest ordered subsequences are of length 4, e. g., (1, 3, 5, 8).

Your program, when given the numeric sequence, must find the length of its longest ordered subsequence.

### **Input**

The first line of input contains the length of sequence N. The second line contains the elements of sequence - N integers in the range from 0 to 10000 each, separated by spaces. 1 <= N <= 1000 

### **Output**

Output must contain a single integer - the length of the longest ordered subsequence of the given sequence. 

### **Sample Input**
	7
	1 7 3 5 9 4 8
### **Sample Output**
	4
## AC代码 C++

```cpp
#include <iostream>
using namespace std;

int main() {
	int n = 0, s = 0;
	cin >> n;
	int a[n], b[n];
	for (int i = 0; i < n; i++) {
		cin >> a[i];
		b[i] = 1;
	}
	for (int i = 0; i < n - 1; i++) {
		for (int j = i + 1; j < n; j++) {
			if (a[j] > a[i] && b[j] <= b[i]) b[j] = b[i] + 1;
		}
	}
	for (int i = 0; i < n; i++) {
		if (b[i] > s) s = b[i];
	}
	cout << s << endl;
	return 0;
}
```