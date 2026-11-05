# Day 03 – Java Control Statements

**Learning Track:** Core Java  
**Topic:** Control Statements  
**Folder:** 03-Control-Statements  
**Objective:** Understand how to control program execution using conditional statements, loops and branching statements.

---

## 1. Introduction to Control Statements

### 1. What are control statements in Java?

Control statements determine the order in which statements are executed in a Java program.

By default, Java executes statements sequentially, from top to bottom. Control statements allow us to make decisions, repeat operations and change the normal execution flow.

### 2. Types of control statements

Java control statements are broadly classified into three categories:

1. Decision-making or selection statements
2. Looping or iteration statements
3. Jump or branching statements

---

## 2. Decision-Making Statements

Decision-making statements execute different blocks of code depending on whether a condition evaluates to true or false.

### 3. What is an if statement?

The if statement executes a block of code only when the specified condition is true.

Syntax:

```java
if (condition) {
    // Code executes when condition is true
}
```

Example:

```java
public class IfExample {
    public static void main(String[] args) {
        int age = 25;

        if (age >= 18) {
            System.out.println("Eligible to vote");
        }
    }
}
```

### 4. What is an if-else statement?

The if-else statement executes one block when the condition is true and another block when it is false.

Example:

```java
public class IfElseExample {
    public static void main(String[] args) {
        int age = 16;

        if (age >= 18) {
            System.out.println("Eligible to vote");
        } else {
            System.out.println("Not eligible to vote");
        }
    }
}
```

### 5. What is an else-if ladder?

An else-if ladder is used when multiple conditions need to be evaluated sequentially.

Example:

```java
public class ElseIfExample {
    public static void main(String[] args) {
        int marks = 85;

        if (marks >= 90) {
            System.out.println("Grade A");
        } else if (marks >= 75) {
            System.out.println("Grade B");
        } else if (marks >= 50) {
            System.out.println("Grade C");
        } else {
            System.out.println("Fail");
        }
    }
}
```

The first matching condition executes. Remaining conditions are skipped.

### 6. What is a nested if statement?

An if statement inside another if statement is called a nested if.

Example:

```java
public class NestedIfExample {
    public static void main(String[] args) {
        int age = 25;
        boolean hasId = true;

        if (age >= 18) {
            if (hasId) {
                System.out.println("Entry allowed");
            } else {
                System.out.println("ID required");
            }
        } else {
            System.out.println("Entry denied");
        }
    }
}
```

### 7. Difference between if-else and nested if

| if-else | Nested if |
|---|---|
| Selects between alternative blocks | Checks a condition inside another condition |
| Suitable for simple decisions | Suitable for dependent conditions |
| Usually easier to read | Can become complex when deeply nested |

### 8. What is a switch statement?

The switch statement selects one execution path from multiple alternatives based on the value of an expression.

Example:

```java
public class SwitchExample {
    public static void main(String[] args) {
        int day = 3;

        switch (day) {
            case 1:
                System.out.println("Monday");
                break;

            case 2:
                System.out.println("Tuesday");
                break;

            case 3:
                System.out.println("Wednesday");
                break;

            default:
                System.out.println("Invalid day");
        }
    }
}
```

Important points:

- `break` prevents execution from falling through into subsequent cases.
- `default` executes when no case matches.
- Traditional switch supports types such as byte, short, char, int, their wrappers, String and enums.
- long, float, double and boolean are not supported as traditional switch selector types.

### 9. What happens if we do not use break in switch?

Without break, execution can continue into subsequent case labels. This behavior is called fall-through.

Example:

```java
public class SwitchBreakExample {
    public static void main(String[] args) {
        int number = 1;

        switch (number) {
            case 1:
                System.out.println("One");

            case 2:
                System.out.println("Two");

            case 3:
                System.out.println("Three");
                break;

            default:
                System.out.println("Invalid");
        }
    }
}
```

Output:

```text
One
Two
Three
```

### 10. What is the enhanced switch expression?

Modern Java supports switch expressions, which can return a value.

Example:

```java
public class SwitchExpressionExample {
    public static void main(String[] args) {
        int day = 2;

        String result = switch (day) {
            case 1 -> "Monday";
            case 2 -> "Tuesday";
            case 3 -> "Wednesday";
            default -> "Invalid day";
        };

        System.out.println(result);
    }
}
```

Switch expressions were finalized in Java 14.

---

## 3. Looping Statements

Looping statements execute a block of code repeatedly while a specified condition allows it.

### 11. What is a for loop?

A for loop is generally used when the number of iterations is known or controlled by an initialization, condition and update expression.

Syntax:

```java
for (initialization; condition; update) {
    // Statements
}
```

Example:

```java
public class ForLoopExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }
    }
}
```

Execution:

1. Initialization executes once.
2. Condition is checked.
3. If true, loop body executes.
4. Update expression executes.
5. Condition is checked again.
6. Loop terminates when the condition becomes false.

### 12. What is a while loop?

A while loop checks its condition before executing the loop body.

It is useful when the number of iterations is not known in advance.

Example:

```java
public class WhileExample {
    public static void main(String[] args) {
        int i = 1;

        while (i <= 5) {
            System.out.println(i);
            i++;
        }
    }
}
```

### 13. What is a do-while loop?

A do-while loop executes the loop body first and checks the condition afterward.

Therefore, the body executes at least once, even if the condition is initially false.

Example:

```java
public class DoWhileExample {
    public static void main(String[] args) {
        int i = 1;

        do {
            System.out.println(i);
            i++;
        } while (i <= 5);
    }
}
```

### 14. Difference between for, while and do-while

| Feature | for | while | do-while |
|---|---|---|---|
| Condition check | Before execution | Before execution | After execution |
| Minimum execution | Zero times | Zero times | At least once |
| Best suited for | Count-controlled loops | Condition-controlled loops | At-least-once execution |
| Initialization | Usually in loop header | Usually before loop | Usually before loop |

### 15. What is an infinite loop?

An infinite loop continues executing because its termination condition never becomes false.

Example:

```java
while (true) {
    System.out.println("Running continuously");
}
```

Infinite loops are sometimes intentional in server applications, event-processing systems and monitoring processes. They must have a controlled exit mechanism.

### 16. What is a nested loop?

A loop inside another loop is called a nested loop.

Example:

```java
public class NestedLoopExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 3; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

Output:

```text
* * *
* * *
* * *
```

The inner loop completes all its iterations for every iteration of the outer loop.

### 17. What is an enhanced for loop?

The enhanced for loop, also called the for-each loop, is used to iterate over arrays and collections.

Example:

```java
public class EnhancedForExample {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40};

        for (int number : numbers) {
            System.out.println(number);
        }
    }
}
```

Advantages:

- Simple syntax.
- Improves readability.
- Useful for iterating through arrays and collections.

Limitation: It does not directly provide the index, and it is not suitable when you need to modify collection structure during iteration.

---

## 4. Jump or Branching Statements

### 18. What is break?

The break statement terminates the nearest enclosing loop or switch statement.

Example:

```java
public class BreakExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i == 5) {
                break;
            }

            System.out.println(i);
        }
    }
}
```

Output:

```text
1
2
3
4
```

### 19. What is continue?

The continue statement skips the remaining statements in the current loop iteration and proceeds to the next iteration.

Example:

```java
public class ContinueExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            if (i == 3) {
                continue;
            }

            System.out.println(i);
        }
    }
}
```

Output:

```text
1
2
4
5
```

### 20. What is return?

The return statement terminates the execution of a method and optionally sends a value back to its caller.

Example:

```java
public class ReturnExample {

    static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        int result = add(10, 20);
        System.out.println(result);
    }
}
```

A void method can use `return;` without returning a value.

### 21. Difference between break, continue and return

| Statement | Purpose |
|---|---|
| break | Terminates the nearest loop or switch |
| continue | Skips the current loop iteration |
| return | Terminates the current method |

### 22. What is a labeled break?

A labeled break terminates a specified enclosing loop rather than only the nearest loop.

Example:

```java
public class LabeledBreakExample {
    public static void main(String[] args) {

        outer:
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 3; j++) {
                if (i == 2 && j == 2) {
                    break outer;
                }

                System.out.println(i + " " + j);
            }
        }
    }
}
```

### 23. What is a labeled continue?

A labeled continue skips the current iteration of the specified enclosing loop and continues with its next iteration.

Example:

```java
public class LabeledContinueExample {
    public static void main(String[] args) {

        outer:
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 3; j++) {
                if (j == 2) {
                    continue outer;
                }

                System.out.println(i + " " + j);
            }
        }
    }
}
```

---

## 5. Important Differences and Concepts

### 24. Difference between switch and if-else

| switch | if-else |
|---|---|
| Selects among matching case values | Evaluates boolean conditions |
| Useful for fixed alternatives | Useful for ranges and complex conditions |
| Supports supported constant case labels | Supports relational and logical conditions |
| Can use switch expressions | Can use nested conditions |

### 25. Can we use String in switch?

Yes. Java supports String expressions in switch statements.

Example:

```java
String browser = "Chrome";

switch (browser) {
    case "Chrome":
        System.out.println("Chrome browser selected");
        break;

    case "Firefox":
        System.out.println("Firefox browser selected");
        break;

    default:
        System.out.println("Unsupported browser");
}
```

This is useful in Selenium automation when selecting browser configurations.

### 26. Can we use a loop inside another loop?

Yes. This is called a nested loop. It is commonly used for matrices, patterns and multidimensional data.

### 27. Can we use break inside an if statement?

Yes, but only when that if statement is contained within a loop or switch where break is permitted. An if statement by itself cannot be terminated using break.

### 28. Can we use continue inside a switch?

Not as a way to skip a switch case. However, continue can be used in a switch nested inside a loop to continue the enclosing loop.

---

## 6. Real-Time QA Automation Applications

### Example 1: Browser selection using switch

```java
String browser = "Chrome";

switch (browser) {
    case "Chrome":
        System.out.println("Launch Chrome");
        break;

    case "Firefox":
        System.out.println("Launch Firefox");
        break;

    case "Edge":
        System.out.println("Launch Edge");
        break;

    default:
        System.out.println("Unsupported browser");
}
```

### Example 2: Validate multiple test results

```java
int[] statusCodes = {200, 201, 400, 500};

for (int statusCode : statusCodes) {
    if (statusCode >= 400) {
        System.out.println("API failure: " + statusCode);
    } else {
        System.out.println("API success: " + statusCode);
    }
}
```

### Example 3: Retry an operation

```java
int maxAttempts = 3;

for (int attempt = 1; attempt <= maxAttempts; attempt++) {

    System.out.println("Attempt: " + attempt);

    boolean success = attempt == 3;

    if (success) {
        System.out.println("Operation successful");
        break;
    }
}
```

In real automation frameworks, retries should be controlled and used only for appropriate transient failures. They should not hide genuine application defects.

### Example 4: Skip invalid test data

```java
String[] users = {"admin", "", "tester", null};

for (String user : users) {

    if (user == null || user.isBlank()) {
        continue;
    }

    System.out.println("Testing user: " + user);
}
```

### Example 5: Stop processing after a critical failure

```java
boolean[] testResults = {true, true, false, true};

for (int i = 0; i < testResults.length; i++) {

    if (!testResults[i]) {
        System.out.println("Critical failure at test: " + (i + 1));
        break;
    }

    System.out.println("Test passed: " + (i + 1));
}
```

---

## 7. Coding Practice

### Beginner Level

1. Check whether a number is positive, negative or zero.
2. Check whether a number is even or odd.
3. Find the largest of three numbers using if-else.
4. Find the grade based on marks using an else-if ladder.
5. Check whether a year is a leap year.
6. Create a calculator using switch.
7. Print numbers from 1 to 100 using a for loop.
8. Print numbers from 100 to 1 using a while loop.
9. Print the multiplication table of a given number.
10. Calculate the sum of the first N natural numbers.

### Intermediate Level

11. Reverse a number using a while loop.
12. Count the digits in a number.
13. Check whether a number is a palindrome.
14. Check whether a number is prime.
15. Print all prime numbers between 1 and 100.
16. Find the factorial of a number.
17. Print the Fibonacci series.
18. Find the sum of digits of a number.
19. Print a right-angled triangle star pattern.
20. Print a pyramid star pattern.

### Advanced / Interview Level

21. Find Armstrong numbers within a given range.
22. Find the GCD of two numbers using a loop.
23. Find the LCM of two numbers.
24. Print a diamond star pattern.
25. Demonstrate labeled break and labeled continue.
26. Predict the output of nested loops.
27. Write a program to identify duplicate values using nested loops.
28. Create a menu-driven calculator using switch and loops.
29. Simulate login attempts with a maximum of three retries.
30. Process test data and skip invalid records using continue.

---

## 8. Interview Questions

1. What are control statements in Java?
2. What are the three categories of control statements?
3. What is the difference between if-else and switch?
4. What is an else-if ladder?
5. What is a nested if statement?
6. What happens if break is not used in a switch?
7. Can we use String in switch?
8. What is an enhanced switch expression?
9. What is the difference between for and while?
10. What is the difference between while and do-while?
11. Which loop executes at least once?
12. What is an infinite loop?
13. What is a nested loop?
14. What is an enhanced for loop?
15. What is the difference between break and continue?
16. What is the difference between break and return?
17. What is a labeled break?
18. What is a labeled continue?
19. Can we use break inside an if statement?
20. Can we use continue inside a switch?
21. Can a for loop omit initialization or update?
22. Can we write an infinite for loop?
23. How do you avoid infinite loops?
24. How would you implement retry logic in an automation framework?
25. How do you skip invalid test data without stopping the complete test execution?

---

## 9. Day 03 Completion Checklist

- [ ] Understand control statements.
- [ ] Practise if and if-else.
- [ ] Understand else-if ladder.
- [ ] Practise nested if.
- [ ] Understand switch and fall-through.
- [ ] Learn switch expressions.
- [ ] Practise for loop.
- [ ] Practise while loop.
- [ ] Practise do-while loop.
- [ ] Understand nested loops.
- [ ] Practise enhanced for loop.
- [ ] Understand break, continue and return.
- [ ] Practise labeled break and continue.
- [ ] Complete at least 15 coding exercises.
- [ ] Practise interview questions.
- [ ] Understand real-time QA automation applications.
- [ ] Push notes and programs to GitHub.

**Expected outcome:** Be able to implement conditional logic, iteration, retry mechanisms, data filtering and execution control in Java programs and automation frameworks.