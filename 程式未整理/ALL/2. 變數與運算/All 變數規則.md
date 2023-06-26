---
tags: ALL
aliase: 
created: 2023-04-28 06:59
modified: 星期五 28日 四月 2023 06:59:01
---

# All 變數規則
***
# 命名
>[!info]+
>*變數名稱*由底線`_`、英文字母、數字組成，數字不能放前面，有些程式語言(Java)還可以使用錢字號`$`

# 範圍與數值
>[!info]+ two's complement
>變數使用2's complement的系統，`00000000` 為 0, `11111111` 為 -1， 最前面的為sign bit表示正負數

>[!info]+ 正轉負、負轉正
>若需要轉換正負號則對二進制數字a*取complement再加上1*

>[!info]+ 數值是有範圍的
>根據他們的類型有不同的範圍，int類型範圍為 2<sup>-31</sup>~2<sup>31</sup>-1

## overflow 溢位
>[!info]+
>overflow 只可能發生在同號數的相加

>[!info]+
>在C、Java中overflow不會造成exception，但在Mips、frotran中則會raise exception

當浮點數的操作產生了無限或NaN（not a number）時，C++標準庫提供了`std::numeric_limits`類型和`std::isnan()`和`std::isinf()`函數來進行檢測和處理。然而，當浮點數的值超出其表示範圍時，C++標準庫沒有提供類似於整數的exception機制。在這種情況下，程序可能會出現不可預測的結果或者未定義的行為。因此，在進行浮點運算時，需要特別注意數值範圍的限制。