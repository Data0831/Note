---
tags: Java
aliase: 
created: 2023-02-08 19:57
modified: 星期三 8日 二月 2023 19:57:27
---

# TimeTool
***
```java
package tool;

import java.text.SimpleDateFormat;
import java.util.Date;

public class TimeTool {
	private static final SimpleDateFormat fmt = new SimpleDateFormat("HH:mm:ss.SSS");
	public interface Task{
		void excute();//interface default is public
	}
	
	public static void check(String title, Task task) {
		if(task == null) return;//object default is pointer/ref and can set to null
		title = (title == null)? "": ("[" + title + "]");
		System.out.println(title);
		System.out.println("Start: " + fmt.format(new Date()));
		long begin = System.currentTimeMillis();
		task.excute();
		long end = System.currentTimeMillis();
		System.out.println("End: " + fmt.format(new Date()));
		double delta = (end-begin) / 1000.0;
		System.out.println("cost: " + delta + "sec");
		System.out.println("---------------------------------------");
	}
}
```
