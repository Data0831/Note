---
tags: 邏輯設計
aliase: 
created: 2023-05-29 20:37
modified: 星期二 30日 五月 2023 08:51:31
---

# 4 combinational logic
***

# introduction
Logic circuits for digital systems may be *combinational* or *sequential*. 

>[!info]+ combinnational VS sequential
>**combinnational circuit 組合電路**: 輸出由當前的輸入所決定，n input可對應2<sup>n</sup>種output ex: adder、multiplexer、decoder
>**sequential circuit 循序電路**: 一部分電路會循環，並且具有*記憶*效果 ex:SR latch

## analysis procedure
1. 確認是否為組合電路
	1. 有無迴圈 feedback path
2. 寫出布林函數 derive boolean function(*truth table*)
3. 描述電路功能 verbal explantaion

## design procedure
1. 闡述電路功能 state the problem(spec)
2. 決定input、output變數 determine the input output and assign symbol
3. 寫出真值表並且化簡布林函數 derive the truth table and simplies boolean function
4. 畫電路圖，並驗證 draw logic digram and check correctness

## half adder 半加器

>[!col]+
>半加器電路圖
>![](https://www.techopedia.com/wp-content/uploads/2023/03/9097e01b7bfd4e8dbf671dcfa129beae.png)
>
>| A | B | S | C |
>|:--|:--|:--|:--|
>| 0 | 0 | 0 | 0 |
>| 0 | 1 | 1 | 0 |
>| 1 | 0 | 1 | 0 |
>| 1 | 1 | 0 | 1 |  
>

![](https://www.allaboutelectronics.org/wp-content/uploads/2022/02/slide_2.png)

## full adder 全加器

![123|800](https://www.electroniclinic.com/wp-content/uploads/2020/04/Full-Adder-block-diagram.png)


>[!col]+
>全加器電路圖
>![](https://theorycircuit.com/wp-content/uploads/2018/07/full-adder-circuit.png)
>
> 
> |  A  |  B  | Cin |  S  |  Cout |
> |:----|:----|:----|:----|:------|
> |  0  |  0  |   0 |  0  |    0  |
> |   0 |   0 |   1 |   1 |     0 |
> |  0  |  1  |   0 |  1  |    0  |
> |   0 |   1 |   1 |   0 |     1 |
> |  1  |  0  |   0 |  1  |    0  |
> |   1 |   0 |   1 |   0 |     1 |
> |  1  |  1  |   0 |  0  |    1  |
> |   1 |   1 |   1 |   1 |     1 |  
>

>[!info]+
>由兩個**半加器**與一個**OR gate**組成

```verilog linenos title:"全加器模組 Full Adder Module"
module half_adder(input A,B, output S,C // gate level
);
xor G1(S,A,B);
and G2(C,A,B);
endmodule

module half_adder_assign(input A,B, output S,C// data flow level
);
assign S = A^B;//A xor B
assign C = A&&B;// A and B
endmodule

module full_adder(input A,B,Cin, output S,Cout
);
wire P1, G1, G2;// propergate 是 sum, Generate 是 carry

half_adder HA1(A,B,P1,G1);// sum1 = A+B
half_adder HA2(A,B,S,G2);// sum2 = sum1 + Cin
or or1(Cout, G1, G2);// 確認進位 Cout = HA1.carry || HA2.carry
endmodule
```


<iframe width="560" height="315" src="https://www.youtube.com/embed/EQYk2681sSA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

