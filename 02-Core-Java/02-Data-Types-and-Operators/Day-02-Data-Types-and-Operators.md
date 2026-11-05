# Day 02 – Java Data Types and Operators

**Learning Track:** Core Java  
**Topic:** Data Types and Operators  
**Folder:** 02-Data-Types-and-Operators  
**Objective:** Understand Java data types, memory concepts, type conversion, operators and their practical usage.

---

## 1. Introduction to Data Types

### 1. What is a data type in Java?

A data type specifies the kind of value a variable can store. It determines the operations that can be performed on that value and the range of values it can represent.

Example:

```java
int age = 25;
double salary = 55000.50;
char grade = 'A';
boolean isActive = true;
```

### 2. Types of data types

Java data types are divided into two main categories:

**A. Primitive data types**

Java has eight primitive data types:

| Data Type | Size | Example |
|---|---:|---|
| byte | 8 bits | `byte age = 25;` |
| short | 16 bits | `short number = 1000;` |
| int | 32 bits | `int salary = 50000;` |
| long | 64 bits | `long population = 9000000L;` |
| float | 32 bits | `float price = 99.5f;` |
| double | 64 bits | `double amount = 999.99;` |
| char | 16 bits | `char grade = 'A';` |
| boolean | JVM-dependent representation | `boolean valid = true;` |

Note: Java specifies the precision and value characteristics of primitive types, but does not specify a universal storage size for boolean.

**B. Non-primitive data types**

Examples:
- String
- Arrays
- Classes
- Interfaces
- Enums

These are reference types. Variables of reference types hold references to objects or arrays.

### 3. Difference between primitive and non-primitive data types

| Primitive | Non-primitive |
|---|---|
| Built into Java | Includes classes, arrays and interfaces |
| Stores a primitive value | Stores an object or array reference |
| Has predefined value ranges | Depends on the type |
| Cannot be null | Can be null |
| No methods | Objects can expose methods |

---

## 2. Primitive Data Types in Detail

### 4. Integer data types

Java provides four integer types:

- byte: -128 to 127
- short: -32,768 to 32,767
- int: -2,147,483,648 to 2,147,483,647
- long: 64-bit signed integer

Example:

```java
public class IntegerTypes {
    public static void main(String[] args) {
        byte age = 25;
        short year = 2026;
        int salary = 50000;
        long population = 8000000000L;

        System.out.println(age);
        System.out.println(year);
        System.out.println(salary);
        System.out.println(population);
    }
}
```

Important: An integer literal is normally an int. Use `L` or `l` for long literals. Prefer uppercase `L`.

### 5. Floating-point data types

- float: 32-bit floating-point value.
- double: 64-bit floating-point value.

Example:

```java
float price = 99.50f;
double salary = 75000.75;

System.out.println(price);
System.out.println(salary);
```

Important:
- Decimal literals are double by default.
- Use `f` or `F` for float literals.
- Floating-point arithmetic can introduce precision errors.
- For financial calculations, consider BigDecimal instead of float or double.

### 6. Character data type

The char type stores a single UTF-16 code unit.

Example:

```java
char grade = 'A';
char symbol = '$';
char number = '7';

System.out.println(grade);
System.out.println(symbol);
System.out.println(number);
```

A char uses single quotes, whereas String uses double quotes.

### 7. Boolean data type

A boolean stores either true or false.

Example:

```java
boolean isLoggedIn = true;
boolean isAdmin = false;

System.out.println(isLoggedIn);
System.out.println(isAdmin);
```

Boolean values are commonly used in conditions and validation logic.

---

## 3. Type Conversion and Type Casting

### 8. What is type conversion?

Type conversion means converting a value from one data type to another.

Two main types:

1. Widening conversion
2. Narrowing conversion

### 9. Widening conversion (Implicit casting)

Converting a smaller compatible numeric type into a larger compatible numeric type.

Example:

```java
public class WideningExample {
    public static void main(String[] args) {
        int number = 100;
        double result = number;

        System.out.println(result);
    }
}
```

Output:

```text
100.0
```

### 10. Narrowing conversion (Explicit casting)

Converting a larger numeric type into a smaller numeric type.

Example:

```java
public class NarrowingExample {
    public static void main(String[] args) {
        double price = 99.99;
        int result = (int) price;

        System.out.println(result);
    }
}
```

Output:

```text
99
```

Important: Narrowing can lose fractional or significant information.

### 11. Difference between widening and narrowing

| Widening | Narrowing |
|---|---|
| Smaller to larger compatible type | Larger to smaller type |
| Usually implicit | Requires explicit cast |
| Generally preserves the value | Can lose information |
| Example: int to double | Example: double to int |

### 12. Type promotion in expressions

Java automatically promotes smaller integral types such as byte, short and char to int when used in most arithmetic expressions.

Example:

```java
byte a = 10;
byte b = 20;

// byte result = a + b; // Compilation error
int result = a + b;

System.out.println(result);
```

To store the result in a byte, an explicit cast is required:

```java
byte result = (byte) (a + b);
```

---

## 4. Wrapper Classes and Autoboxing

### 13. What are wrapper classes?

Wrapper classes provide object representations of primitive data types.

| Primitive | Wrapper |
|---|---|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

### 14. What is autoboxing?

Autoboxing automatically converts a primitive value into its corresponding wrapper object.

```java
int number = 100;
Integer object = number;

System.out.println(object);
```

### 15. What is unboxing?

Unboxing automatically converts a wrapper object into its corresponding primitive value.

```java
Integer object = 200;
int number = object;

System.out.println(number);
```

### 16. Why are wrapper classes useful?

- Collections such as ArrayList use objects rather than primitive types.
- They provide utility methods for conversion and comparison.
- They can represent the absence of a value using null.
- They are useful in generic programming.

Important: Unboxing a null wrapper object causes NullPointerException.

---

## 5. Operators in Java

### 17. What are operators?

Operators are symbols that perform operations on operands.

Example:

```java
int result = 10 + 20;
```

Here, `+` is the operator and 10 and 20 are operands.

### 18. Types of operators

Java operators include:

1. Arithmetic operators
2. Unary operators
3. Relational operators
4. Logical operators
5. Assignment operators
6. Bitwise operators
7. Shift operators
8. Ternary operator
9. instanceof operator

### 19. Arithmetic operators

| Operator | Meaning | Example |
|---|---|---|
| + | Addition | a + b |
| - | Subtraction | a - b |
| * | Multiplication | a * b |
| / | Division | a / b |
| % | Modulus | a % b |

Example:

```java
int a = 20;
int b = 10;

System.out.println(a + b);
System.out.println(a - b);
System.out.println(a * b);
System.out.println(a / b);
System.out.println(a % b);
```

Important: Integer division discards the fractional part.

### 20. Unary operators

Unary operators work with one operand.

| Operator | Meaning |
|---|---|
| + | Unary plus |
| - | Unary minus |
| ++ | Increment |
| -- | Decrement |
| ! | Logical complement |
| ~ | Bitwise complement |

### 21. Pre-increment and post-increment

**Pre-increment:** Increments the value before using it in the expression.

**Post-increment:** Uses the current value first and increments afterward.

Example:

```java
int a = 10;
int b = ++a;

System.out.println(a); // 11
System.out.println(b); // 11

int x = 10;
int y = x++;

System.out.println(x); // 11
System.out.println(y); // 10
```

### 22. Relational operators

Relational operators compare two values and return a boolean result.

| Operator | Meaning |
|---|---|
| == | Equal to |
| != | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |

Example:

```java
int age = 25;

System.out.println(age >= 18);
System.out.println(age == 25);
System.out.println(age < 18);
```

### 23. Logical operators

| Operator | Meaning |
|---|---|
| && | Logical AND |
| || | Logical OR |
| ! | Logical NOT |

Example:

```java
int age = 25;
boolean hasId = true;

System.out.println(age >= 18 && hasId);
System.out.println(age >= 18 || hasId);
System.out.println(!hasId);
```

### 24. Short-circuit evaluation

Java uses short-circuit evaluation with `&&` and `||`.

- With `&&`, if the first condition is false, the second condition is not evaluated.
- With `||`, if the first condition is true, the second condition is not evaluated.

Example:

```java
int number = 10;

if (number > 20 && ++number > 5) {
    System.out.println("Condition true");
}

System.out.println(number); // 10
```

This is useful in null checks and safe condition evaluation.

### 25. Difference between && and &

- `&&` is short-circuit logical AND.
- `&` can perform logical AND on boolean operands but evaluates both operands.
- `&` also performs bitwise AND on integral operands.

Similarly, `||` short-circuits while `|` evaluates both boolean operands.

### 26. Assignment operators

| Operator | Example | Equivalent |
|---|---|---|
| = | a = 10 | Assign 10 |
| += | a += 5 | a = a + 5 |
| -= | a -= 5 | a = a - 5 |
| *= | a *= 2 | a = a * 2 |
| /= | a /= 2 | a = a / 2 |
| %= | a %= 2 | a = a % 2 |

### 27. Bitwise operators

Bitwise operators operate on individual bits of integral values.

| Operator | Meaning |
|---|---|
| & | Bitwise AND |
| \| | Bitwise OR |
| ^ | Bitwise XOR |
| ~ | Bitwise complement |

Example:

```java
int a = 5; // 0101
int b = 3; // 0011

System.out.println(a & b); // 1
System.out.println(a | b); // 7
System.out.println(a ^ b); // 6
System.out.println(~a);    // -6
```

### 28. Shift operators

| Operator | Meaning |
|---|---|
| << | Left shift |
| >> | Signed right shift |
| >>> | Unsigned right shift |

Example:

```java
int number = 8;

System.out.println(number << 1);  // 16
System.out.println(number >> 1);  // 4
System.out.println(number >>> 1); // 4
```

### 29. Ternary operator

The ternary operator is a compact alternative to a simple if-else expression.

Syntax:

```java
condition ? expression1 : expression2;
```

Example:

```java
int age = 20;

String result = age >= 18 ? "Eligible" : "Not Eligible";

System.out.println(result);
```

### 30. instanceof operator

The instanceof operator checks whether an object is an instance of a particular type.

Example:

```java
String name = "Java";

System.out.println(name instanceof String); // true
```

It is commonly used when working with inheritance and object references.

---

## 6. Operator Precedence

Operator precedence determines the order in which operators are evaluated.

A simplified precedence order from higher to lower:

1. Postfix: `expr++`, `expr--`
2. Unary: `++`, `--`, `!`, `~`
3. Multiplicative: `*`, `/`, `%`
4. Additive: `+`, `-`
5. Shift: `<<`, `>>`, `>>>`
6. Relational: `<`, `>`, `<=`, `>=`, `instanceof`
7. Equality: `==`, `!=`
8. Bitwise AND: `&`
9. Bitwise XOR: `^`
10. Bitwise OR: `|`
11. Logical AND: `&&`
12. Logical OR: `||`
13. Ternary: `?:`
14. Assignment: `=`, `+=`, `-=`

Example:

```java
int result = 10 + 5 * 2;

System.out.println(result); // 20
```

Multiplication executes before addition.

Use parentheses to make complex expressions easier to understand.

---

## 7. Important Interview Questions

1. What are the eight primitive data types in Java?
2. What is the difference between primitive and non-primitive data types?
3. What is the difference between float and double?
4. Why do we use L for long and F for float?
5. What is the difference between widening and narrowing?
6. What happens when we add two byte variables?
7. What are wrapper classes?
8. Explain autoboxing and unboxing.
9. What is the difference between `==` and `equals()`?
10. What is the difference between pre-increment and post-increment?
11. What is the difference between `&&` and `&`?
12. What is short-circuit evaluation?
13. What is the difference between `||` and `|`?
14. What are bitwise operators?
15. What is the difference between `>>` and `>>>`?
16. What is the ternary operator?
17. What is operator precedence?
18. Can we use boolean values in arithmetic operations?
19. What happens when we divide an integer by zero?
20. Why is BigDecimal preferred for financial calculations?

---

## 8. Coding Practice

Complete these programs independently.

### Beginner

1. Declare all eight primitive data types and print their values.
2. Calculate the area of a rectangle.
3. Calculate simple interest.
4. Convert Celsius to Fahrenheit.
5. Demonstrate widening and narrowing conversion.
6. Swap two numbers using a temporary variable.
7. Swap two numbers without a temporary variable.
8. Find the quotient and remainder of two integers.

### Intermediate

9. Demonstrate pre-increment and post-increment.
10. Find the largest of two numbers using the ternary operator.
11. Check whether a person is eligible to vote using logical operators.
12. Demonstrate short-circuit evaluation.
13. Demonstrate bitwise AND, OR and XOR.
14. Demonstrate left shift and right shift.
15. Convert an Integer wrapper object into an int.
16. Demonstrate operator precedence using different expressions.

### Interview-level practice

17. Predict the output of complex increment expressions.
18. Explain the output of mixed int, double and float expressions.
19. Find the result of nested ternary expressions.
20. Write a program to check whether a number is even using bitwise AND.
21. Swap two integers using XOR and explain its limitations.
22. Demonstrate the difference between `&&` and `&` using method calls.

---

## 9. QA Automation Real-Time Applications

Java data types and operators are frequently used in Selenium and API automation.

**Example 1: Validate page title**

```java
String actualTitle = "Login Page";
String expectedTitle = "Login Page";

boolean isTitleCorrect = actualTitle.equals(expectedTitle);

System.out.println(isTitleCorrect);
```

**Example 2: Validate API status code**

```java
int actualStatusCode = 200;
int expectedStatusCode = 200;

boolean isStatusCorrect = actualStatusCode == expectedStatusCode;
```

**Example 3: Validate response time**

```java
long responseTime = 1500;
long maxResponseTime = 2000;

boolean isWithinLimit = responseTime <= maxResponseTime;
```

**Example 4: Validate user eligibility**

```java
int age = 25;
boolean hasValidAccount = true;

boolean eligible = age >= 18 && hasValidAccount;
```

**Example 5: Validate list size**

```java
int actualCount = 10;
int expectedCount = 10;

boolean isCountCorrect = actualCount == expectedCount;
```

---

## 10. Day 02 Completion Checklist

- [ ] Understand all eight primitive types.
- [ ] Understand reference types.
- [ ] Learn primitive data type ranges.
- [ ] Understand widening and narrowing.
- [ ] Understand type promotion.
- [ ] Learn wrapper classes.
- [ ] Understand autoboxing and unboxing.
- [ ] Practise arithmetic and unary operators.
- [ ] Practise relational and logical operators.
- [ ] Understand short-circuit evaluation.
- [ ] Practise assignment and bitwise operators.
- [ ] Understand shift and ternary operators.
- [ ] Learn operator precedence.
- [ ] Complete at least 15 coding programs.
- [ ] Practise interview questions.
- [ ] Push notes and programs to GitHub.

**Expected outcome:** Be able to confidently use Java data types and operators in Selenium automation frameworks, API automation and Java coding interviews.