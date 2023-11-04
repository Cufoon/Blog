---
title: "C++ RADAR Brands"
slug: "cpp-RADAR-brands"
date: 2019-08-07T15:15:20+08:00
draft: false
tags: ["CppProblems"]
---

# RADAR Brands

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

Farmer John has been branding the cows with a serial number ever since he started the farm. The new cow fad is 'RADAR' brands, so-called because they read the same forwards and backwards (they are palindromic). All the cows want their daughters branded in the new RADAR style.

Each mother wants her daughter's brand to be derived from her own non-RADAR brand by summing the mother's brand and its reverse. Sometimes (e.g., 12 + 21 = 33) this yields a RADAR palindrome right away. Sometimes the process must be repeated several times until a RADAR brand emerges. Consider the brand '87' that requires four steps to convert to a RADAR brand:

            Brand   Reverse    Sum
    Step 1:   87  +    78   =  165
    Step 2:  165  +   561   =  726
    Step 3:  726  +   627   = 1353
    Step 4: 1353  +  3531   = 4884

Given the mother's brand (a positive integer), determine the number of steps and ultimate RADAR brand that results from applying the procedure above. No answer will be greater than two billion.


### **Input**

Line 1: A single integer, the mother's non-RADAR brand.

### **Output**

Line 1: Two space-separated integers, respectively: the number of steps to find the RADAR brand and the ultimate RADAR brand.

### **Sample Input**
    87
### **Sample Output**
    4 4884
## **问题分析**
	这个题如何利用字符串和整型的转换会超时，所以直接利用字符串相加即可
	由于最终求的是一个回文数，而且计算的过程中两个数字是相互倒着的 所以我们不用一次又一次地把字符串颠倒
	直接相加最终得到的回文数即可
## AC代码 C++

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

string add(string a){
	string b;
	b = a;
	reverse(b.begin(), b.end());
	int len = a.length();
	for (int i = 0; i < len - 1; i++) {
		int tmp = a[i] + b[i] - 96;
		if (tmp > 9) {
			tmp -= 10;
			a[i + 1]++;
		}
		a[i] = tmp + 48;
	}
	int tmp = a[len - 1] + b[len - 1] - 96;
	if (tmp > 9) {
		tmp -= 10;
		a[len - 1] = tmp + 48;
		return a + "1";
	}
	else {
		a[len - 1] = tmp + 48;
		return a;
	}
}

int main() {
	string n = "";
	cin >> n;
	string result;
	int steps = 0;
	while (1) {
		steps++;
		result = add(n);
		string tmp = result;
		reverse(tmp.begin(), tmp.end());
		if (tmp == result) break;
		else n = result;
	}
	cout << steps << " " << result;
	return 0;
}
```