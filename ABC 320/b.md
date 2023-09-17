# 问题描述：****
### Problem Statement
You are given a string S. Find the maximum length of a contiguous substring of S that is a palindrome. Note that there is always a contiguous substring of S that is a palindrome.

### Constraints
S is a string of length between 2 and 100, inclusive, consisting of uppercase English letters.

## 中文
### 问题描述
你被给予一个字符串S。找出S的连续子字符串中，是回文的最大长度。请注意，S中总是存在一个连续的回文子字符串。
  
### 限制条件
S是一个长度在2到100之间（包含2和100）的字符串，由大写英文字母组成。

# 官方题解

```cpp
#include <iostream>
#include <algorithm>
#include <string>
using namespace std;

bool is_palindrome(string s) {
	int n = s.size();
	for (int i = 0; i < n; i++) if (s[i] != s[n - i - 1]) return false;
	return true;
}

int main() {
	string s;
	cin >> s;
	int n = s.size();
	int ans = 1;
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

首先，定义了一个 is_palindrome 函数，它接受一个字符串作为参数并返回一个布尔值，表示该字符串是否是回文。
在 main 函数中，首先读入字符串 s（在我们的例子中是 "level"），然后初始化最长回文的长度 ans 为1。
接着，我们有两层嵌套的循环。外层循环的变量 i 从0到字符串的长度-1，而内层循环的变量 j 从 i+1 到字符串的长度。这两个循环将会枚举所有的子串。
以下是对于 "level" 字符串的循环情况的逐步描述：

当 i = 0 时，即子串起始位置是 'l'：
j = 1：子串是 "l"，是一个回文。
j = 2：子串是 "le"，不是回文。
j = 3：子串是 "lev"，不是回文。
j = 4：子串是 "leve"，不是回文。
j = 5：子串是 "level"，是一个回文。
当 i = 1 时，即子串起始位置是 'e'：
j = 2：子串是 "e"，是一个回文。
...以此类推。
每次当找到一个回文，它都会与当前的最长回文长度 ans 比较，如果更长，就更新 ans。
在上述过程中，对于每个 i 和 j 的组合，都会构造一个子串 t，这是通过一个从 i 到 j-1 的循环完成的。然后调用 is_palindrome 函数检查这个子串 t 是否是回文。

对于 "level"，这个程序会找到最长的回文子串 "level"，并输出其长度5。
