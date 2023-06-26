# Java 默認參數

## 函式參數
>[!info]+
>Java 不支持默認參數 (default parameter) 的概念，定義函式時不能為參數設置默認值

兩方法可達成類似默認參數的效果

1. 函數重載
2. 使用預設值，在函式中對參數進行判斷，如果未傳入參數則使用預設值。

```java
class MyClass {
    public void print(String y) {
        if (y == null) y = "default";
    }
}
```

>[!note]+
>方法並不完美，傳參數的數量要完整，不然會報錯

