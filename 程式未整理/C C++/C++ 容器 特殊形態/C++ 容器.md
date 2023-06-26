---
tags: C++
aliase: vector
created: 2022-12-31 11:20
modified: 星期四 12日 一月 2023 15:04:26
---
## C++ 容器

# C++ vector
## vector syntax
**EXAMPLE:**

```c++
void printv(vector<int>& v) {
	for (vector<int>::iterator i = v.begin(); i != v.end(); i++) {
		cout << *i << " ";
	}
	cout << endl;
}

int main() {
	vector<int> v1;

	for (int i = 0; i < 5; i++) {
		v1.push_back(i);
	}
	printv(v1);

	return 0;
}
```
push:
-`v.push_back(value)`
iterator:
-`for (vector<int>::iterator i = v.begin(); i != v.end(); i++)`
constructor:
-`vector<int> v1;`
-`vector v1(v2);`
-`vector v1(v2.begin(), v2.end());`
-`vector v1(n, elem);`
assign value:
-`v1 = v2;`
-`v1.assign(v2.begin(), v2.end())`
-`v1.assign(n, elem)`

