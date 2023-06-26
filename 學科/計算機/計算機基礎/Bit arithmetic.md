---
tags: 
aliase: 
created: 2023-02-27 10:57
modified: 星期一 27日 二月 2023 10:57:29
---

# Bit arithmetic
***
## Complement
>[!info]+
>r's complement = r<sup>n</sup> - N
>(r-1)'s complement = r<sup>n</sup> - N -1

>N: 數字
>n: 位數+1
>r: r進制

<u>ex</u>:
N = 546700, n = 7, r = 10
10's complement = 10<sup>7</sup> - 546700 = 453300
9's complement = 10<sup>7</sup> - 546700 -1 = 453299

---
## Binary Integer
### 2s-Complement Unsigned Integers
$x=x_{n-1}2^{n-1}+x_{n-2}2^{n-2}+...+x_12^1+x_02^0$
- Range: 0 to +2<sup>n</sup>-1
- Example:
	0000 0000 0000 0000 0000 0000 0000 1011<sub>2</sub>
	= 0 + ... + 1x2<sup>3</sup>+0x2<sup>2</sup>+1x2<sup>1</sup>+1x2<sup>0</sup>
	= 11<sub>10</sub>
- 0 to 4,294,967,295 (32bit)

### 2s-Complement Signed Integers
$x=-x_{n-1}2^{n-1}+x_{n-2}2^{n-2}+...+x_12^1+x_02^0$
- Range: -2<sup>n-1</sup> to +2<sup>n-1</sup>-1
- Example
	1111 1111 1111 1111 1111 1111 1111 1100<sub>2</sub>
	= -1x2<sup>31</sup> + ... + 1x2<sup>2</sup>+0x2<sup>1</sup>+0x2<sup>0</sup>
	= -2,147,483,648 + 2,147,483,644 = -4<sub>10</sub>
- -2,147,483,648 to -2,147,483,647 (32bit)
- 正數與unsigned整數一樣

### Signed Negation
- x+x'=1111...111<sub>2</sub>=-1
- x'+1=-x

Example:
- +2 = 0000 0000 ... 0010<sub>2</sub>
- -2 = 1111 1111 ... 1101<sub>2</sub> + 1
	= 1111 1111 ... 1110<sub>2</sub>

### Sign Extension
- In MIPS instruction set
	- addi:extend immediate value
	- 1b，1h:extend loaded byte/halfword
	- beq，bne:extend the displacement
- Replicate the sign bit to left
	- c.f. unsigned value: extend with 0s
- Examples: 8bit to 16-bit
	- +2:0000 0010 => 0000 0000 0000 0010
	- -2:1111 1110 => 1111 1111 1111 1110

>加法器為32bit若使用短整數進行加法那必須要做sign extension

---
## Numbers example
| Decimal |  2補數 |  1補數 | Sign-Magnitude form |
|:--------|:-----|:-----|:--------------------|
|      +7 | 0111 | 0111 |                0111 |
|      +6 | 0110 | 0110 |                0110 |
|      +5 | 0101 | 0101 |                0101 |
|      +4 | 0100 | 0100 |                0100 |
|      +3 | 0011 | 0011 |                0011 |
|      +2 | 0010 | 0010 |                0010 |
|      +1 | 0001 | 0001 |                0001 |
|      +0 | 0000 | 0000 |                0000 |
|      -0 | ---- | 1111 |                1000 |
|      -1 | 1111 | 1110 |                1001 |
|      -2 | 1110 | 1101 |                1010 |
|      -3 | 1101 | 1100 |                1011 |
|      -4 | 1100 | 1011 |                1100 |
|      -5 | 1011 | 1010 |                1101 |
|      -6 | 1010 | 1001 |                1110 |
|      -7 | 1001 | 1000 |                1111 |
|      -8 | 1000 | ---- | ----                |  
>Sign-Magnitude form: 最前面的 1/0 控制正負