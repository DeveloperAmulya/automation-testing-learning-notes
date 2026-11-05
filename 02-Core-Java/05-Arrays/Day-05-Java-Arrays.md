# Day 05 – Java Arrays

**Learning Track:** Core Java  
**Topic:** Arrays  
**Folder:** 05-Arrays  
**Objective:** Understand array declaration, initialization, traversal, manipulation, multidimensional arrays, sorting, searching and practical applications in automation testing.

---

## 1. Introduction to Arrays

### 1. What is an array in Java?

An array is a data structure that stores multiple values of the same data type in a single variable.

Each element is accessed using an index, starting from zero.

Example:

```java
public class ArrayExample {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};

        System.out.println(numbers[0]);
        System.out.println(numbers[2]);
    }
}
```

Output:

```text
10
30
```

Important characteristics:

- Arrays have a fixed length after creation.
- Arrays store elements of a specified component type.
- Array indexing starts from zero.
- Arrays are objects in Java.
- Arrays can store primitive values or object references.
- Arrays are accessed using indexes.

### 2. Why do we use arrays?

Without arrays, we might declare multiple variables individually:

```java
int mark1 = 80;
int mark2 = 90;
int mark3 = 75;
int mark4 = 85;
```

Using arrays:

```java
int[] marks = {80, 90, 75, 85};
```

Advantages:

- Stores multiple values under one reference.
- Makes data processing easier.
- Supports iteration using loops.
- Useful for sorting and searching.
- Reduces repetitive variable declarations.

---

## 2. Array Declaration and Initialization

### 3. How do we declare an array?

Syntax:

```java
dataType[] arrayName;
```

Examples:

```java
int[] numbers;
String[] names;
double[] prices;
```

Java also supports this declaration style:

```java
int numbers[];
```

However, `int[] numbers` is generally preferred because it clearly indicates that the type is an array of integers.

### 4. How do we create an array?

Use the `new` keyword:

```java
int[] numbers = new int[5];
```

This creates an integer array with five elements.

### 5. How do we initialize an array?

**Method 1: Initialize during declaration**

```java
int[] numbers = {10, 20, 30, 40};
```

**Method 2: Create first, assign later**

```java
int[] numbers = new int[4];

numbers[0] = 10;
numbers[1] = 20;
numbers[2] = 30;
numbers[3] = 40;
```

### 6. What are the default values of array elements?

When an array is created using `new`, its elements receive default values.

| Data type | Default value |
|---|---|
| byte | 0 |
| short | 0 |
| int | 0 |
| long | 0L |
| float | 0.0f |
| double | 0.0d |
| char | `'\u0000'` |
| boolean | false |
| Reference types | null |

Example:

```java
public class ArrayDefaultValues {
    public static void main(String[] args) {
        int[] numbers = new int[3];
        boolean[] flags = new boolean[3];
        String[] names = new String[3];

        System.out.println(numbers[0]);
        System.out.println(flags[0]);
        System.out.println(names[0]);
    }
}
```

### 7. What happens if we access an invalid array index?

Java throws `ArrayIndexOutOfBoundsException` when an invalid index is accessed.

Example:

```java
int[] numbers = {10, 20, 30};

System.out.println(numbers[5]);
```

This produces a runtime exception.

Valid indexes range from `0` to `array.length - 1`.

---

## 3. Array Properties and Memory Concepts

### 8. What is the length property in an array?

The `length` property returns the total number of elements in an array.

Example:

```java
int[] numbers = {10, 20, 30, 40};

System.out.println(numbers.length);
```

Output:

```text
4
```

Important difference:

- Array: `array.length`
- String: `string.length()`
- Collection: `collection.size()`

### 9. Are arrays objects in Java?

Yes. Arrays are objects created at runtime.

Even arrays of primitive values are objects.

Example:

```java
int[] numbers = new int[5];

System.out.println(numbers instanceof Object);
```

Output:

```text
true
```

### 10. Can we change the size of an array after creation?

No. Array length is fixed after the array is created.

If a different size is needed, create another array and copy the elements.

Example:

```java
int[] oldArray = {10, 20, 30};

int[] newArray = new int[5];

for (int i = 0; i < oldArray.length; i++) {
    newArray[i] = oldArray[i];
}
```

For dynamically growing collections, use `ArrayList`.

### 11. What happens when we assign one array reference to another?

Both references point to the same array object.

Example:

```java
int[] first = {10, 20, 30};

int[] second = first;

second[0] = 100;

System.out.println(first[0]);
```

Output:

```text
100
```

This happens because both variables refer to the same array.

### 12. How do we copy an array?

**Using a loop:**

```java
int[] original = {10, 20, 30};
int[] copy = new int[original.length];

for (int i = 0; i < original.length; i++) {
    copy[i] = original[i];
}
```

**Using Arrays.copyOf():**

```java
import java.util.Arrays;

int[] original = {10, 20, 30};

int[] copy = Arrays.copyOf(original, original.length);
```

**Using System.arraycopy():**

```java
int[] original = {10, 20, 30};
int[] copy = new int[3];

System.arraycopy(original, 0, copy, 0, original.length);
```

### 13. Difference between shallow copy and deep copy

- A shallow copy of an object array copies references to the same contained objects.
- A deep copy creates independent copies of the contained objects as well.

For primitive arrays, copying the elements produces independent values.

For arrays of mutable objects, `Arrays.copyOf()` only performs a shallow copy.

---

## 4. Traversing Arrays

### 14. How do we traverse an array using a for loop?

```java
int[] numbers = {10, 20, 30, 40};

for (int i = 0; i < numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

This approach provides access to both the index and element.

### 15. How do we traverse an array using an enhanced for loop?

```java
int[] numbers = {10, 20, 30, 40};

for (int number : numbers) {
    System.out.println(number);
}
```

This approach is simpler when only the element is needed.

### 16. Difference between for loop and enhanced for loop

| Normal for loop | Enhanced for loop |
|---|---|
| Provides index access | Does not directly provide index |
| Supports forward and backward traversal | Normally traverses from first to last |
| Useful for modifying elements by index | Useful for simple element traversal |
| More flexible | More readable |

---

## 5. Single-Dimensional Arrays

### 17. What is a single-dimensional array?

A single-dimensional array stores elements in a linear sequence.

Example:

```java
int[] numbers = {10, 20, 30, 40, 50};
```

Representation:

| Index | Value |
|---:|---:|
| 0 | 10 |
| 1 | 20 |
| 2 | 30 |
| 3 | 40 |
| 4 | 50 |

### 18. How do we find the sum of array elements?

```java
int[] numbers = {10, 20, 30, 40};

int sum = 0;

for (int number : numbers) {
    sum += number;
}

System.out.println(sum);
```

### 19. How do we find the largest and smallest elements?

```java
int[] numbers = {40, 10, 90, 20, 5};

int max = numbers[0];
int min = numbers[0];

for (int number : numbers) {
    if (number > max) {
        max = number;
    }

    if (number < min) {
        min = number;
    }
}

System.out.println("Maximum: " + max);
System.out.println("Minimum: " + min);
```

This assumes the array is non-empty.

### 20. How do we reverse an array?

```java
int[] numbers = {10, 20, 30, 40, 50};

int left = 0;
int right = numbers.length - 1;

while (left < right) {
    int temp = numbers[left];
    numbers[left] = numbers[right];
    numbers[right] = temp;

    left++;
    right--;
}

for (int number : numbers) {
    System.out.println(number);
}
```

### 21. How do we search for an element?

```java
int[] numbers = {10, 20, 30, 40};

int target = 30;
boolean found = false;

for (int number : numbers) {
    if (number == target) {
        found = true;
        break;
    }
}

System.out.println(found);
```

---

## 6. Multidimensional Arrays

### 22. What is a two-dimensional array?

A two-dimensional array is an array of arrays, commonly used to represent rows and columns.

Example:

```java
int[][] matrix = {
    {10, 20, 30},
    {40, 50, 60},
    {70, 80, 90}
};
```

Representation:

| | Column 0 | Column 1 | Column 2 |
|---|---:|---:|---:|
| Row 0 | 10 | 20 | 30 |
| Row 1 | 40 | 50 | 60 |
| Row 2 | 70 | 80 | 90 |

### 23. How do we access elements in a two-dimensional array?

```java
int[][] matrix = {
    {10, 20},
    {30, 40}
};

System.out.println(matrix[0][0]);
System.out.println(matrix[1][1]);
```

Output:

```text
10
40
```

### 24. How do we traverse a two-dimensional array?

```java
int[][] matrix = {
    {10, 20},
    {30, 40},
    {50, 60}
};

for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }

    System.out.println();
}
```

### 25. What is a jagged array?

A jagged array is a two-dimensional array in which each row can have a different length.

Example:

```java
int[][] numbers = new int[3][];

numbers[0] = new int[2];
numbers[1] = new int[3];
numbers[2] = new int[4];
```

Each row is an independent array.

### 26. Difference between two-dimensional and jagged arrays

| Two-dimensional rectangular array | Jagged array |
|---|---|
| Rows commonly have equal lengths | Rows can have different lengths |
| Suitable for matrices | Suitable for irregular data |
| Each row is still a separate array | Each row is a separate array |

Important: Java multidimensional arrays are arrays containing other arrays, not a single guaranteed rectangular memory block.

---

## 7. Arrays Utility Class

### 27. What is the Arrays class?

`java.util.Arrays` provides utility methods for manipulating and processing arrays.

Common methods:

| Method | Purpose |
|---|---|
| Arrays.toString() | Converts array contents into readable text |
| Arrays.sort() | Sorts array elements |
| Arrays.equals() | Compares array contents |
| Arrays.copyOf() | Copies an array |
| Arrays.fill() | Fills an array with a value |
| Arrays.binarySearch() | Searches a sorted array |
| Arrays.deepToString() | Displays nested array contents |
| Arrays.deepEquals() | Compares nested array contents |

### 28. How do we print an array?

```java
import java.util.Arrays;

int[] numbers = {30, 10, 20};

System.out.println(Arrays.toString(numbers));
```

### 29. How do we sort an array?

```java
import java.util.Arrays;

int[] numbers = {40, 10, 30, 20};

Arrays.sort(numbers);

System.out.println(Arrays.toString(numbers));
```

Output:

```text
[10, 20, 30, 40]
```

### 30. How do we compare two arrays?

```java
import java.util.Arrays;

int[] first = {10, 20, 30};
int[] second = {10, 20, 30};

System.out.println(Arrays.equals(first, second));
```

Output:

```text
true
```

Using `==` on arrays checks reference identity, not element-by-element equality.

### 31. How do we fill an array?

```java
import java.util.Arrays;

int[] numbers = new int[5];

Arrays.fill(numbers, 10);

System.out.println(Arrays.toString(numbers));
```

Output:

```text
[10, 10, 10, 10, 10]
```

### 32. How does binarySearch() work?

Binary search searches for a value in a sorted array.

```java
import java.util.Arrays;

int[] numbers = {10, 20, 30, 40, 50};

int index = Arrays.binarySearch(numbers, 30);

System.out.println(index);
```

Output:

```text
2
```

Important: For predictable results, the array must be sorted according to the same ordering used for the search.

---

## 8. Sorting and Searching Algorithms

### 33. What is linear search?

Linear search checks each element one by one until the target is found or the array ends.

Time complexity: O(n).

### 34. What is binary search?

Binary search repeatedly divides a sorted search range into halves.

Time complexity: O(log n).

It requires sorted data or another suitable ordered search space.

### 35. What is bubble sort?

Bubble sort repeatedly compares adjacent elements and swaps them when they are in the wrong order.

Example:

```java
int[] numbers = {5, 3, 4, 1};

for (int i = 0; i < numbers.length - 1; i++) {
    for (int j = 0; j < numbers.length - 1 - i; j++) {
        if (numbers[j] > numbers[j + 1]) {
            int temp = numbers[j];
            numbers[j] = numbers[j + 1];
            numbers[j + 1] = temp;
        }
    }
}
```

Typical time complexity:
- Best case: O(n) with an optimized early-exit implementation.
- Average case: O(n²).
- Worst case: O(n²).

### 36. What is selection sort?

Selection sort repeatedly finds the smallest remaining element and places it in its correct position.

Typical time complexity:
- Best case: O(n²).
- Average case: O(n²).
- Worst case: O(n²).

### 37. What is insertion sort?

Insertion sort builds a sorted section by inserting each new element into its correct position.

Typical time complexity:
- Best case: O(n).
- Average case: O(n²).
- Worst case: O(n²).

---

## 9. Arrays vs Collections

### 38. Difference between Array and ArrayList

| Array | ArrayList |
|---|---|
| Fixed size | Dynamically resizable |
| Can store primitives and references | Stores objects; primitives use wrapper classes |
| Uses `length` | Uses `size()` |
| Can be multidimensional | Can contain nested lists |
| Supports direct indexed access | Supports indexed access |
| Built-in language structure | Part of Java Collections Framework |

Example:

```java
int[] numbers = {10, 20, 30};
```

```java
import java.util.ArrayList;

ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(30);
```

---

## 10. Real-Time QA Automation Applications

### Example 1: Store browser names

```java
String[] browsers = {"Chrome", "Firefox", "Edge"};

for (String browser : browsers) {
    System.out.println("Executing tests on: " + browser);
}
```

### Example 2: Store expected API status codes

```java
int[] expectedStatusCodes = {200, 201, 400, 401, 404};

for (int code : expectedStatusCodes) {
    System.out.println("Expected status: " + code);
}
```

### Example 3: Validate test results

```java
boolean[] testResults = {true, true, false, true};

for (int i = 0; i < testResults.length; i++) {
    if (!testResults[i]) {
        System.out.println("Test failed at index: " + i);
    }
}
```

### Example 4: Store test usernames

```java
String[] usernames = {"admin", "tester", "guest"};

for (String username : usernames) {
    System.out.println("Testing login for: " + username);
}
```

### Example 5: Validate expected and actual values

```java
String[] expected = {"Home", "Login", "Dashboard"};
String[] actual = {"Home", "Login", "Dashboard"};

for (int i = 0; i < expected.length; i++) {
    if (!expected[i].equals(actual[i])) {
        System.out.println("Mismatch at index: " + i);
    }
}
```

In real test automation, also verify that both arrays have compatible lengths before comparing corresponding elements.

---

## 11. Coding Practice

### Beginner Level

1. Declare and initialize an integer array.
2. Print all array elements using a for loop.
3. Print all array elements using an enhanced for loop.
4. Find the length of an array.
5. Calculate the sum of array elements.
6. Calculate the average of array elements.
7. Find the largest element.
8. Find the smallest element.
9. Count even and odd numbers.
10. Search for a particular element.
11. Reverse an array.
12. Copy one array into another.
13. Print elements at even indexes.
14. Find the second-largest element.
15. Find the second-smallest element.

### Intermediate Level

16. Sort an array in ascending order.
17. Sort an array in descending order.
18. Remove duplicate elements.
19. Find duplicate elements.
20. Count the frequency of each element.
21. Merge two arrays.
22. Find common elements between two arrays.
23. Find missing numbers in a sequence.
24. Move all zeros to the end.
25. Rotate an array to the left.
26. Rotate an array to the right.
27. Find pairs whose sum equals a target.
28. Find the maximum difference between two elements.

### Advanced / Interview Level

29. Implement linear search.
30. Implement binary search.
31. Implement bubble sort.
32. Implement selection sort.
33. Implement insertion sort.
34. Find the maximum subarray sum using Kadane's algorithm.
35. Find the majority element.
36. Find the intersection of two arrays.
37. Find the union of two arrays.
38. Find the longest consecutive sequence.
39. Find the product of array elements except self.
40. Solve the Two Sum problem.
41. Find the missing and repeating number.
42. Find the top K frequent elements.

### Multidimensional Array Practice

43. Create and print a 2D matrix.
44. Calculate the sum of each row.
45. Calculate the sum of each column.
46. Find the transpose of a matrix.
47. Add two matrices.
48. Multiply two matrices.
49. Find the diagonal sum of a matrix.
50. Check whether a matrix is symmetric.

---

## 12. Important Interview Questions

1. What is an array in Java?
2. Why are arrays fixed in size?
3. Are arrays objects in Java?
4. Can an array store different data types?
5. What is the default value of an array element?
6. What happens when an invalid index is accessed?
7. What is the difference between array length and String length?
8. Can we resize an array?
9. What happens when we assign one array reference to another?
10. How do we copy an array?
11. What is the difference between shallow copy and deep copy?
12. What is the difference between a normal for loop and enhanced for loop?
13. What is a multidimensional array?
14. What is a jagged array?
15. What is the difference between array and ArrayList?
16. What is the Arrays utility class?
17. What is the difference between Arrays.equals() and ==?
18. What is the difference between Arrays.sort() and manual sorting?
19. How does binary search work?
20. Why must an array be sorted before binary search?
21. What is the time complexity of linear search?
22. What is the time complexity of binary search?
23. Explain bubble sort, selection sort and insertion sort.
24. How do you find the second-largest element?
25. How do you remove duplicates from an array?
26. How do you find duplicate elements?
27. How do you find the missing number?
28. How do you rotate an array?
29. How do you merge two arrays?
30. How are arrays used in Selenium and API automation?

---

## 13. Day 05 Completion Checklist

- [ ] Understand array fundamentals.
- [ ] Learn array declaration and initialization.
- [ ] Understand default values.
- [ ] Practise array indexing.
- [ ] Understand fixed array length.
- [ ] Understand array references and copying.
- [ ] Practise normal and enhanced for loops.
- [ ] Understand single-dimensional arrays.
- [ ] Understand multidimensional arrays.
- [ ] Practise jagged arrays.
- [ ] Learn the Arrays utility class.
- [ ] Practise sorting and searching.
- [ ] Understand array vs ArrayList.
- [ ] Complete at least 20 coding exercises.
- [ ] Practise interview questions.
- [ ] Understand QA automation applications.
- [ ] Push notes and programs to GitHub.

**Expected outcome:** Be able to create, traverse, manipulate, search and sort arrays confidently, and apply array concepts in Java coding interviews and Selenium/API automation frameworks.