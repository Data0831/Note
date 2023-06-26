---
tags: 邏輯設計
aliase: 
created: 2023-04-07 12:15
modified: 星期五 7日 四月 2023 12:15:54
---

# 3 Gate-level minimization
***
3.1 INTRODUCTION
3.2 THE MAP METHOD
3.3 FOUR-VARIABLE K-MAP
3.4 PRODUCT-OF-SUMS SIMPLIFICATION
3.5 DON'T-CARE CONDITIONS
3.6 NAND AND NOR IMPLEMENTATION
3.7 OTHER TWO-LEVEL IMPLEMENTATIONS
3.8 EXCLUSIVE-OR FUNCTION
3.9 HARDWARE DESCRIPTION LANGUAGE

---

>[!info]+
>Gate-level minimization(閘級最小化): is the design task of finding an optimal(優化) gate-level implementa-  
tion of the Boolean functions


# 3.2 3.3 k map

>[!col]+
>![[Kmap(2,3,4)]]
>
>- two variable k-map
>- three variable k-map
>- four variable k-map

## proposition of Karnaugh map

>[!info]+
>A diagram(k map) made up of *squares*(由方形組成)

- Epression(**表示**): 
	- each square represents one *minterm* (a **pictorial form**(圖形式) of a *truth table*)
	- can convert truth table to k map, or k map to truth table 
- simplication / minimization / differ: **化簡特性**
	1. all the minterms of the function are *covered*(被選中) when we combine the squares
	2. Sometimes there may be two or more expressions(多種可能) that satisfy the simplification criteria(標準)
	3. 其他:
		- 2<sup>n</sup> adjacent squares, n = 0, 1, 2,...  
		- two *adjacent*(相鄰) squares (相鄰方塊的0,1變化)
		- *Gray code* sequence
		- applicable if *variables < 7*

## implicant
>[!success]+
>**implicant**: each square(minterm) has value *1* -> 2<sup>n</sup> 大小的方格(n≥0, n∈z)
>**prime implicant**:maximum(最大) adjacent squares in the map
>**essential**: a minterm is covered by *only one* prime implicant

>[!col]+
>![[implicant_k_map|900]]
>
>**implicant**: m0, m2, m8, m9, m10, m11 ... 2<sup>n</sup> 大小的方格
>**prime implicant**: AB', B'D' (最大大小方格)
>**essential prime implicant**: B'D', AB' (m0, m2, m9, m11 只有被cover 1 次)
>m0: B'D' m2: B'D' m8: AB', B'D' m9: AB' m10: AB', B'D' m11: AB'

How to find the simplified expression?  
- Method  
- Find all prime implicants  
- Find all essential prime implicants  
- Select minimum number of prime implicant to  
cover the minterm that not cover by essential  
prime implicants

# 3.4 Simplify sop and pos
- Approach #1
	- sop: k map
	- pos: 
		1. find F' (k map Simplified minterm = 0)
		2. demorgan F'	
- Approach #2: duality (k map MAXTERM ver.)
	- combinations of maxterms (it was minterms)  

# 3.5 don't cate condition
>[!info]+
>**don't cate condition**: not specified(指定) for certain combinations of variables

- can be implemented as 0 or 1
- denote notation: d (w, x, y, z) = $\sum$(0, 2, 5)

# 3.6 nor and nand
>[!info]+
>**NAND**: (universal gate) can implement any digital system

![[NAND_circuit]]
and-invert = invert or

## NAND implmenation
NAND-NAND = sum of products
AND-OR logic => NAND-NAND logic

AND => AND-INVERT
OR => INVERT-OR

## NOR implmenation
NOR-NOR = sum of products
AND => INVERT-AND
OR => OR-INVERT

# 3.7 weired logic
- weired logic
	- AND-OR-INVERT function  
	- OR-AND-INVERT function

## Nondegenerate Forms
eight of them: degenerate forms = a single operation  
◼ The eight nondegenerate forms  
◼ AND-OR, OR-AND, NAND-NAND, NOR-NOR, NOR-OR,  
NAND-AND, OR-NAND, AND-NOR  
◼ AND-OR and NAND-NAND = sum of products  
◼ OR-AND and NOR-NOR = product of sums  
◼ NOR-OR, NAND-AND, OR-AND, AND-OR = ?

AND-OR-INVERT (AOI) Implementation  
◼ NAND-AND = AND-NOR = AOI  
◼ F = (AB+CD+E)'  
◼ F' = AB+CD+E(sum of products)  
◼ simplify F' in sum of products

OR-AND-INVERT (OAI) Implementation  
◼ OR-NAND = NOR-OR = OAI  
◼ F = ((A+B)(C+D)E)'  
◼ F' = (A+B)(C+D)E (product of sums)  
◼ simplified F' in products of sum