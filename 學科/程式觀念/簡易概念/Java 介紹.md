---
tags: 程式 
aliase: 
created: 2023-02-17 18:39
modified: 星期五 17日 二月 2023 18:39:17
---

# Java 介紹
***
## 三種JAVA
- Java Standard Edition
- Java Enterprise Edition
	- large-scale
	- distributed networking
	- web-based
- Java Micro Edition
	- Subset of Java SE
	- resource-constrained embedded devices
		- Smartwatches

## JRE vs JAVA SE vs JDK

- Java SE(Java Platform, Standard Edition)
	- 通常為開發者使用
	- 有debug的功能
- JRE(Java 執行階段環境): 
	- 通常給一般使用者使用
- JDK(Java開發工具組)
	- 包含IDE

## Compiler


```mermaid
graph LR;
a(compiler)
b(disk)
f(Native OS)
	subgraph "Java Runtime Enviroment"
		c(Bytecode Verifier) & d(Class Loader)
		e(Just-In-Time Compiler)
	end
	
source -->  a
a --> |Bytecode| b
b --> |Bytecode| c
c --> d
d --> e
e --> |Native Code| f
```

