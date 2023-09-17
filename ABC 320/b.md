# 问题描述：****
### Problem Statement
You are given a string S. Find the maximum length of a contiguous substring of S that is a palindrome. Note that there is always a contiguous substring of S that is a palindrome.

### Constraints
S is a string of length between 2 and 100, inclusive, consisting of uppercase English letters.

## 中文
### 问题描述
给你一个字符串S。找出给定字符串中最长的回文子串，并输出它的长度。请注意，S中总是存在一个连续的回文子字符串。
  
### 限制条件
S是一个长度在2到100之间（包含2和100）的字符串，由大写英文字母组成。

# 官方题解

```cpp
#include <iostream>
#include <algorithm>
#include <string>
using namespace std;

//定义了一个 is_palindrome 函数，它接受一个字符串作为参数并返回一个布尔值，表示该字符串是否是回文。

bool is_palindrome(string s) {
	int n = s.size();
	for (int i = 0; i < n; i++) if (s[i] != s[n - i - 1]) return false;
	return true;
}

//
int main() {
	string s;
	cin >> s;
	int n = s.size();

	int ans = 1;//初始化最长回文的长度 ans 为1。

	//我们有两层嵌套的循环。外层循环的变量 i 从0到字符串的长度-1，而内层循环的变量 j 从 i+1 到字符串的长度。这两个循环将会枚举所有的子串。
	for (int i = 0; i < n; i++) {
		for (int j = i + 1; j <= n; j++) {
			string t = "";
			for (int k = i; k < j; k++) t += s[k];
			if (is_palindrome(t)) ans = max(ans, j - i);
		}
	}
	cout << ans << '\n';
}
```
这段代码的目的是找出给定字符串中最长的回文子串并输出它的长度。

我会使用字符串 "level" 作为例子来解释这个程序的工作方式。

```cpp
对于每个 i 和 j 的组合，都会构造一个子串 t，这是通过一个从 i 到 j-1 的循环完成的。
然后调用 is_palindrome 函数检查这个子串 t 是否是回文。

每次当找到一个回文，它都会与当前的最长回文长度 ans 比较，如果更长，就更新 ans。

i=0
current string is: l
current string is: le
current string is: lev
current string is: leve
current string is: level

i=1
current string is: e
current string is: ev
current string is: eve
current string is: evel

i=2
current string is: v
current string is: ve
current string is: vel

i=3
current string is: e
current string is: el

i=4
current string is: l
```

对于 "level"，这个程序会找到最长的回文子串 "level"，并输出其长度5。
