---
title: "C++ Children's Game"
slug: "cpp-Children_s-Game"
date: 2019-08-07T15:15:16+08:00
draft: false
tags: ["CppProblems"]
---

# Children's Game

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

There are lots of number games for children. These games are pretty easy to play but not so easy to make. We will discuss about an interesting game here. Each player will be given N positive integers. (S)He can make a big integer by appending those integers after one another. Such as if there are 4 integers as 123, 124, 56, 90 then the following integers can be made: 1231245690, 1241235690, 5612312490, 9012312456, 9056124123 etc. In fact 24 such integers can be made. But one thing is sure that 9056124123 is the largest possible integer which can be made.

You may think that it’s very easy to find out the answer but will it be easy for a child who has just got the idea of number? 


### **Input**

Each input starts with a positive integer N (≤ 50). In next lines there are N positive integers. Input is terminated by N = 0, which should not be processed. The largest integer that the program should accept is 32767.

### **Output**

For each input set, you have to print the largest possible integer which can be made by appending all the N integers.

### **Sample Input**
    4
    123 124 56 90
    5
    123 124 56 90 9
    5
    9 9 9 9 9
    0
### **Sample Output**
    9056124123
    99056124123
    99999
## **问题分析**
根据题意很容易想到，利用字符串，然后进行字符串的比较，把字符串大的排到前面即可，但是遇到一些情况时确实不能满足条件的。

比如字符串7和76 字符串76比字符串7大 按照上面的思路 排出来的数是767 而事实上776>767 这样得到的结果不对

所以问题就变成了字符串a和b  a+b是否大于b+a  这样sort排序后得到的结果就是符合条件的
## AC代码 C++

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

bool cmp(const string& a,const string& b) {
	return a + b > b + a; //用这个方式解决 9和90时 应该是990而不是909的问题
}
string a[50];

int main() {
	while (1) {
		int N = 0;
		cin >> N;
		if (N == 0) break;
		for (int i = 0; i < N; i++) cin >> a[i];
		sort(a, a + N, cmp);
		for (int i = 0; i < N; i++) cout << a[i];
		cout << endl;
	}
	return 0;
}
```