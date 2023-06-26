---
tags: JAVA
aliase: 
created: 2023-04-12 10:58
modified: 星期三 12日 四月 2023 10:58:30
---

# JAVA 90
***
1. Inheritance is also known as the
 A.is-a relationship.
 B.uses-a relationship.
 C.has-a relationship.
 D.knows-a relationship.
 
>[!NOTE]- Ans
>A

2. To catch an exception, the code that might throw the exception must be enclosed in a \_\_\_\_\_\_\_\_.
 A.catch block.
 B.throws block.
 C.try block.
 D.finally block.
 
>[!NOTE]- Ans
>C
 
3. Consider the class below:
```java linenos
public class Test
{
   public static void main(String[] args)
   {
      int[] a = {99, 22, 11, 3, 11, 55, 44, 88, 2, -3};
      int result = 0;
      for (int i = 0; i < a.length; i++)
      {
         if (a[i] > 30)
            result += a[i];
      } 
      System.out.printf("Result is: %d%n", result);
   } 
} 
```

The output of this Java program will be:
 A.Result is: 286.
 B.Result is: 280.
 C.Result is: 154.
 D.Result is: 332.

>[!NOTE]- Ans
>A

4. Which of the following statements is false?
 A.All exceptions must derive from the class Throwable.
 B.The string returned from class Throwable’s getMessage method contains the name of the exception’s class.
 C.The class Throwable provides the method getStackTrace that outputs the stack trace to the standard error stream.
 D.The class Throwable provides the method getMessage that returns the descriptive string stored in an exception.

>[!NOTE]- Ans
>C

5. Which of the following is the escape character?
 A."
 B.\*
 C.\\
 D.\\n
 
>[!NOTE]- Ans
>C

6. Which statement is false?
 A.enum constants are implicitly final and static. 
 B.An enum constructor cannot be overloaded. 
 C.An enum declaration is a comma-separated list of enum constants and may optionally include other components of traditional classes, such as constructors, fields and methods.
 D.Any attempt to create an object of an enum type with operator new results in a compilation error.

>[!NOTE]- Ans
>B

7. Which of the following will not help prevent infinite loops?
 A.If the loop is counter-controlled, the body of the loop should increment or decrement the counter as needed. 
 B.Ensure that the header of a for or while statement is not followed by a semicolon.
 C.Include braces around the statements in a do…while statement.
 D.If the loop is sentinel-controlled, ensure that the sentinel value is input eventually.
 
>[!NOTE]- Ans
>C
>B: while(i<3);{}

8. The default implementation of method clone of Object performs a \_\_\_\_\_\_\_\_.
 A.deep copy.
 B.empty copy.
 C.full copy.
 D.shallow copy.

>[!NOTE]- Ans
>D

9. Which of the following statements is true?
 A.Constructors can specify parameters but not return types.
 B.Constructors cannot specify parameters but can specify return types.
 C.Constructors can specify neither parameters nor return types.
 D.Constructors can specify parameters and return types.

>[!NOTE]- Ans
>A

10. When a method terminates, the values of its local variables are \_\_\_\_\_\_\_\_.
 A.saved
 B.restored
 C.lost
 D.copied

>[!NOTE]- Ans
>C

11. Which of the following exceptions is a checked exception?
 A.InputMismatchException.
 B.IOException.
 C.RuntimeException.
 D.ArithmeticException.

>[!NOTE]- Ans
>B

12. In the catch block below, what is e?

```java linenos
catch (ArithmeticException e) 
{ 
    System.err.printf(e); 
} 
```

 A.The type of the exception being caught.
 B.The name of catch block’s exception parameter.
 C.A finally block.
 D.An exception handler.
 
>[!NOTE]- Ans
>B

13. Which of the following statements is true?
 A.Always create your own exception clases.
 B.Like any other class, an exception class can contain fields and methods.
 C.Using existing exceptions makes the program less robust.
 D.The new exception class should extend RuntimeException if the program should be required to handle the exception.

>[!NOTE]- Ans
>B

14. Which of the following is not a valid Java identifier?

 A.m\_x
 B.$\_AAA. 
 C.my Value
 D.width

>[!NOTE]- Ans
>C

15. The \_\_\_\_\_\_\_\_\_ of a class are also called the public services or the public interface that the class provides to its clients.

 A.public constructors.
 B.public instance variables.
 C.All of the above.
 D.public methods.

>[!NOTE]- Ans
>D

16. Which of the following statements is false?

 A.Reuse helps you build more reliable and effective systems, because existing classes and components often have undergone extensive testing, debugging and performance tuning. 
 B.Avoid reinventing the wheel—use existing high-quality pieces wherever possible. This software reuse is a key benefit of object-oriented programming.
 C.Each class can be used only once to build many objects. 
 D.Just as the notion of interchangeable parts was crucial to the Industrial Revolution, reusable classes are crucial to the software revolution that has been spurred by object technology.

>[!NOTE]- Ans
>C

17. After a finally block has finished executing (and there are no exceptions to be handled), \_\_\_\_\_\_\_\_.

 A.control proceeds to the first statement after the last catch block.
 B.the application exits.
 C.control returns to the throw point.
 D.control proceeds to the first statement after the finally block.

>[!NOTE]- Ans
>D

18. Which of the following statements is true?
 A.Logic errors are caught by the compiler. Syntax errors have effects at execution time.
 B.Both syntax errors and logic errors are caught by the compiler.
 C.Syntax errors are caught by the compiler. Logic errors have effects at execution time.
 D.Both syntax errors and logic errors have effects at execution time.

>[!NOTE]- Ans
>C

19. The default equals implementation of class Object determines:

 A.whether two objects have the same instance variable values. 
 B.whether two references have the same type.
 C.whether two references refer to the same object in memory.
 D.whether two objects have the same instance variables.

>[!NOTE]- Ans
>C

20. Polymorphism allows for specifics to be dealt with during:

 A.execution.
 B.programming.
 C.compilation.
 D.debugging.

>[!NOTE]- Ans
>A
>Polymorphism允許在執行時期根據物件的實際類型來決定使用哪個方法

21. A(n) \_\_\_\_\_\_\_ class cannot be instantiated.
 A.abstract.
 B.polymorphiC. 
 C.concrete.
 D.final.

>[!NOTE]- Ans
>A

22.Consider integer array values, which contains 5 elements. Which statements successfully swap the contents of the array at index 3 and index 4?

 A.
```java linenos
int temp = values[3];
values[3] = values[4];
values[4] = temp;
```
 B.
```java linenos
values[4] = values[3];
values[3] = values[4];
```
 C.
 ```java linenos
int temp = values[3];
values[3] = values[4];
values[4] = values[3];
```
 D.
 ```java linenos
values[3] = values[4];
values[4] = values[3];
```
   
>[!NOTE]- Ans
>A

23. If the desired Object is not found, binarySearch returns \_\_\_\_\_\_\_\_\_\_.

 A. a negative value
 B. zero
 C. an ObjectNotFoundError.
 D. a positive value
 
>[!NOTE]- Ans
>A
>因為binarySearch方法會回傳找到的元素的索引，如果找不到就會回傳 (-(插入點) - 1) ，其中插入點是指當前元素不存在於陣列中時，可插入元素>位置。因此回傳的值一定是負數，而非負值或0

24. Consider the abstract superclass below:

```java linenos
public abstract class Foo
{
   private int A;   public int b;
   public Foo(int aVal, int bVal)
   {
      a = aVal;
      b = bVal;
   }
   public abstract int calculate();
} 
```

Any concrete subclass that extends class Foo:
 A.Must implement a method called calculate.
 B.Both (a) and (b).
 C.Will not be able to access the instance variable A. 
 D.Neither (a) nor (b).

>[!NOTE]- Ans
>AC

25. Which of the following will count down from 10 to 1 correctly?
 A.for (int j = 10; j <= 1; j++)
 B.for (int j = 1; j <= 10; j++)
 C.for (int j = 10; j >= 1; j--)
 D.for (int j = 10; j > 1; j--)

>[!NOTE]- Ans
>C

26. How many times is the body of the loop below executed?

```java linenos
int counter = 1.
while (counter > 20) 
{
   // body of loop
   counter = counter - 1.
} // end while
```

 A.20.
 B.19.
 C.0.
 D.21.

>[!NOTE]- Ans
>C

27. Which statement is false?

 A.A class is an instance of its object.
 B.A class is to an object as a blueprint is to a house.
 C.Classes are reusable software components.
 D.Performing a task in a program requires a method.

>[!NOTE]- Ans
>A

28. Which superclass members are inherited by all subclasses of that superclass?

 A.private constructors.
 B.protected constructors.
 C.private instance variables and methods.
 D.protected instance variables and methods.

>[!NOTE]- Ans
>D

29. A constructor cannot:

 A.be overloaded. 
 B.initialize variables to their defaults.
 C.specify return types or return values.
 D.have the same name as the class.

>[!NOTE]- Ans
>C

30. What happens when this is used in a constructor’s body to call another constructor of the same class if that call is not the first statement in the constructor?

 A.A logic error occurs.
 B.A compilation error occurs.
 C.A runtime error occurs.
 D.Nothing happens. The program compiles and runs.

>[!NOTE]- Ans
>D

31. When method printf requires multiple arguments, the arguments are separated with \_\_\_\_\_\_\_\_.
 A.colons (:).
 B.semicolons (;).
 C.periods (.).
 D.commas (,).

>[!NOTE]- Ans
>D

32. The control variable of a counter-controlled loop should be declared as \_\_\_\_\_\_\_\_to prevent errors.

 A.Any of the above.
 B.float. 
 C.double.
 D.int.

>[!NOTE]- Ans
>D

33. Overloaded methods always have the same \_\_\_\_\_\_\_\_\_.

 A.order of the parameters 
 B.return type
 C.number of parameters
 D.method name

>[!NOTE]- Ans
>D

34. Consider the classes below, declared in the same file:


```java linenos
class A.
{
   int a.
   public A() 
   {
      a = 7;
   }
}

class B extends A.
{
   int b;
   public B() 
   {
		b = 8;
   }	
}
```

Which of the statements below is false?
 A.After the constructor for class B executes, the variable a will have the value 7.
 B.A reference of type A can be treated as a reference of type B. 
 C.After the constructor for class B executes, the variable b will have the value 8.
 D.Both variables a and b are instance variables.

>[!NOTE]- Ans
>B

35. Which set of statements totals the values in two-dimensional int array items?

 A.
```java lines
int total = 0;
for (int subItems : items)
   for (int item : subItems)
      total += item;
```
 B.
```java linenos
int total = 0;
for (int item: int[] subItems : items)
   total += item;
```
 C.
 ```java linenos
int total = 0;
for (int[] subItems : items)
   for (int item : subItems)
      total += item;
```
 D.
 ```java linenos
int total = 0;
for (int[] subItems : items)
   for (int item : items)
      total += item;
```

>[!NOTE]- Ans
>C

36. Which of the following statements is false?

 A.The finally block and try block can appear in any order.
 B.A finally block is placed after the last catch block.
 C.A finally block is optional.
 D.A finally block typically releases resources acquired in the corresponding try block.

>[!NOTE]- Ans
>A

37. Which of the following statements is false?

 A.The BigDecimal method format receives a double argument and returns a BigDecimal object that represents the exact value specied. 
 B.An application that requires precise floating-point calculations such as those in financial applications should use class BigDecimal from package java.math.
 C.We use class NumberFormat for formatting numeric values as locale-specific strings.
 D.In the U.S, locale, the value 15467.82 would be formatted as "15,467.82", whereas in many European locales it would be formatted as "15.467,56".

>[!NOTE]- Ans
>A: valueOf method receives double

38. Which of the following data items are arranged from the smallest to the largest in the data hierarchy.
 A.bits, characters, fields, records, files.
 B.records, characters, fields, bits, files.
 C.fields, characters, bits, files, records.
 D.bits, files, fields, records, characters.

>[!NOTE]- Ans
>A

39. Which of the following statements is false?

 A.Attributes are specified by the class’s methods.
 B.A bank-account object would likely have a balance attribute that represents the amount of money in the account.
 C.Each bank-account object knows the balance in the account it represents, but not the balances of the other accounts in the bank. 
 D.An object's attributes are specified as part of the object’s class.

>[!NOTE]- Ans
>A

40. End-of-line comments that should be ignored by the compiler are denoted using

 A.Two forward slashes ( // ).
 B.A slash and a star ( /* ).
 C.Three forward slashes ( /// ).
 D.A slash and two stars ( /** ).

>[!NOTE]- Ans
>A

41. Which of the following statements is true?

 A.The argument types in the method call must be identical to the types of the corresponding parameters in the method’s declaration.
 B.Local variables are automatically initialized. 
 C.The default value for an instance variable of type String is void.
 D.Every instance variable has a default initial value—a value provided by Java when you do not specify the instance variable’s initial value.

>[!NOTE]- Ans
>A
>null 不算預設值

42. Which of the following statements is true? 

 A.The private members of a class are directly accessible to the clients of a class.
 B.None of the above is true.
 C.Methods and instance variables can both be either public or private.
 D.Information hiding is achieved by restricting access to class members via keyword public.

>[!NOTE]- Ans
>C

43. Which of the following initializer lists would correctly set the elements of array n?

 A.array n[int] = {1, 2, 3, 4, 5};.
 B.int n = new int(1, 2, 3, 4, 5);.
 C.int[] n = {1, 2, 3, 4, 5};.
 D.int n[5] = {1; 2; 3; 4; 5};.

>[!NOTE]- Ans
>C

44. Composition is sometimes referred to as a(n) \_\_\_\_\_\_\_\_.

 A.is-a relationship
 B.one-to-many relationship
 C.many-to-one relationship
 D.has-a relationship

>[!NOTE]- Ans
>D

45. Which of the following is false?

 A.A static method must be used to access private static instance variables.
 B.A static method can be accessed even when no objects of its class have been instantiated. 
 C.A static method has no this reference.
 D.A static method can call instance methods directly.

>[!NOTE]- Ans
>D

46. Which statement below could be used to simulate the outputs of rolling a six-sided die? Suppose randomNumbers is a SecureRandom object.

 A.3 + randomNumbers.nextInt(3); 
 B.1 + randomNumbers.nextInt(2); 
 C.6 + randomNumbers.nextInt(1); 
 D.1 + randomNumbers.nextInt(6);

>[!NOTE]- Ans
>D

47. Which is a correct static method call of Math class method sqrt?
 
 A.sqrt(900);
 B.Math math = new Math(); math.sqrt(900);
 C.math.sqrt(900);
 D.Math.sqrt(900);

>[!NOTE]- Ans
>D

48. Consider the following Java statements:

```java linenos
int x = 9;
double y = 5.3;
result = calculateValue(x, y);
```


Which of the following statements is false?
 A.x and y are arguments.
 B.x and y are parameters.
 C.Copies of x and y are passed to the method calculateValue.
 D.A method is called with its name and parentheses.

>[!NOTE]- Ans
>B

49. Which of the following statements is false?

 A.Variables declared in the body of a particular method are local variables and can be used only in that method. 
 B.A method’s parameters are local variables of the method. 
 C.Every method’s body is delimited by left and right braces ({ and }).
 D.Keyword null indicates that a method will perform a task but will not return any information.

>[!NOTE]- Ans
>D void

50. Which statement is false?

 A.A ListIterator accesses the elements of a List.
 B.ArrayLists execute faster than Vectors because they are not thread safe.
 C.A LinkedList is a linked list implementation of a List.
 D.Class ArrayList is a fixed-size array. 

>[!NOTE]- Ans
>D dyamic

51. Which of the following statements about the switch statement is false?

 A.You cannot use a String in a switch statement’s default case label.
 B.You can use Strings in a switch statement’s controlling expression.
 C.You can use a String in a switch statement's case label.
 D.You can use a comma-separated list of Strings in a switch statement’s case label. 

>[!NOTE]- Ans
>D

52. Which of the following is false?

 A.Memory leaks using Java are rare because of automatic garbage collection.
 B.Method finalize does not take parameters and has return type void. 
 C.The garbage collector reclaims unused memory.
 D.Objects are marked for garbage collection by method finalize.

>[!NOTE]- Ans
>D

53. Which of the following statements is false?

 A.Dramatically different classes can often meaningfully implement the same interface.
 B.Method toString can be invoked implicitly on any object.
 C.With inheritance, classes and their inherited classes tend to be very similar.
 D.References to interface types do not have access to method toString.

>[!NOTE]- Ans
>D

54. Information is passed to a method in \_\_\_\_\_\_\_\_.

 A.the arguments to the method
 B.the method name
 C.that method’s return
 D.the method body

>[!NOTE]- Ans
>A

55. A class that implements an interface but does not declare all of the interface’s methods must be declared \_\_\_\_\_\_\_\_.

 A.abstract.
 B.publiC. 
 C.final.
 D.interface.

>[!NOTE]- Ans
>A

56.Collections method sort that accepts a List as an argument. It sorts the List elements, which must implement the \_\_\_\_\_\_\_\_\_\_ interface.
 
 A.Comparable.
 B.Comparator.
 C.Ordering.
 D.Compare.

>[!NOTE]- Ans
>A

57. Which of the following statements is false?

 A.If the class you're inheriting from declares instance variables as private, the inherited class can access those instance variables directly.
 B.A class's instance variables are normally declared private to enforce good software engineering.
 C.A class can directly inherit from class Object.
 D.It's often much more efficient to create a class by inheriting from a similar class than to create the class by writing every line of code the new class requires.

>[!NOTE]- Ans
>A

58. In an expression containing values of the types int and double, the \_\_\_\_\_\_\_\_ values are \_\_\_\_\_\_\_\_ to \_\_\_\_\_\_\_\_ values for use in the expression.

 A.int, promoted, double.
 B.int, demoted, double.
 C.double, promoted, int.
 D.double, demoted, int.

>[!NOTE]- Ans
>A

59. Declaring instance variables \_\_\_\_\_\_\_\_ is known as data hiding or information hiding.

 A.private 
 B.static
 C.secure 
 D.masked 

>[!NOTE]- Ans
>A

60. Which statement best describes the relationship between superclass and subclass types?

 A.A subclass reference cannot be assigned to a superclass variable and a superclass reference cannot be assigned to a subclass variable.
 B.A subclass reference can be assigned to a superclass variable and a superclass reference can be assigned to a subclass variable.
 C.A superclass reference can be assigned to a subclass variable, but a subclass reference cannot be assigned to a superclass variable.
 D.A subclass reference can be assigned to a superclass variable, but a superclass reference cannot be assigned to a subclass variable.

>[!NOTE]- Ans
>D

61. Maps allocate keys to values and cannot contain duplicate keys, i.e., the key-to-value mapping is a \_\_\_\_\_\_\_\_\_\_ mapping.

 A.many-to-one.
 B.one-to-one.
 C.one-to-many.
 D.many-to-many.

>[!NOTE]- Ans
>B

62. When a subclass constructor calls its superclass constructor, what happens if the superclass’s constructor does not assign a value to an instance variable?

 A.The program compiles and runs because the instance variables are initialized to their default values.
 B.A syntax error occurs.
 C.A run-time error occurs.
 D.A compile-time error occurs.

>[!NOTE]- Ans
>A

63. Which of the following statements about abstract superclasses is true?

 A.abstract superclasses may contain data. 
 B.abstract superclasses must declare all methods as abstract.
 C.abstract superclasses must declare all data members not given values as abstract.
 D.abstract superclasses may not contain implementations of methods.

>[!NOTE]- Ans
>D

64. When a superclass variable refers to a subclass object and a method is called on that object, the proper implementation is determined at execution time. What is the process of determining the correct method to call?
 
 A.early binding.
 B.non-binding.
 C.on-time binding.
 D.late binding.

>[!NOTE]- Ans
>D

65. Arrays are \_\_\_\_\_\_\_\_. 

 A.data structures that contain up to 10 related data items
 B.variable-length entities
 C.used to draw a sequence of lines, or “rays”
 D.fixed-length entities

>[!NOTE]- Ans
>D

66. To create the best solutions, you should follow a detailed \_\_\_\_\_\_\_\_  process for determining your project’s \_\_\_\_\_\_\_\_ (i.e., defining what the system is supposed to do) and developing a \_\_\_\_\_\_\_\_ that satisfies them (i.e., specifying how the system should do it).

 A.requirements, design, analysis
 B.analysis, requirements, design
 C.design, requirements, analysis
 D.analysis, design, set of requirements

>[!NOTE]- Ans
>A

67. When must a program explicitly use the this reference?

 A.Accessing a private variable.
 B.Accessing a local variable.
 C.Accessing an instance variable that is shadowed by a local variable.
 D.Accessing a public variable.

>[!NOTE]- Ans
>A

68. What is the value of result after the following Java statements execute (assume all variables are of type int)?

```java linenos
a = 4;
b = 12;
c = 37;
d = 51;
result = d % a * c + a % b + a;
```
 
 A.127.
 B.11. 
 C.51.
 D.59.
 
>[!NOTE]- Ans
>A

69. Which of the following statements is false?

 A.Variables of types byte, char, short, int, long, float and double are initialized to 0.
 B.Primitive-type instance variables are initialized by default.
 C.A primitive-type variable can store exactly one value of its declared type at a time.
 D.Variables of type boolean are initialized to true.

>[!NOTE]- Ans
>A

70. Which of the following statements is false?

 A.Every class declaration contains keyword class followed immediately by the class’s name.
 B.Each class declaration that begins with the access modifier private must be stored in a file that has the same name as the class and ends with the .java filename extension.
 C.Class, method and variable names are identifiers.
 D.An object has attributes that are implemented as instance variables and carried with it throughout its lifetime.

>[!NOTE]- Ans
>B

71. An import declaration is not required if you always refer to a class with its \_\_\_\_\_\_\_\_ name, which includes its package name and class name.

 A.fully qualified name
 B.default package
 C.compile-time
 D.paired

>[!NOTE]- Ans
>A

72. Consider the code segment below. Which of the following statements is false?


```java linenos
int[] g;
g = new int[23];
```

 A.The second statement creates the array.
 B.g is a reference to an array of integers.
 C.The value of g\[3] is -1. 
 D.The first statement declares an array reference.

>[!NOTE]- Ans
>C

73. If the superclass contains only abstract method declarations, the superclass is used for \_\_\_\_\_\_\_\_.

 A.Neither.
 B.Both.
 C.interface inheritance.
 D.implementation inheritance.

>[!NOTE]- Ans
>B

74. When overriding a superclass method and calling the superclass version from the subclass method, failure to prefix the superclass method name with the keyword super and a dot (.) in the superclass method call causes \_\_\_\_\_\_\_\_.

 A.a syntax error.
 B.a compile-time error.
 C.infinite recursion.
 D.a runtime error.

>[!NOTE]- Ans
>C

75. Which statement is false?

 A.Collections discourage software reuse because they are non-portable.
 B.Collections are carefully constructed for rapid execution and efficient use of memory.
 C.A collection is an object that can hold references to other objects.
 D.The collection interfaces declare the operations that can be performed on each type of collection.

>[!NOTE]- Ans
>A

76. If a class does not define constructors, the compiler provides a default constructor with no parameters, and the class’s instance variables are initialized to \_\_\_\_\_\_\_\_. 

 A.null*
 B.their default values
 C.zero
 D.false

>[!NOTE]- Ans
>B

77. Which of the following are types of assertions?
 A.Preconditions.
 B.Postconditions.
 C.Preconditions and Postconditions. 
 D.Conditions in control statements.

>[!NOTE]- Ans
>C

78.Superclass methods with this level of access cannot be called from subclasses.

 A.protected. 
 B.private.
 C.package. 
 D.public.
 
>[!NOTE]- Ans
>B


79. Which expression is equivalent to if (!(grade == sentinelValue))?

 A.if (grade != sentinelValue)
 B.! if (grade !== sentinelValue)
 C.if (grade !== sentinelValue)
 D.if (grade == sentinelValue)

>[!NOTE]- Ans
>A

80. LinkedList method listIterator returns a(n) \_\_\_\_\_\_\_\_\_\_.
 A.Iterator.
 B.bidirectional iterator.
 C.List.
 D.sub list.

>[!NOTE]- Ans
>B

81. Which of the following is a double-selection control statement?

 A.do…while
 B.if
 C.if…else
 D.for

>[!NOTE]- Ans
>C

82. Which of the following is not included in an exception’s stack trace?

 A.Instructions on handling the exception.
 B.A descriptive message for the exception.
 C.The name of the exception.
 D.The method-call stack at the time the exception occurred.

>[!NOTE]- Ans
>A

83. If the catch-or-declare requirement for a checked exception is not satisfied \_\_\_\_\_\_\_\_.

 A.a stack trace will be displayed indicating the exception that has occurred and where it occurred. 
 B.a stack trace will be displayed, along with a message indicating that the exception must be caught.
 C.the compiler will issue an error message indicating that the exception must be caught or declared. 
 D.the compiler will issue an error message indicating that the exception must be caught.

>[!NOTE]- Ans
>C

84. Comparator method compare should return \_\_\_\_\_\_\_\_ if the first argument is greater than the second argument.

 A.a positive int value.
 B.a String.
 C.a negative int value.
 D.zero.

>[!NOTE]- Ans
>A

85. Classes and methods are declared final for all but the following reasons:
 A.final methods and classes prevent further inheritance.
 B.final methods allow inlining the code.
 C.final methods can improve performance.
 D.final methods are static.

>[!NOTE]- Ans
>D

86. Every class in Java, except \_\_\_\_\_\_\_\_, extends an existing class.

 A.Class.
 B.String.
 C.Object.
 D.Integer.

>[!NOTE]- Ans
>C

87. The classes and interfaces which comprise the collections framework are members of package \_\_\_\_\_\_\_\_.

 A.java.collections.
 B.java.collection.
 C.javax.swing.
 D.java.util. 

>[!NOTE]- Ans
>D

88.Java supports type inferencing with the <> notation in statements that declare and create generic type variables and objects. For example, the following line:

	`List<String> list = new ArrayList<String>();`

can be written as:

 A.List<String\> list = new ArrayList<>();
 B.List<> list = new ArrayList<>();
 C.List<> list = new ArrayList<String\>();
 D.List<String\> list = new ArrayList();

>[!NOTE]- Ans
>A

89. Which statement is false?

 A.Lists use zero-based indices.
 B.A List is sometimes called a sequence.
 C.A List is a Collection.
 D.A List cannot contain duplicate elements.

>[!NOTE]- Ans
>D

90. Which of the following operators associates from left to right?
 A.?:
 B./
 C.%=
 D.=

>[!NOTE]- Ans
>B