---
title: "C++ Number lengths"
slug: "cpp-number-lengths"
date: 2019-08-07T15:15:19+08:00
draft: false
tags: ["CppProblems"]
---

# Number lengths

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

N! (N factorial) can be quite irritating and difficult to compute for large values of N. So instead of calculating N!, I want to know how many digits are in it. (Remember that N! = N * (N - 1) * (N - 2) * ... * 2 * 1) 

### **Input**

Each line of the input will have a single integer N on it 0 < N < 1000000 (1 million). Input is terminated by end of file. 

### **Output**

For each value of N, print out how many digits are in N!. 

### **Sample Input**
    1
    3
    32000
    1000000
### **Sample Output**
    1
    1
    130271
    5565709

## **问题分析**
	利用log10求位数 很快出结果
## AC代码 C++

```cpp
#include <iostream>
#include <algorithm>
#include <cmath>
using namespace std;
int main() {
	int n;
	while (cin >> n) {
		double length = 0.0;
		for (int i = 1; i <= n; i++) {
			length += log10(i * 1.0);
		}
		cout << int(length + 1) << endl;
	}
	return 0;
}
```