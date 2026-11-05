# Day 06 – Java Object-Oriented Programming (OOP)

**Learning Track:** Core Java  
**Topic:** Object-Oriented Programming  
**Folder:** 06-OOP  
**Objective:** Understand classes, objects, constructors, inheritance, polymorphism, abstraction, encapsulation, interfaces and their practical applications in automation frameworks.

---

# 1. Introduction to OOP

## 1. What is Object-Oriented Programming?

Object-Oriented Programming (OOP) is a programming approach based on classes and objects.

It organizes code into reusable components that combine data and behavior.

Java uses OOP concepts to build maintainable, modular, reusable and scalable applications.

Main advantages:

- Code reusability.
- Modularity.
- Maintainability.
- Data security through encapsulation.
- Flexibility through polymorphism.
- Extensibility through inheritance and abstraction.

## 2. What are the four pillars of OOP?

The four main pillars are:

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

| Pillar | Purpose |
|---|---|
| Encapsulation | Bundles data and methods and controls access |
| Inheritance | Allows a class to reuse and extend another class |
| Polymorphism | Allows one interface or method name to represent different behaviors |
| Abstraction | Hides implementation details and exposes essential functionality |

---

# 2. Classes and Objects

## 3. What is a class in Java?

A class is a blueprint or template used to create objects.

It defines the fields and methods that its objects can have.

Example:

```java
public class Employee {

    int employeeId;
    String employeeName;

    void displayDetails() {
        System.out.println(employeeId);
        System.out.println(employeeName);
    }
}
```

Here, Employee is a class containing two instance variables and one method.

## 4. What is an object in Java?

An object is an instance of a class.

An object has:

- State: represented by fields or variables.
- Behavior: represented by methods.
- Identity: distinguishes one object from another.

Example:

```java
public class EmployeeTest {

    public static void main(String[] args) {

        Employee employee = new Employee();

        employee.employeeId = 101;
        employee.employeeName = "Amulya";

        employee.displayDetails();
    }
}
```

## 5. Difference between class and object

| Class | Object |
|---|---|
| Blueprint or template | Instance of a class |
| Defines fields and methods | Has actual state and behavior |
| Declared using class keyword | Commonly created using new |
| Does not represent an individual instance | Represents an individual instance |

## 6. How do we create an object?

Syntax:

```java
ClassName referenceName = new ClassName();
```

Example:

```java
Employee employee = new Employee();
```

Explanation:

- `Employee` is the class.
- `employee` is the reference variable.
- `new` creates an object.
- `Employee()` invokes a constructor.

The reference variable holds a reference to the object, not the object itself.

## 7. Can we create multiple objects from one class?

Yes. Each object has its own instance state.

Example:

```java
Employee employee1 = new Employee();
Employee employee2 = new Employee();

employee1.employeeId = 101;
employee2.employeeId = 102;
```

Both objects share the class definition but have separate instance variables.

---

# 3. Constructors

## 8. What is a constructor in Java?

A constructor is a special class member used during object creation to initialize an object.

Characteristics:

- Constructor name must match the class name.
- It has no return type, not even void.
- It executes when an object is created.
- Constructors can be overloaded.
- Constructors are not inherited.

Example:

```java
public class Employee {

    int employeeId;
    String employeeName;

    Employee() {
        employeeId = 101;
        employeeName = "Amulya";
    }

    void display() {
        System.out.println(employeeId);
        System.out.println(employeeName);
    }

    public static void main(String[] args) {
        Employee employee = new Employee();
        employee.display();
    }
}
```

## 9. What are the types of constructors?

Commonly discussed constructor types:

1. Default constructor.
2. No-argument constructor.
3. Parameterized constructor.
4. Copy-constructor-style constructor.

### Default constructor

If a class declares no constructor, the compiler provides a default no-argument constructor.

Example:

```java
class Student {
    int studentId;
}
```

The compiler provides a default constructor.

Important: If you declare any constructor yourself, the compiler does not provide the default constructor.

### No-argument constructor

A constructor explicitly written without parameters.

```java
class Student {

    Student() {
        System.out.println("Student object created");
    }
}
```

### Parameterized constructor

A constructor that accepts parameters.

```java
class Student {

    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
}
```

### Copy-constructor-style constructor

Java does not provide a built-in copy constructor, but we can create a constructor that initializes an object using another object's state.

```java
class Student {

    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    Student(Student other) {
        this.id = other.id;
        this.name = other.name;
    }
}
```

## 10. What is constructor overloading?

Defining multiple constructors in the same class with different parameter lists is called constructor overloading.

Example:

```java
class Student {

    int id;
    String name;

    Student() {
        id = 0;
        name = "Unknown";
    }

    Student(int id) {
        this.id = id;
    }

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
}
```

## 11. Difference between constructor and method

| Constructor | Method |
|---|---|
| Initializes an object | Performs an operation |
| Same name as class | Can have any valid method name |
| No return type | Has a return type or void |
| Invoked during object creation or constructor chaining | Invoked through a method call |
| Not inherited | Instance methods can be inherited |

## 12. What is this keyword?

`this` refers to the current object.

Uses:

- Access current object's instance variables.
- Resolve naming conflicts between fields and parameters.
- Call another constructor in the same class using `this()`.
- Pass or return the current object.

Example:

```java
class Student {

    int id;

    Student(int id) {
        this.id = id;
    }
}
```

## 13. What is constructor chaining?

Constructor chaining means calling one constructor from another constructor.

Using `this()` calls another constructor in the same class.

Using `super()` calls a constructor in the parent class.

Example:

```java
class Student {

    Student() {
        this(101);
        System.out.println("No-argument constructor");
    }

    Student(int id) {
        System.out.println("Student ID: " + id);
    }
}
```

In Java, an explicit `this()` or `super()` constructor invocation must be the first statement in a constructor. Modern Java versions have specific rules for restricted constructor prologues, but traditional constructor chaining follows this rule.

---

# 4. Encapsulation

## 14. What is encapsulation?

Encapsulation is the process of bundling data and related methods inside a class while controlling access to the object's internal state.

It is commonly implemented using:

- Private instance variables.
- Public getter methods.
- Public setter methods.
- Validation inside setter methods.

Example:

```java
public class Employee {

    private int employeeId;
    private String employeeName;

    public int getEmployeeId() {
        return employeeId;
    }

    public void setEmployeeId(int employeeId) {
        if (employeeId > 0) {
            this.employeeId = employeeId;
        }
    }

    public String getEmployeeName() {
        return employeeName;
    }

    public void setEmployeeName(String employeeName) {
        this.employeeName = employeeName;
    }
}
```

## 15. Advantages of encapsulation

- Protects internal state from uncontrolled access.
- Allows validation before modifying data.
- Improves maintainability.
- Reduces coupling.
- Provides controlled access to class members.

## 16. Difference between abstraction and encapsulation

| Encapsulation | Abstraction |
|---|---|
| Bundles data and methods and controls access | Hides implementation details |
| Focuses on controlling access to state | Focuses on exposing essential behavior |
| Commonly uses private fields and methods | Commonly uses interfaces and abstract classes |
| Example: private employee salary with controlled access | Example: WebDriver interface |

---

# 5. Inheritance

## 17. What is inheritance?

Inheritance allows one class to acquire accessible members and behavior from another class.

The class being inherited from is called the parent or superclass.

The class that inherits is called the child or subclass.

Java uses the `extends` keyword for class inheritance.

Example:

```java
class Animal {

    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Dog barks");
    }
}
```

## 18. What are the types of inheritance?

Common inheritance structures:

1. Single inheritance.
2. Multilevel inheritance.
3. Hierarchical inheritance.
4. Multiple inheritance.
5. Hybrid inheritance.

### Single inheritance

One child class inherits from one parent class.

```java
class A {
    void displayA() {
        System.out.println("Class A");
    }
}

class B extends A {
    void displayB() {
        System.out.println("Class B");
    }
}
```

### Multilevel inheritance

A class inherits from a class that itself inherits from another class.

```java
class A {
    void methodA() {
        System.out.println("A");
    }
}

class B extends A {
    void methodB() {
        System.out.println("B");
    }
}

class C extends B {
    void methodC() {
        System.out.println("C");
    }
}
```

### Hierarchical inheritance

Multiple child classes inherit from the same parent class.

```java
class Animal {
    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking");
    }
}

class Cat extends Animal {
    void meow() {
        System.out.println("Meowing");
    }
}
```

### Multiple inheritance

A Java class cannot extend multiple classes.

However, Java supports multiple inheritance of type through interfaces.

```java
interface Camera {
    void takePhoto();
}

interface MusicPlayer {
    void playMusic();
}

class Smartphone implements Camera, MusicPlayer {

    public void takePhoto() {
        System.out.println("Photo captured");
    }

    public void playMusic() {
        System.out.println("Music playing");
    }
}
```

### Hybrid inheritance

Hybrid inheritance combines multiple inheritance structures.

Java can model such structures using classes and interfaces, subject to its class inheritance rules.

## 19. What is the super keyword?

`super` refers to the immediate parent class portion of the current object.

Uses:

- Access parent class variables.
- Call parent class methods.
- Invoke parent class constructors using `super()`.

Example:

```java
class Animal {

    String name = "Animal";

    void display() {
        System.out.println("Parent method");
    }
}

class Dog extends Animal {

    String name = "Dog";

    void show() {
        System.out.println(super.name);
        super.display();
    }
}
```

## 20. Can constructors be inherited?

No. Constructors are not inherited.

However, a child constructor can invoke a parent constructor using `super()`.

## 21. What is the difference between this and super?

| this | super |
|---|---|
| Refers to the current object | Refers to the parent class portion of the current object |
| Accesses current class members | Accesses parent class members |
| Calls current class constructor using this() | Calls parent constructor using super() |
| Used to resolve current instance variable conflicts | Used to access hidden parent fields or overridden parent methods |

## 22. What is the IS-A relationship?

Inheritance represents an IS-A relationship.

Example:

A Dog IS-A Animal.

```java
class Animal {
}

class Dog extends Animal {
}
```

## 23. What is the HAS-A relationship?

A HAS-A relationship represents composition or aggregation, where one class contains or refers to another object.

Example:

```java
class Engine {
    void start() {
        System.out.println("Engine started");
    }
}

class Car {

    private Engine engine = new Engine();

    void startCar() {
        engine.start();
    }
}
```

A Car HAS-A Engine.

---

# 6. Polymorphism

## 24. What is polymorphism?

Polymorphism means one interface or method name can represent different behaviors depending on the context.

Java supports two major forms:

1. Compile-time polymorphism.
2. Runtime polymorphism.

## 25. What is compile-time polymorphism?

Compile-time polymorphism is commonly achieved through method overloading.

The compiler determines which overloaded method to invoke based on the method arguments and applicable overload resolution rules.

Example:

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

## 26. What is method overloading?

Defining multiple methods with the same name but different parameter lists in the same class is called method overloading.

Ways to overload:

- Different number of parameters.
- Different parameter types.
- Different parameter order.

Important: Changing only the return type does not create a valid overload.

## 27. What is runtime polymorphism?

Runtime polymorphism is achieved through method overriding and dynamic method dispatch.

The JVM determines which overridden instance method implementation to invoke based on the actual object's class.

Example:

```java
class Animal {

    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Test {

    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.sound();
    }
}
```

Output:

```text
Dog barks
```

## 28. What is method overriding?

When a subclass provides its own implementation of an inherited instance method using a compatible method signature and return type, it is called method overriding.

Rules:

- Method name and parameter types must match.
- Return type must be compatible.
- Access cannot be made more restrictive.
- Static methods are hidden, not overridden.
- Private methods are not overridden.
- Final methods cannot be overridden.
- The `@Override` annotation helps detect mistakes.

## 29. Difference between overloading and overriding

| Overloading | Overriding |
|---|---|
| Same method name, different parameters | Same inherited instance method signature |
| Usually occurs in the same class | Occurs across superclass and subclass |
| Compile-time polymorphism | Runtime polymorphism |
| Return type alone cannot distinguish overloads | Return type must be compatible |
| Static methods can be overloaded | Static methods are hidden, not overridden |

## 30. Can we overload the main() method?

Yes. Multiple main methods can be declared with different parameter lists.

However, the JVM entry point remains the standard main method.

## 31. Can we override static methods?

No. Static methods belong to the class rather than individual objects.

When a subclass declares a static method with the same signature, it is called method hiding.

## 32. What is dynamic method dispatch?

Dynamic method dispatch is the mechanism through which an overridden instance method is selected at runtime based on the actual object.

Example:

```java
Animal animal = new Dog();
animal.sound();
```

Although the reference type is Animal, the Dog implementation executes.

---

# 7. Abstraction

## 33. What is abstraction?

Abstraction hides implementation details and exposes only essential functionality to the user.

Java supports abstraction mainly through:

1. Abstract classes.
2. Interfaces.

## 34. What is an abstract class?

An abstract class is declared using the `abstract` keyword.

It cannot be instantiated directly.

It can contain:

- Abstract methods.
- Concrete methods.
- Constructors.
- Instance variables.
- Static members.

Example:

```java
abstract class Vehicle {

    abstract void start();

    void stop() {
        System.out.println("Vehicle stopped");
    }
}

class Car extends Vehicle {

    @Override
    void start() {
        System.out.println("Car started");
    }
}
```

## 35. What is an abstract method?

An abstract method is a method declared without an implementation.

Example:

```java
abstract void start();
```

A concrete subclass must implement inherited abstract methods unless it is also abstract.

## 36. What is an interface?

An interface defines a contract that implementing classes agree to provide.

Example:

```java
interface WebDriverActions {

    void launchBrowser();

    void closeBrowser();
}

class ChromeDriverActions implements WebDriverActions {

    public void launchBrowser() {
        System.out.println("Chrome launched");
    }

    public void closeBrowser() {
        System.out.println("Chrome closed");
    }
}
```

Interfaces can also contain default methods, static methods and private methods, depending on Java version and language rules.

Interface fields are implicitly public, static and final.

## 37. Difference between abstract class and interface

| Abstract class | Interface |
|---|---|
| Declared using abstract class | Declared using interface |
| A class extends one class | A class can implement multiple interfaces |
| Can have instance variables | Fields are implicitly public, static and final |
| Can have constructors | Cannot have constructors |
| Can contain abstract and concrete methods | Can contain abstract, default, static and private methods |
| Useful for shared state and behavior | Useful for defining contracts and capabilities |

## 38. Can an abstract class have a constructor?

Yes. Its constructor executes when a concrete subclass object is created through constructor chaining.

## 39. Can we create an object of an abstract class?

No. An abstract class cannot be instantiated directly.

However, we can declare a reference of its type and assign a subclass object to it.

```java
Vehicle vehicle = new Car();
```

## 40. Can an interface extend another interface?

Yes. An interface can extend one or multiple interfaces.

```java
interface A {
    void methodA();
}

interface B {
    void methodB();
}

interface C extends A, B {
    void methodC();
}
```

---

# 8. Important Java Keywords and OOP Concepts

## 41. What is the final keyword?

The final keyword restricts modification depending on where it is used.

- Final variable: Cannot be reassigned after initialization.
- Final method: Cannot be overridden.
- Final class: Cannot be extended.

Example:

```java
final class Demo {
    final int value = 100;
}
```

## 42. What is the static keyword?

Static members belong to the class rather than individual objects.

They can be accessed using the class name.

Example:

```java
class Employee {

    static String company = "ABC Technologies";

    int employeeId;
}
```

## 43. What are access modifiers?

Access modifiers control the visibility of classes and members.

| Modifier | Same class | Same package | Subclass outside package | Other package |
|---|---|---|---|---|
| private | Yes | No | No | No |
| default/package-private | Yes | Yes | No through ordinary package access | No |
| protected | Yes | Yes | Yes, subject to protected access rules | No ordinary access |
| public | Yes | Yes | Yes | Yes |

## 44. What is the Object class?

Object is the root superclass of Java classes.

Every class ultimately inherits from Object unless it is an interface.

Important Object methods:

- toString()
- equals()
- hashCode()
- getClass()
- clone()
- wait()
- notify()
- notifyAll()

## 45. What is the difference between aggregation and composition?

Both represent HAS-A relationships.

**Aggregation:**
- A weaker ownership relationship.
- The contained object can exist independently.

**Composition:**
- A stronger ownership relationship.
- The containing object owns the lifecycle of the contained component conceptually.

---

# 9. OOP Concepts in Selenium Automation Framework

## 46. How is encapsulation used in Page Object Model?

In Page Object Model, page classes encapsulate page locators and page-specific actions.

Example:

```java
public class LoginPage {

    private WebDriver driver;

    private By username = By.id("username");
    private By password = By.id("password");
    private By loginButton = By.id("login");

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void login(String user, String pass) {
        driver.findElement(username).sendKeys(user);
        driver.findElement(password).sendKeys(pass);
        driver.findElement(loginButton).click();
    }
}
```

The test class uses the public login method without directly accessing the private locators.

## 47. How is inheritance used in automation frameworks?

A common design uses a BaseTest class containing shared setup and teardown methods.

Example:

```java
public class BaseTest {

    protected WebDriver driver;

    @BeforeMethod
    public void setUp() {
        // Initialize browser
    }

    @AfterMethod
    public void tearDown() {
        if (driver != null) {
            driver.quit();
        }
    }
}
```

A test class can extend BaseTest to reuse its setup and teardown behavior.

Inheritance should be used only when there is a genuine IS-A relationship or a suitable framework design reason. Composition is often better for reusable utilities and services.

## 48. How is polymorphism used in Selenium WebDriver?

WebDriver is an interface, and browser-specific drivers provide implementations.

Example:

```java
WebDriver driver = new ChromeDriver();
```

Or:

```java
WebDriver driver = new FirefoxDriver();
```

The same WebDriver reference type can work with different browser implementations.

## 49. How is abstraction used in Selenium?

WebDriver exposes browser interaction methods through an interface.

Automation code can use methods such as:

- get()
- findElement()
- click()
- sendKeys()
- quit()

The browser-specific implementation details are handled by the driver implementation.

## 50. Real-time OOP framework design example

A typical framework can be organized as:

```text
src/test/java/
│
├── base/
│   └── BaseTest.java
│
├── pages/
│   ├── LoginPage.java
│   └── HomePage.java
│
├── tests/
│   └── LoginTest.java
│
├── utilities/
│   ├── WaitUtils.java
│   └── ScreenshotUtils.java
│
└── factory/
    └── DriverFactory.java
```

Design principles:

- Encapsulation: Page classes hide locators and implementation details.
- Inheritance: Shared test lifecycle can be reused through BaseTest where appropriate.
- Polymorphism: WebDriver references can work with different browser drivers.
- Abstraction: Interfaces expose contracts without requiring callers to know implementation details.

---

# 10. Coding Practice

## Beginner Level

1. Create an Employee class with ID, name and salary.
2. Create two objects from the same class.
3. Create a Student class with a display method.
4. Demonstrate default and parameterized constructors.
5. Demonstrate constructor overloading.
6. Demonstrate the this keyword.
7. Demonstrate constructor chaining.
8. Create a class with private variables and getters/setters.
9. Implement basic encapsulation.
10. Demonstrate static and instance variables.

## Intermediate Level

11. Implement single inheritance.
12. Implement multilevel inheritance.
13. Implement hierarchical inheritance.
14. Demonstrate the super keyword.
15. Demonstrate method overloading.
16. Demonstrate method overriding.
17. Demonstrate runtime polymorphism.
18. Create an abstract class and implement it.
19. Create an interface and implement it.
20. Implement multiple interfaces in one class.
21. Demonstrate HAS-A relationships.
22. Demonstrate aggregation and composition.
23. Demonstrate final variables, methods and classes.
24. Demonstrate access modifiers.

## Advanced / Interview Level

25. Design a simple employee management system using OOP.
26. Design a banking application using encapsulation.
27. Implement runtime polymorphism using different payment methods.
28. Design a notification system using interfaces.
29. Design a vehicle hierarchy using inheritance.
30. Create a calculator using method overloading.
31. Demonstrate dynamic method dispatch.
32. Demonstrate method hiding using static methods.
33. Design a Selenium Page Object Model using encapsulation.
34. Design browser selection using WebDriver polymorphism.
35. Design a reusable automation framework using abstraction and interfaces.

---

# 11. Important Interview Questions

1. What is OOP?
2. What are the four pillars of OOP?
3. What is a class?
4. What is an object?
5. What is the difference between class and object?
6. What is a constructor?
7. What are the types of constructors?
8. What is constructor overloading?
9. What is constructor chaining?
10. What is the difference between this and super?
11. What is encapsulation?
12. What is inheritance?
13. What are the types of inheritance?
14. Why does Java not support multiple class inheritance?
15. How can Java achieve multiple inheritance through interfaces?
16. What is polymorphism?
17. What is compile-time polymorphism?
18. What is runtime polymorphism?
19. What is method overloading?
20. What is method overriding?
21. What is dynamic method dispatch?
22. Can we override static methods?
23. Can we overload static methods?
24. What is abstraction?
25. What is an abstract class?
26. What is an interface?
27. What is the difference between abstract class and interface?
28. Can an abstract class have a constructor?
29. Can an interface extend multiple interfaces?
30. What is the difference between HAS-A and IS-A?
31. What is composition?
32. What is aggregation?
33. What is the Object class?
34. What is the difference between final, finally and finalize()?
35. How do you implement OOP concepts in Selenium automation?
36. Explain how POM uses encapsulation.
37. Explain how WebDriver demonstrates polymorphism.
38. How do you decide between inheritance and composition in a framework?
39. How would you design a scalable hybrid automation framework using OOP?
40. Explain OOP concepts using your real-time automation project.

---

# 12. Day 06 Completion Checklist

- [ ] Understand classes and objects.
- [ ] Practise object creation.
- [ ] Understand constructors.
- [ ] Practise constructor overloading.
- [ ] Understand this and super.
- [ ] Understand encapsulation.
- [ ] Understand inheritance.
- [ ] Practise all supported inheritance structures.
- [ ] Understand HAS-A relationships.
- [ ] Understand polymorphism.
- [ ] Practise method overloading.
- [ ] Practise method overriding.
- [ ] Understand abstraction.
- [ ] Practise abstract classes.
- [ ] Practise interfaces.
- [ ] Understand static and final.
- [ ] Understand access modifiers.
- [ ] Complete at least 15 coding exercises.
- [ ] Practise OOP interview questions.
- [ ] Explain OOP concepts using Selenium examples.
- [ ] Push notes and programs to GitHub.

**Expected outcome:** Be able to design reusable Java classes, explain all four OOP pillars, implement inheritance and polymorphism, and confidently explain how OOP principles are applied in a real-time Selenium automation framework.

Object-Oriented Programming (OOP)
27 Questions with interview-ready answers
1. What are the four pillars of OOP?
Java is an object-oriented programming language based on four main principles: Encapsulation, Inheritance, Polymorphism, and Abstraction.
- Encapsulation: Wrapping data and methods into a single unit and restricting direct access to data.
- Inheritance: Acquiring properties and methods from a parent class to promote code reusability.
- Polymorphism: One method or behavior taking different forms through overloading and overriding.
- Abstraction: Hiding implementation details and exposing only essential functionality.
These principles help us develop reusable, maintainable, flexible, and scalable applications.

QA automation example:
- Encapsulation: Page Object Model classes.
- Inheritance: BaseTest and child test classes.
- Polymorphism: Method overloading and overriding in utility classes.
- Abstraction: WebDriver interface and browser implementations.
2. Explain encapsulation with a real-time example.
Encapsulation is the process of wrapping data and methods into a single class and restricting direct access to the data.

In Java, we achieve encapsulation by declaring variables as private and providing public getter and setter methods to access or update them.

For example, in a LoginPage class, I can declare username and password fields as private and provide methods such as enterUsername() and enterPassword().

This ensures that the internal implementation is controlled and accessed through defined methods.

Java example:
public class LoginPage {

    private String username;
    private String password;

    public void enterUsername(String username) {
        this.username = username;
    }

    public void enterPassword(String password) {
        this.password = password;
    }
}
QA example: In a Selenium framework, I keep WebElements private inside Page Object classes and expose public methods such as login() and clickSubmit(). This protects the internal page implementation and makes test scripts cleaner.
3. Explain inheritance and its types.
Inheritance is an OOP concept where one class acquires the properties and methods of another class using the extends keyword.

The class providing properties is called the parent or superclass, and the class inheriting them is called the child or subclass.

Java supports these types of inheritance:
1. Single inheritance: One child inherits from one parent.
2. Multilevel inheritance: A class inherits from a child class, forming multiple levels.
3. Hierarchical inheritance: Multiple child classes inherit from one parent.
4. Multiple inheritance: One class inherits from multiple parents. Java does not support this through classes, but it supports multiple inheritance of type through interfaces.
QA example: I create a BaseTest class containing browser initialization, driver management, and teardown methods. My LoginTest and BookingTest classes extend BaseTest and reuse those common methods.
4. Why doesn't Java support multiple inheritance through classes?
Java does not support multiple inheritance through classes mainly to avoid ambiguity and complexity.

For example, if two parent classes contain the same method and a child class inherits both, the compiler may not know which implementation should be used. This is commonly called the diamond problem.

To avoid this ambiguity, Java allows a class to extend only one class.

However, Java supports implementing multiple interfaces, allowing a class to inherit multiple behavioral contracts.

Example:
interface A {
    void display();
}

interface B {
    void display();
}

class C implements A, B {

    public void display() {
        System.out.println("Display method");
    }
}
Here, class C implements both interfaces and provides its own implementation.
5. What is polymorphism?
Polymorphism means one name or behavior can take multiple forms.

In Java, polymorphism allows us to perform similar operations in different ways depending on the method parameters or the actual object.

There are two main types:
- Compile-time polymorphism, achieved through method overloading.
- Runtime polymorphism, achieved through method overriding.
QA example: In our automation framework, we can create overloaded methods to perform different types of searches. We can also override browser-specific behavior in child classes.

Polymorphism improves flexibility, code reusability, and maintainability.
6. Explain compile-time and runtime polymorphism.
Java supports two types of polymorphism.

Compile-time polymorphism: It is achieved through method overloading. The compiler identifies which method to execute based on the method name and parameter list.

Runtime polymorphism: It is achieved through method overriding. The JVM determines which overridden instance method to execute based on the actual object at runtime.

Example:
class Search {

    void search(String name) {
        System.out.println(name);
    }

    void search(int id) {
        System.out.println(id);
    }
}
This is compile-time polymorphism.

Runtime example:
class Browser {
    void launch() {
        System.out.println("Browser launched");
    }
}

class Chrome extends Browser {
    @Override
    void launch() {
        System.out.println("Chrome launched");
    }
}
Browser browser = new Chrome();
browser.launch();
The Chrome implementation executes at runtime.
7. What is method overloading?
Method overloading means defining multiple methods with the same name in the same class but with different parameter lists.

The difference can be in the number of parameters, parameter types, or parameter order.

Method overloading is an example of compile-time polymorphism.

Important: Changing only the return type is not sufficient to overload a method.

Example:
class Login {

    void login(String username) {
        System.out.println(username);
    }

    void login(String username, String password) {
        System.out.println(username + password);
    }

    void login(int userId) {
        System.out.println(userId);
    }
}
QA example: I can create overloaded clickElement() or waitForElement() utility methods to support different input types or waiting conditions.
8. What is method overriding?
Method overriding occurs when a child class provides its own implementation of an instance method already defined in its parent class.

The method name and parameter list must match, and the return type must be the same or covariant.

We use the @Override annotation to indicate that a method is being overridden.

Method overriding is an example of runtime polymorphism.

Example:
class Parent {
    void display() {
        System.out.println("Parent method");
    }
}

class Child extends Parent {
    @Override
    void display() {
        System.out.println("Child method");
    }
}
QA example: I can override a common browser initialization method in a child test class if that particular test suite requires browser-specific setup.
9. Difference between method overloading and overriding.
Method overloading	Method overriding
Same method name with different parameters	Same method signature in parent and child
Usually happens within the same class	Requires inheritance
Compile-time polymorphism	Runtime polymorphism
Return type alone cannot distinguish methods	Return type must be compatible
Inheritance is not mandatory	Inheritance is required
Static methods can be overloaded	Static methods are hidden, not overridden


Interview explanation:

"Overloading means creating multiple methods with the same name but different parameter lists. Overriding means redefining a parent class method in a child class with the same signature. Overloading is resolved at compile time, whereas overriding is resolved at runtime."
10. Can we overload static methods?
Yes, we can overload static methods in Java.

Method overloading depends on the method name and parameter list, not whether the method is static or non-static.

Example:
class Utility {

    static void waitFor(int seconds) {
        System.out.println(seconds);
    }

    static void waitFor(String condition) {
        System.out.println(condition);
    }
}
Both methods are static, but their parameter lists are different.

Therefore, Java allows static method overloading.
11. Can we override static methods?
No, static methods cannot be overridden in Java because they belong to the class rather than individual objects.

If a child class defines a static method with the same signature as its parent class, it is called method hiding, not method overriding.

Example:
class Parent {
    static void display() {
        System.out.println("Parent");
    }
}

class Child extends Parent {
    static void display() {
        System.out.println("Child");
    }
}
The method called depends on the reference type when accessed through a class or reference, not runtime object polymorphism.
12. Can we override private methods?
No, private methods cannot be overridden because they are accessible only within the class in which they are declared.

A private method is not inherited by the child class.

If the child class declares a method with the same name and signature, it is considered a separate method, not an overridden method.

Example:
class Parent {

    private void display() {
        System.out.println("Parent");
    }
}

class Child extends Parent {

    void display() {
        System.out.println("Child");
    }
}
Here, the child's display method is independent of the parent's private method.
13. Can we override final methods?
No, we cannot override final methods in Java.

When a method is declared with the final keyword, its implementation cannot be changed by subclasses.

Example:
class Parent {

    final void display() {
        System.out.println("Parent");
    }
}

class Child extends Parent {

    // Cannot override display()
}
The compiler generates an error if we attempt to override the final method.

Remember:
- Final variable: cannot be reassigned after initialization.
- Final method: cannot be overridden.
- Final class: cannot be extended.
14. What is abstraction?
Abstraction is an OOP concept that hides internal implementation details and exposes only essential functionality to the user.

In Java, we achieve abstraction using abstract classes and interfaces.

For example, when we use Selenium WebDriver, we interact with methods such as get(), findElement(), and quit() without needing to understand their complete internal browser implementation.

QA example: We can define common browser operations in an interface and implement them separately for Chrome and Firefox.

This helps reduce implementation dependency and improves maintainability.
15. Difference between abstraction and encapsulation.
Both are OOP principles, but they solve different problems.
Abstraction	Encapsulation
Hides implementation details	Protects and controls access to data
Focuses on what an object does	Focuses on how data is accessed and maintained
Achieved using abstract classes and interfaces	Achieved using access modifiers and controlled methods
Reduces implementation complexity	Provides data protection


Interview explanation:

"Abstraction hides unnecessary implementation details and exposes only the required functionality. Encapsulation combines data and methods into a single unit and restricts direct access to the data. For example, WebDriver provides abstraction, while private WebElements and public page methods in POM demonstrate encapsulation."
16. Difference between abstract class and interface.
Abstract class	Interface
Declared using abstract class	Declared using interface
Can have abstract and concrete methods	Can have abstract, default, static, and private methods
Can have instance variables and constructors	Cannot have constructors or instance variables
Can have instance and static variables	Fields are implicitly public, static, and final
A class can extend only one class	A class can implement multiple interfaces
Can have different access modifiers for members	Interface methods have specific rules depending on their type


Interview explanation:

"An abstract class is useful when we want to provide common state and partial implementation to related classes. An interface is useful when we want to define a contract that different classes can implement. In automation frameworks, I can use an interface to define browser operations and separate implementations for different browsers."

Example:
interface BrowserActions {
    void launchBrowser();
    void closeBrowser();
}

class ChromeBrowser implements BrowserActions {

    public void launchBrowser() {
        System.out.println("Chrome launched");
    }

    public void closeBrowser() {
        System.out.println("Chrome closed");
    }
}
17. Can an abstract class have a constructor?
Yes, an abstract class can have a constructor.

Even though we cannot create an object directly from an abstract class, its constructor is executed when a concrete child class object is created.

It is mainly used to initialize common variables and shared resources.

Example:
abstract class BaseTest {

    BaseTest() {
        System.out.println("BaseTest constructor");
    }
}

class LoginTest extends BaseTest {

    LoginTest() {
        System.out.println("LoginTest constructor");
    }
}
When we create a LoginTest object, the BaseTest constructor executes first, followed by the LoginTest constructor.

QA example: We can use a BaseTest constructor to initialize common configuration data, although browser setup is often better handled through explicit setup methods or TestNG lifecycle annotations.
18. Can an interface have variables and implemented methods?
Yes. Java interfaces can contain variables and implemented methods, subject to specific rules.
- Variables declared in an interface are implicitly public static final.
- Interfaces can have abstract methods.
- From Java 8, interfaces support default and static methods with implementations.
- From Java 9, interfaces can also contain private methods to reuse internal logic.
Example:
interface Browser {

    int TIMEOUT = 30;

    void launch();

    default void close() {
        System.out.println("Closing browser");
    }

    static void browserInfo() {
        System.out.println("Browser interface");
    }
}
Here, TIMEOUT is a constant, launch() is abstract, close() is a default method, and browserInfo() is a static method.
19. Can an interface extend another interface?
Yes, an interface can extend another interface using the extends keyword.

An interface can extend multiple interfaces, unlike a class, which can extend only one class.

Example:
interface Login {
    void login();
}

interface Logout {
    void logout();
}

interface UserActions extends Login, Logout {
    void dashboard();
}
Here, UserActions inherits the contracts of both Login and Logout.

A class implementing UserActions must implement all inherited abstract methods unless it is itself abstract.
20. Can a class implement multiple interfaces?
Yes, Java supports multiple interface implementation.

A class can implement multiple interfaces using the implements keyword. This helps achieve multiple inheritance of type without the ambiguity of multiple class inheritance.

Example:
interface Login {
    void login();
}

interface Logout {
    void logout();
}

class User implements Login, Logout {

    public void login() {
        System.out.println("Login");
    }

    public void logout() {
        System.out.println("Logout");
    }
}
QA example: An automation class can implement multiple interfaces for browser actions, screenshots, and reporting capabilities.

One important point: if two interfaces provide conflicting default methods with the same signature, the implementing class must resolve the conflict explicitly.
21. What is the this keyword?
The this keyword in Java refers to the current object.

It is commonly used to differentiate instance variables from local variables when they have the same name.

It can also be used to:
- Call another constructor in the same class using this().
- Call current class methods.
- Pass the current object as an argument.
- Return the current object from a method.
Example:
class Employee {

    String name;

    Employee(String name) {
        this.name = name;
    }
}
Here, this.name refers to the instance variable, while name refers to the constructor parameter.

QA example: In Page Object Model classes, we can use this.driver = driver to assign the constructor parameter to the current object's WebDriver variable.
22. What is the super keyword?
The super keyword refers to the immediate parent class object or members.

It is mainly used for three purposes:
1. Access parent class variables.
2. Call parent class methods.
3. Call parent class constructors using super().
Example:
class Parent {

    String name = "Parent";

    void display() {
        System.out.println("Parent method");
    }
}

class Child extends Parent {

    String name = "Child";

    void show() {
        System.out.println(super.name);
        super.display();
    }
}
Here, super.name accesses the parent variable, and super.display() calls the parent method.

Important: super() must be the first statement in a constructor when explicitly used.
23. What is constructor overloading?
Constructor overloading means defining multiple constructors in the same class with different parameter lists.

It allows us to initialize objects in different ways depending on the information available.

Example:
class Employee {

    String name;
    int id;

    Employee() {
        name = "Unknown";
    }

    Employee(String name) {
        this.name = name;
    }

    Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }
}
Here, we have three constructors with different parameter lists.

QA example: We can create different constructors in page classes to initialize the driver, configuration, or test data depending on the framework design.
24. Can a constructor be inherited?
No, constructors cannot be inherited in Java.

However, when we create a child class object, the parent class constructor executes as part of the object initialization process.

If we do not explicitly call a parent constructor, Java inserts an implicit super() call when possible.

Example:
class Parent {

    Parent() {
        System.out.println("Parent constructor");
    }
}

class Child extends Parent {

    Child() {
        System.out.println("Child constructor");
    }
}
When we create a Child object, the Parent constructor executes first, followed by the Child constructor.
25. Can a constructor be overridden?
No, constructors cannot be overridden because constructors are not inherited by child classes.

Method overriding requires inheritance of an instance method, but constructors are used specifically for object initialization.

However, constructors can be overloaded within the same class by changing their parameter lists.

This is an important interview distinction:
- Constructor overloading: Yes.
- Constructor overriding: No.
- Constructor inheritance: No.
26. What is composition?
Composition is an OOP relationship where one class contains an object of another class and uses its functionality.

It represents a strong has-a relationship, where the contained object is typically owned by the containing object.

Example:
class Engine {

    void start() {
        System.out.println("Engine started");
    }
}

class Car {

    private Engine engine = new Engine();

    void startCar() {
        engine.start();
    }
}
Here, Car has an Engine object and uses its functionality. This is composition.

QA example: In a Selenium framework, a Test class can contain Page Object instances, utility objects, and reporting components. The test class uses these objects instead of implementing every functionality itself.

Composition promotes modularity, reusability, and maintainability.
27. Difference between inheritance and composition.
Inheritance	Composition
Represents an IS-A relationship	Represents a HAS-A relationship
Uses extends	Uses object references and object creation
Child inherits parent functionality	One class uses another class's functionality
Creates tighter coupling between parent and child	Often provides more flexible coupling
Useful when a genuine subtype relationship exists	Useful when functionality needs to be assembled from components


Interview explanation:

"Inheritance allows a child class to reuse properties and methods from a parent class. Composition allows one class to use another class's functionality by maintaining its object reference.

In automation framework design, I use inheritance for common test lifecycle operations through BaseTest and composition for reusable components such as Page Objects, utilities, and reporting classes.

I prefer composition when I need flexibility and independent component changes, rather than extending classes unnecessarily."