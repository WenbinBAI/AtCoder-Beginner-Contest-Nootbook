# 问题描述：
### Problem Statement
You are given positive integers **A** and **B**. Print the value **A^B** + **B^A**.

### Constraints
2≤A≤B≤9
All input values are integers.

## 中文
### 问题描述
给定两个正整数 **A** 和 **B**。请打印 **A^B** + **B^A** 的值。

### 限制条件
2≤A≤B≤9
所有输入值都是整数。

# 官方题解
“_”代表这个变量不重要，中间过程的某个值，不作为结果等,了解一下就行
```cpp
#include <iostream>
using namespace std;

int main() {
	int a, b;
	cin >> a >> b;
	int x = 1, y = 1;
	for (int _ = 0; _ < b; _++) x *= a;
	for (int _ = 0; _ < a; _++) y *= b;
	cout << x + y << '\n';
}
```

如果想调用cmath库的话
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main(){
    int a, b;
    cin >> a >> b;

    long long result = pow(a, b) + pow(b, a);
    cout << result << endl;
    return 0;
}
```
