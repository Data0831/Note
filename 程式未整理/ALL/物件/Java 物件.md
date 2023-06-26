---
tags: Java
aliase: class object
created: 2023-01-03 15:41
modified: 星期五 6日 一月 2023 12:26:40
---

# Java 物件
***
# 創建與初始化
## 定義與初始化
```cpp linenos title:"2種初始化方式"
class MyClass {
    int x = 0，y;//1. 定義變數時直接賦值
     public MyClass(){//2. 類別的建構子中賦值 
        y = 0;
    }
}
```

### 未初始化，系統預設值
>[!info]+
沒有賦值的話，創建變數會有系統預設：像int,long,short,byte 會預設為**0**, boolean 預設為**false**, char 預設為**\\u0000**, float,double 預設為**0.0**

## 創建物件
```cpp linenos title:"創建方式"
MyClass c1 = new Myclass();
```

## 建構子與解構子
>[!info]+
>constructor: 與class name同名，可直接呼叫或透過new運算子呼叫
>destructor: Java 中沒有解構子，全由JVM自己回收處理

## this
>[!info]+
>`this` 有兩種作用 1. 代表物件，2. 區分

```cpp linenos title:"this的作用"
void method(int num){// 方法
	System.out.println(this.num);//區分num
}

Base re_obj1(){ //透過this 回傳object
	return this;// return Base
}

Base re_obj2(){ //透過new 回傳object
	return new Base();
}
```

***
# 繼承

>[!info]+
>在 Java 中，可以使用關鍵字 ` extends ` 來實現繼承。
>子類繼承會獲得所有父類資料

## 繼承與建構子
>[!info]+
>子類不繼承父類的建構子，但會繼承父類建構子裡的定義並合併至子類的建構子，換句話說在呼叫子類的建構子前**會先呼叫父類的建構子**做初始化動作

```java linenos title:"繼承與建構子"
class Base {
	public int a = 3;
	public int b;
	Base() {// 父類建構子與初始化
		System.out.println("Base 被呼叫");
	}
}

class Derive extends Base {
	public Derive() {// 子類建構子會先呼叫父類建構子做初始化
		System.out.println("Derive 被呼叫");
		System.out.println("從Base繼承了(a,b) = " + a + ' ' + b + '\n');
	}
}

public class Test {
	public static void main(String args[]) {
		Derive a = new Derive();// 呼叫Derive
	}
}
```



## class繼承
```java
public class ArrayList<E> extends List<E>{
}
```
> ArrayList 繼承 List



***




```java 
class A {
	private int a = 10;
	public void out() {
		System.out.println(a);
	}
}

class B extends A{
	public void out() {
		System.out.println("asd");
	}
}

public class Test {
	public static void main(String[] args) throws Exception{
		double num = 1.23E5;
		B b= new B();
	}
}
```

我該如何利用物件b 調用父類A 的方法out

# Java 訪問修飾符 
>[!info]+
>Access Modifiers: `public` `protected` `private`
>若不加訪問修飾符默認為 `default`


| P=package                   |  public  |  protected  |  default  |  private  |
|:-------------------|:---------|:------------|:----------|:----------|
|  同類別中可存取           |  Y       |  Y          |  Y        |  Y        |
|  同P的子類別可存取   |  Y       |  Y          |  Y        |  N        |
|  同P的非子類別可存取(外部)  |  Y       |  Y          |  Y        |  N        |
|  不同P的子類別可存取  |  Y       |  Y          |  N        |  N        |
| 不同P的非子類別可存取  | Y        | N           | N         | N         | 

# 其他
## instanceof
>[!info]+
>`obj instanceof class`: 用來確認此物件是否為class類型或子類型並回傳true，但若**不是同類型編譯前就會報錯**

```java linenos title:"instanceof" highlight:"8"
class A {}
class B{}

public class Test {
	public static void main(String args[]) {
		A a = new A();
		System.out.println(a instanceof A);
		System.out.println(a instanceof B);//編譯前報錯
	}
}

```


# Java 修飾字
***
## static

>[!info]+
>1.  `一開始載入時就存在，就佔據記憶體`
>2.  `不能也不用new就可以使用`(因為已經占據記憶體了)
>3.  static的成員是大家`共享`的(使用同一區記憶體)

- 變數
- 方法
	- 只能存取static變數，不能存取實體變數
- inner class 內部類
	- 既使外部class未實體化，內部class仍然可以使用
- block 區塊
	- 從上而下，編譯器會將他視為要執行的，如同<mark style="background: #FFB86CA6;">main</mark>
>可使用 類名.(方法/變數/內部類) 這種方式存取
>可參考[[C++ 物件#static|C++]]    [IT](https://ithelp.ithome.com.tw/articles/10230484?sc=pt)

### var、method
```java
class OuterClass {
	static int num = 10;// 變數
	public static int change(int num){// 方法
		this.num = num;
	}
}
```
不需要宣告class即可使用
```java
OuterClass.change(3); //將static變數num 從 10 變為 3
```
### inner class
```Java
class OuterClass {
    class InnerClass {
    }
}
```
存取內部類
```Java
OuterClass.InnerClass innerClass = new OuterClass().new InnerClass();
//或是
OuterClass outer = new OuterClass();
OuterClass.InnerClass inner = outer.new InnerClass();
```
靜態內部類不用加new:
```java
OuterClass.StaticInnerClass inner = new OuterClass.StaticInnerClass();
```

## Java 導入修飾符
### abstract
>[!info]+
>修飾類與函數
>抽象類沒有實體，不能建構實體，只能用來繼承
>抽象方法必須在抽象類裡宣告，沒有實現，只有聲明，在子類繼承後須重新定義

### extends
>[!info]+
>繼承
>`class a extends b{}`

### implements
>[!info]+
>實現
>`class a implements b{}`
>b為接口

## 訪問修飾符
- public
- default
	- 可以在相同的package內使用
- private
- protected
與C++大致一致: [[程式未整理/ALL/物件/C++ 修飾字]]

