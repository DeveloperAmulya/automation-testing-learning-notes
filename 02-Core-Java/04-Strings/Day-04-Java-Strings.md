# Day 04 – Java Strings

**Learning Track:** Core Java  
**Topic:** Strings  
**Folder:** 04-Strings  
**Objective:** Understand String creation, immutability, String pool, String methods, String comparison, StringBuilder, StringBuffer and practical String manipulation.

---

## 1. Introduction to Strings

### 1. What is a String in Java?

A String is a sequence of characters used to represent text.

In Java, String is a predefined class available in the `java.lang` package.

Example:

```java
public class StringExample {
    public static void main(String[] args) {
        String name = "Amulya";
        System.out.println(name);
    }
}
```

Output:

```text
Amulya
```

Important points:
- String is a class, not a primitive data type.
- String objects are immutable.
- String belongs to the `java.lang` package.
- Strings can be created using literals or the `new` keyword.

### 2. How many ways can we create a String?

There are two common ways.

**1. Using String literal**

```java
String name = "Java";
```

**2. Using the new keyword**

```java
String name = new String("Java");
```

Difference:

| String literal | Using new |
|---|---|
| Uses the String pool when an equal literal already exists | Creates a new String object |
| Can reuse an existing pooled String | Explicitly creates a distinct String object |
| More memory-efficient for repeated literals | Can create additional objects |

---

## 2. String Constant Pool

### 3. What is the String Constant Pool?

The String Constant Pool is a special area associated with the JVM's heap where String literals are pooled.

When we create a String literal, Java checks whether an equal literal already exists in the pool.

If it exists, the existing pooled String reference can be reused. Otherwise, a pooled String is created.

Example:

```java
public class StringPoolExample {
    public static void main(String[] args) {
        String s1 = "Java";
        String s2 = "Java";

        System.out.println(s1 == s2);
    }
}
```

Output:

```text
true
```

Both variables refer to the same pooled String.

### 4. Difference between String literal and new String()

```java
public class StringPoolExample2 {
    public static void main(String[] args) {
        String s1 = "Java";
        String s2 = new String("Java");

        System.out.println(s1 == s2);
        System.out.println(s1.equals(s2));
    }
}
```

Output:

```text
false
true
```

Explanation:

- `s1` refers to the pooled String.
- `s2` refers to a separately created String object.
- `==` compares references.
- `equals()` compares String content.

### 5. What is intern() in Java?

The `intern()` method returns the canonical pooled representation of a String.

Example:

```java
public class InternExample {
    public static void main(String[] args) {
        String s1 = new String("Java");
        String s2 = s1.intern();
        String s3 = "Java";

        System.out.println(s2 == s3);
    }
}
```

Output:

```text
true
```

---

## 3. String Immutability

### 6. What is String immutability?

String immutability means that once a String object is created, its contents cannot be changed.

If we perform an operation that appears to modify a String, Java creates another String object or returns an existing String.

Example:

```java
public class ImmutableExample {
    public static void main(String[] args) {
        String name = "Java";

        name.concat(" Programming");

        System.out.println(name);
    }
}
```

Output:

```text
Java
```

The original String remains unchanged because the result of `concat()` was not assigned.

Correct approach:

```java
String name = "Java";
name = name.concat(" Programming");

System.out.println(name);
```

Output:

```text
Java Programming
```

### 7. Why is String immutable in Java?

Important reasons include:

1. String pool reuse is safe because pooled String values cannot be modified.
2. Strings are commonly used in security-sensitive operations.
3. Immutable objects are naturally thread-safe.
4. Strings can cache their hash codes.
5. Immutability makes String behavior predictable.

### 8. What happens internally when we modify a String?

Example:

```java
String s1 = "Hello";
String s2 = s1.concat(" World");
```

- `s1` continues to refer to `"Hello"`.
- `concat()` produces a String containing `"Hello World"`.
- `s2` refers to the resulting String.

---

## 4. String Comparison

### 9. Difference between == and equals()

| == | equals() |
|---|---|
| Compares references for objects | Compares logical content according to implementation |
| Checks whether references point to the same object | String compares character content |
| Operator | Method |

Example:

```java
public class StringComparison {
    public static void main(String[] args) {
        String s1 = new String("Java");
        String s2 = new String("Java");

        System.out.println(s1 == s2);
        System.out.println(s1.equals(s2));
    }
}
```

Output:

```text
false
true
```

### 10. What is equalsIgnoreCase()?

It compares two Strings without considering differences in letter case.

```java
String s1 = "Java";
String s2 = "JAVA";

System.out.println(s1.equalsIgnoreCase(s2));
```

Output:

```text
true
```

### 11. What is compareTo()?

The `compareTo()` method performs lexicographical comparison of two Strings.

It returns:
- Zero if the Strings are equal.
- A negative integer if the first String is lexicographically smaller.
- A positive integer if the first String is lexicographically greater.

Example:

```java
String s1 = "Apple";
String s2 = "Banana";

System.out.println(s1.compareTo(s2));
```

### 12. Difference between equals() and compareTo()

| equals() | compareTo() |
|---|---|
| Checks equality | Performs lexicographical comparison |
| Returns boolean | Returns integer |
| Useful for matching text | Useful for sorting and ordering text |

---

## 5. Important String Methods

### 13. length()

Returns the number of UTF-16 code units in a String.

```java
String name = "Automation";
System.out.println(name.length());
```

Output:

```text
10
```

### 14. charAt()

Returns the character at the specified index.

```java
String name = "Java";
System.out.println(name.charAt(0));
```

Output:

```text
J
```

Important: String indexes start from zero.

### 15. substring()

Extracts part of a String.

```java
String text = "AutomationTesting";

System.out.println(text.substring(0, 10));
System.out.println(text.substring(10));
```

Output:

```text
Automation
Testing
```

Important:
- Start index is inclusive.
- End index is exclusive.

### 16. contains()

Checks whether a String contains a specified character sequence.

```java
String message = "Welcome to Java";

System.out.println(message.contains("Java"));
```

Output:

```text
true
```

### 17. startsWith() and endsWith()

```java
String url = "https://example.com";

System.out.println(url.startsWith("https"));
System.out.println(url.endsWith(".com"));
```

Both return boolean values.

### 18. toUpperCase() and toLowerCase()

```java
String name = "Java";

System.out.println(name.toUpperCase());
System.out.println(name.toLowerCase());
```

### 19. trim() and strip()

Both methods remove leading and trailing whitespace, but they differ in their whitespace definitions.

```java
String text = "  Java Programming  ";

System.out.println(text.trim());
System.out.println(text.strip());
```

- `trim()` removes characters with code points up to U+0020 at the beginning and end.
- `strip()` uses Unicode-aware whitespace handling.

`strip()` was introduced in Java 11.

### 20. replace()

Replaces matching characters or character sequences.

```java
String text = "Java is easy";

System.out.println(text.replace("easy", "powerful"));
```

### 21. replaceAll() and replaceFirst()

These methods use regular expressions.

```java
String text = "Java123Automation456";

System.out.println(text.replaceAll("[0-9]", ""));
System.out.println(text.replaceFirst("[0-9]", ""));
```

Output:

```text
JavaAutomation
Java23Automation456
```

### 22. split()

Splits a String into an array using a regular expression delimiter.

```java
String data = "Java,Selenium,TestNG";

String[] tools = data.split(",");

for (String tool : tools) {
    System.out.println(tool);
}
```

### 23. isEmpty() and isBlank()

```java
String s1 = "";
String s2 = "   ";

System.out.println(s1.isEmpty());
System.out.println(s2.isEmpty());

System.out.println(s1.isBlank());
System.out.println(s2.isBlank());
```

Output:

```text
true
false
true
true
```

- `isEmpty()` checks whether length is zero.
- `isBlank()` checks whether the String is empty or contains only whitespace characters as defined by Java's whitespace handling.

`isBlank()` was introduced in Java 11.

### 24. indexOf() and lastIndexOf()

```java
String text = "Automation Testing";

System.out.println(text.indexOf('t'));
System.out.println(text.lastIndexOf('t'));
```

These methods return the index of a matching character or substring, or `-1` if no match exists.

### 25. concat()

Joins two Strings.

```java
String first = "Java";
String second = " Programming";

String result = first.concat(second);

System.out.println(result);
```

### 26. String.join()

Joins multiple character sequences using a delimiter.

```java
String result = String.join("-", "Java", "Selenium", "TestNG");

System.out.println(result);
```

Output:

```text
Java-Selenium-TestNG
```

### 27. valueOf()

Converts different types of values into their String representation.

```java
int number = 100;

String result = String.valueOf(number);

System.out.println(result);
```

### 28. toCharArray()

Converts a String into a character array.

```java
String name = "Java";

char[] characters = name.toCharArray();

for (char ch : characters) {
    System.out.println(ch);
}
```

---

## 6. StringBuilder and StringBuffer

### 29. What is StringBuilder?

StringBuilder is a mutable sequence of characters.

Unlike String, its contents can be modified without creating a new String object for every modification.

Example:

```java
public class StringBuilderExample {
    public static void main(String[] args) {
        StringBuilder builder = new StringBuilder("Java");

        builder.append(" Programming");

        System.out.println(builder);
    }
}
```

Output:

```text
Java Programming
```

### 30. What is StringBuffer?

StringBuffer is also a mutable sequence of characters.

Its methods are synchronized, making its individual operations suitable for synchronized access from multiple threads.

Example:

```java
StringBuffer buffer = new StringBuffer("Java");

buffer.append(" Automation");

System.out.println(buffer);
```

### 31. Difference between String, StringBuilder and StringBuffer

| Feature | String | StringBuilder | StringBuffer |
|---|---|---|---|
| Mutability | Immutable | Mutable | Mutable |
| Thread safety | Immutable object is naturally thread-safe | Not synchronized | Synchronized methods |
| Performance for repeated modifications | Can be inefficient | Usually faster in single-threaded use | Synchronization can add overhead |
| Introduced | Java 1.0 | Java 1.5 | Java 1.0 |

### 32. Important StringBuilder methods

```java
StringBuilder sb = new StringBuilder("Java");

sb.append(" Testing");
sb.insert(4, " Automation");
sb.replace(0, 4, "Python");
sb.delete(0, 6);
sb.reverse();

System.out.println(sb);
```

Important methods:
- append()
- insert()
- replace()
- delete()
- deleteCharAt()
- reverse()
- capacity()
- length()
- setCharAt()
- toString()

### 33. Difference between length() and capacity()

- `length()` returns the number of characters currently stored.
- `capacity()` returns the current storage capacity of StringBuilder or StringBuffer.

Example:

```java
StringBuilder sb = new StringBuilder("Java");

System.out.println(sb.length());
System.out.println(sb.capacity());
```

For a newly created StringBuilder using this constructor, the initial capacity is 16 plus the initial String length.

---

## 7. Advanced String Concepts

### 34. What is String concatenation?

String concatenation combines multiple Strings.

Example:

```java
String firstName = "Amulya";
String lastName = "Battu";

String fullName = firstName + " " + lastName;

System.out.println(fullName);
```

The `+` operator is commonly used for concatenation.

### 35. What happens when we concatenate String and other data types?

Java converts the non-String operand to its String representation during concatenation.

```java
int age = 25;

String result = "Age: " + age;

System.out.println(result);
```

Output:

```text
Age: 25
```

### 36. What is String formatting?

String formatting creates formatted text using placeholders.

```java
String name = "Amulya";
int age = 25;

String result = String.format("Name: %s, Age: %d", name, age);

System.out.println(result);
```

Common format specifiers:
- `%s` – String
- `%d` – Integer
- `%f` – Floating-point
- `%c` – Character
- `%b` – Boolean

### 37. What is a regular expression?

A regular expression is a pattern used to match, validate, extract or replace text.

Example:

```java
String email = "test@example.com";

boolean valid = email.matches("^[A-Za-z0-9+_.-]+@[A-Za-z0-9.-]+$");

System.out.println(valid);
```

This is a basic pattern example, not a complete production-grade email validation standard.

### 38. What is String deduplication?

String deduplication is a JVM optimization that can allow multiple equal String objects to share the same underlying character storage.

It does not make Strings mutable or change their logical equality.

### 39. What is the difference between String and char[]?

| String | char[] |
|---|---|
| Immutable | Mutable |
| Represents text | Stores character elements |
| Provides many built-in methods | Uses array operations |
| Cannot directly overwrite its contents | Individual elements can be overwritten |

A mutable character array can be useful when handling sensitive character data, although secure erasure requires care and cannot guarantee removal of all copies.

---

## 8. Real-Time QA Automation Applications

### Example 1: Validate page title in Selenium

```java
String actualTitle = driver.getTitle();
String expectedTitle = "Login Page";

if (actualTitle.equals(expectedTitle)) {
    System.out.println("Title validation passed");
} else {
    System.out.println("Title validation failed");
}
```

### Example 2: Validate URL

```java
String actualUrl = driver.getCurrentUrl();

if (actualUrl.startsWith("https://")) {
    System.out.println("Secure URL");
}
```

### Example 3: Validate error message

```java
String actualMessage = driver.findElement(errorMessage).getText();

if (actualMessage.contains("Invalid credentials")) {
    System.out.println("Error message validated");
}
```

### Example 4: Remove spaces from test data

```java
String username = "  testuser  ";

String formattedUsername = username.strip();

System.out.println(formattedUsername);
```

### Example 5: Compare API response values

```java
String actualStatus = "SUCCESS";
String expectedStatus = "SUCCESS";

boolean result = actualStatus.equals(expectedStatus);

System.out.println(result);
```

### Example 6: Extract values from API response

```java
String response = "status=SUCCESS;message=Booking created";

String[] values = response.split(";");

for (String value : values) {
    System.out.println(value);
}
```

### Example 7: Build dynamic test data

```java
StringBuilder testData = new StringBuilder();

testData.append("Username: tester");
testData.append(", Password: test123");
testData.append(", Role: Admin");

System.out.println(testData);
```

---

## 9. Coding Practice

### Beginner Level

1. Reverse a String.
2. Find the length of a String without using length().
3. Convert a String to uppercase and lowercase.
4. Count vowels and consonants.
5. Count the number of words in a sentence.
6. Check whether a String is empty or blank.
7. Compare two Strings using equals() and ==.
8. Count the occurrence of a character.
9. Remove all whitespace from a String.
10. Extract a substring from a given String.

### Intermediate Level

11. Check whether a String is a palindrome.
12. Check whether two Strings are anagrams.
13. Remove duplicate characters from a String.
14. Find the first non-repeated character.
15. Find the first repeated character.
16. Count uppercase, lowercase, digits and special characters.
17. Reverse each word in a sentence.
18. Reverse the order of words in a sentence.
19. Find duplicate words in a sentence.
20. Find the longest word in a sentence.
21. Count character frequency using a map.
22. Replace all spaces with hyphens.
23. Check whether one String is a rotation of another.
24. Find the maximum occurring character.

### Advanced / Interview Level

25. Implement String reversal without using reverse().
26. Check whether two Strings are rotations.
27. Find the longest substring without repeating characters.
28. Find the longest common prefix in an array of Strings.
29. Compress a String using character counts.
30. Find all permutations of a String.
31. Find the longest palindromic substring.
32. Demonstrate String pool behavior using intern().
33. Predict the output of complex String comparison examples.
34. Compare String concatenation performance with StringBuilder.
35. Implement basic email and phone-number format validation using regular expressions.

---

## 10. Important Interview Questions

1. What is String in Java?
2. Why is String immutable?
3. What is the String Constant Pool?
4. What is the difference between String literal and new String()?
5. What is the intern() method?
6. What happens internally when we concatenate Strings?
7. What is the difference between == and equals()?
8. What is the difference between equals() and compareTo()?
9. What is the difference between String, StringBuilder and StringBuffer?
10. Why is StringBuilder faster for repeated modifications in single-threaded code?
11. Is StringBuilder thread-safe?
12. Is StringBuffer thread-safe?
13. What is the difference between length() and capacity()?
14. What is the difference between substring() and subSequence()?
15. What is the difference between trim() and strip()?
16. What is the difference between isEmpty() and isBlank()?
17. What is the difference between replace() and replaceAll()?
18. What is the difference between split() and StringTokenizer?
19. Can we override the String class?
20. Why is String declared final?
21. What is the difference between String and char[]?
22. How do you reverse a String without using reverse()?
23. How do you find duplicate characters in a String?
24. How do you validate a String using regular expressions?
25. How are Strings used in Selenium automation?
26. How do you validate API response text using Java Strings?
27. What is String deduplication?
28. What is the difference between Unicode code points and String length?

---

## 11. Day 04 Completion Checklist

- [ ] Understand String class.
- [ ] Understand String creation.
- [ ] Understand String Constant Pool.
- [ ] Understand String immutability.
- [ ] Practise == and equals().
- [ ] Understand intern().
- [ ] Practise important String methods.
- [ ] Understand StringBuilder.
- [ ] Understand StringBuffer.
- [ ] Compare String, StringBuilder and StringBuffer.
- [ ] Understand regular expressions.
- [ ] Practise String manipulation programs.
- [ ] Complete at least 15 coding exercises.
- [ ] Practise interview questions.
- [ ] Understand Selenium and API testing applications.
- [ ] Push notes and programs to GitHub.

**Expected outcome:** Be able to manipulate, compare, validate and process Strings confidently in Java coding interviews, Selenium automation frameworks and REST Assured API testing.