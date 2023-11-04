---
title: "C++ Friend Number"
slug: "cpp-friend-number"
date: 2019-08-07T15:15:17+08:00
draft: false
tags: ["CppProblems"]
---

# Friend Number

**Time Limit**: 1000ms, **Special Time Limit**:2500ms, **Memory Limit**:32768KB

### **Problem description**

Friend numbers are defined recursively as follows.

- (1)numbers 1 and 2 are friend numbers;
- (2)if a and b are friend numbers,so is ab+a+b;
- (3)only the numbers defined in (1) and (2) are friend numbers.

Now your task is to judge whether an integer is a friend number. 

### **Input**

There are several lines in input files,each line has a nonnegative integer a,0≤a≤2^30. 

### **Output**

For the number a on each line of the input file,if a is a friend number,output "YES!",otherwise output "NO!" 

### **Sample Input**
    3
    13121
    12131
### **Sample Output**
    YES!
    YES!
    NO!
## **问题分析**
	这是一个数学问题，题目中说"if a and b are friend numbers,so is ab+a+b"
	我们假设c=ab+a+b
	那么c+1=ab+a+b+1
	即c+1=(a+1)*(b+1)
	我们假如再把a+1 b+1按照这个方法拆分下去
	就可以得到c+1=(2^n)*(3^m)
	然后就有思路了
*Tip:2^n^!=3^m^*
## AC代码 C++

```cpp
#include <stdio.h>
	int main() {
	int t = 0;
	while (scanf("%d",& t)) {
		if (t == 0) printf("NO!\n");
		else {
			t++;
			while (t % 2 == 0) {
				t /= 2;
			}
			while (t % 3 == 0) {
				t /= 3;
			}
			if (t == 1) printf("YES!\n");
			else printf("NO!\n");
		}
	}
	return 0;
}
```