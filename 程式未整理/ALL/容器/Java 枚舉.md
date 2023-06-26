---
tags: Java 
aliase: 
created: 2023-04-12 11:30
modified: 星期三 12日 四月 2023 11:30:47
---

# Java 枚舉
***
>[!info]+
>In Java, enum types are special types of *classes* and enum constants are implicitly **final** and **static**.


```java linenos
enum WeekDay{
	MONDAY,
	TUESDAY,
	WEDNESDAY,
	THURDAY,
	FRIDAY,
	SATURDAY,
	SUNDAY;
	
	public boolean isHoliday(WeekDay day) {
		if(day == WeekDay.SATURDAY || day == WeekDay.SUNDAY)//若是六日則為假日
			return true;
		return false;
	}
}
```

1. 訪問

```java linenos
WeekDay day = WeekDay.SUNDAY; // 賦值
boolean isSunday = (day == WeekDay.SUNDAY)? true: false; // == 比較
```

2. 遍歷

```java linenos
for (Weekday day : Weekday.values()) {
    System.out.println(day);
}
```

3. 建構子 constructor

```java linenos
enum MyEnum{
	VALUE1("abc"), // 建構 VALUE1
	VALUE2("123"); // 建構 VALUE2
	private String str;
	
	private MyEnum(String str) {
		this.str = str; // 創建時VALUE1/VALUE2 賦予對應字串
	}
	
	public String getStr() {
		return this.str;
	}
}

public class Test {
	public static void main(String args[]) {
		MyEnum a = MyEnum.VALUE1;
		System.out.println(a.getStr());
	}
}
```
