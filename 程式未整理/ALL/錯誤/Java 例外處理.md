---
tags: Java
aliase: exception
created: 2023-01-06 12:44
modified: 星期五 6日 一月 2023 12:44:35
---
# Java  exception
***

>[!info]+
在Java中，所有異常都繼承自**Throwable**類. Throwable類本身有兩個子類：*Error*和*Exception*，Error類通常用於表示嚴重的系統級錯誤，例如內存不足、棧溢出等，這些錯誤一般無法處理，只能由Java虛擬機處理；而Exception類則表示程序運行過程中出現的可處理異常，例如除以零、文件不存在等，這些異常可以通過Java程序進行處理。


# try - catch - finally
>[!info]+
>`printStackTrace()` 方法會將例外物件對應的堆疊追蹤 (stack trace) 輸出到標準錯誤輸出

```java
try {
    // some code that may throw an exception
    int x = 1/0;
} catch (Exception e) {
    e.printStackTrace();
} finally{
	// 不論有沒有觸發exception都會執行
}
```

## throw
>[!info]+
>throw丟出警告，告知使用者錯誤

```java
throw new IllegalArgumentException("Age must be at least 18.");
throw new Exception("hello");
```


# 自定義 exception

```java linenos
class MyException extends Exception{
	public MyException() {
		super();
		// TODO Auto-generated constructor stub
	}
	public MyException(String message) {
		super(message);
		// TODO Auto-generated constructor stub
	}
}
```

## exception 成員方法
- getMessage(): String -> class name + error message
- printStackTrace(): void -> 輸出 class name + error message
- getStackTrace(): String -> class name + error message
	- 若為Exception 輸出會不正常，請使用getMessage

# exception 種類
>[!info]+
>**checked exception**: 編譯時異常(runtime exception), 不需要在代碼中聲明或捕獲
>**unchecked exception**: 運行時異常(compile-time exception)

## checked exception 種類：
-   IOException：當 I/O 操作失敗或中斷時，可能會拋出此異常。
-   SQLException：當訪問數據庫時發生錯誤時，可能會拋出此異常。
-   ClassNotFoundException：當試圖根據字符串查找類時，如果找不到該類，可能會拋出此異常。
-   InterruptedException：當一個正在等待的線程被中斷時，可能會拋出此異常。
-   InvocationTargetException：當通過反射調用方法時，如果被調用方法拋出異常，則會將異常包裝在 InvocationTargetException 中。
-   NoSuchMethodException：當試圖訪問一個不存在的方法時，可能會拋出此異常。
-   ParseException：當解析字符串中的日期和時間時出現問題時，可能會拋出此異常。
-   CloneNotSupportedException：當嘗試複製一個不支持 Cloneable 接口的對象時，可能會拋出此異常。
-   FileNotFoundException：當試圖打開一個不存在的文件時，可能會拋出此異常。
-   ReflectiveOperationException：當反射操作無法完成時，可能會拋出此異常。

## unchecked exceptions 的種類：
1.  NullPointerException：當程式嘗試存取 null 物件的成員時，會拋出此例外。
2.  IndexOutOfBoundsException：當程式嘗試存取陣列或集合的不存在或無效的索引時，會拋出此例外。
3.  IllegalArgumentException：當程式傳遞無效的參數給一個方法時，會拋出此例外。
4.  ClassCastException：當程式嘗試將一個物件轉型為不相容的型別時，會拋出此例外。
5.  ArithmeticException：當數學運算失敗時，例如除以零，會拋出此例外。
6.  ArrayStoreException：當程式嘗試將錯誤型別的物件存儲到陣列時，會拋出此例外。
7.  UnsupportedOperationException：當程式嘗試呼叫不支援的方法時，會拋出此例外。
8.  SecurityException：當安全性限制被違反時，例如存取受保護的資源，會拋出此例外。


---
```java
public static void main(String[] args) throws Exception{
	if(10>0)	throw new Exception();	
}
```

```java
public static void main(String[] args){
	if(10>0)	throw new IllegalArgumentException();	
}
```

為什麼第一段程式碼main 之後要加 throw Exception，為什麼第二段不用?

編譯器會強制檢查方法可能拋出的受檢異常（checked exception），這包括所有繼承自java.lang.Exception的異常（除了 RuntimeException 及其子類）。在第一段代碼中，throw new Exception() 拋出了一個 checked exception，因此編譯器要求我們在方法聲明中添加 throws Exception。

在第二段代碼中，throw new IllegalArgumentException() 拋出的是一個未檢查異常（unchecked exception）。 unchecked exception不需要在方法聲明中聲明，這是因為編譯器不會強制檢查它們。


# SuppressWarnings
>[!info]+
>從 Java 5.0 起，您可以使用 `java.lang.SuppressWarning` 註釋，來停用與編譯單元子集相關的編譯警告。
>[info](https://www.ibm.com/docs/zh-tw/developer-for-zos/9.1.1?topic=code-excluding-warnings)


