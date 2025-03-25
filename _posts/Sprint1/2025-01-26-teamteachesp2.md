---
layout: post
title: Team Teaches Part 2
courses: {'csa': {'week': 21}}
type: ccc
comments: True
---

Overall, doing a team teach, and listening to all the others was a very enjoyable experience. I took notes on the units and summarized them below. 
## Unit 10: Recursion

### Recursion Overview
- **Recursion** is when a function calls itself to break a problem into smaller subproblems until it reaches a **base case**.

### AP Exam Weight
- **5-7.5%** → **Only MCQs** have recursion; **no recursive FRQs**.

### Recursive vs. Iterative
- **Iteration** uses loops; **recursion** calls itself.
- Recursion takes **more memory** but can be **more elegant**.
- Risk of **stack overflow** if the base case isn’t defined.

### Key Concepts
- **Base Case** → Stops recursion.
- **Recursive Case** → Calls itself on a smaller problem.

### Examples
- **Factorial**  
- **Sum of Digits**  
- **Recursive Multiplication**  
- **Binary Search**  

### Recursive Binary Search
- Efficiently finds a target in a **sorted array** by splitting the search space in half.
- **Steps:**
  1. Find the middle.  
  2. If it’s the target, return it.  
  3. If it’s smaller, search right; if larger, search left.  
  4. Repeat until found or search space is empty.  
- **Faster than linear search**, especially on big datasets.

### Tracing Recursive Calls
- Understanding how the function breaks down and returns results.

**Confidence Score: 9/10**

## Methods & Control Structures

### AP EXAM WEIGHT
15-22.5%

### What are Methods?
- Reusable code that performs specific tasks.
- Helps break down programs into manageable parts.

### Key Parts of a Method:
- **Modifier**: Describes the method’s properties.
    - **Access Modifiers**: Determines who can access the method.
      - **public**: Accessible everywhere.
      - **private**: Accessible only within the class.
      - **protected**: Accessible within the package and subclasses.
      - **Default (no modifier)**: Accessible within the package.
    - **Non-Access Modifiers**: Additional properties of the method.
      - **static**: Belongs to the class, not the object.
      - **final**: Cannot be overridden.

- **Method name**: Defines the method (e.g., `public int add(int a, int b)`).
- **Return Types**: Specifies what the method returns (e.g., `int`, `void`).
- **Parameters**: Inputs for dynamic behavior.
- **Method Body**: Contains the code to be executed.

### Types of Methods:
- **Instance**: Belongs to objects (e.g., `myObject.method()`).
- **Static**: Belongs to the class (e.g., `ClassName.method()`).


### Conditional Statements:
- Use `if`, `else if`, and `else` to make decisions.
    Example:
    ```java
    if (x > 0) {
        System.out.println("Positive");
    }
    ```

### Loops:
- Repeat code using:
  - **for**: Known iterations.
    Example:
    ```java
    for (int i = 0; i < 5; i++) {
        // code
    }
    ```
  - **while**: Runs while a condition is true.
    Example:
    ```java
    while (x < 10) {
        // code
    }
    ```
  - **do-while**: Runs at least once.
    Example:
    ```java
    do {
        // code
    } while (x < 10);
    ```


## Classes

### Intro/Review

### What Are Classes in Java?
- **Definition**: A class is a blueprint for creating objects. It encapsulates data (fields) and behaviors (methods).

### Why Are Classes Important?
- Organize code into reusable, modular units.
- Support **Object-Oriented Programming (OOP)** principles:
  - **Encapsulation**: Keep data safe by hiding it.
  - **Abstraction**: Simplify complex systems.
  - **Inheritance**: Reuse code.
  - **Polymorphism**: Make programs more flexible and scalable.

### Components of a Class:
- **Fields (Attributes)**: Variables that represent the state of the object.
- **Methods**: Functions that define the object’s behavior.
- **Constructors**: Special methods to initialize objects.
- **Access Modifiers**: Define how fields and methods can be accessed (private, public, protected).

### Levels of Access:
- **private**: Accessible only within the class.
- **public**: Accessible anywhere.
- **protected**: Accessible within the package and subclasses.
- **Default (no modifier)**: Accessible within the package.

## Object-Oriented Programming Principles

### Encapsulation:
- Keep fields private, provide controlled access using getters and setters.

### Inheritance:
- Allow a new class (subclass) to inherit from an existing class (superclass).

### Polymorphism:
- The ability to use the same method name in different contexts.
  - **Method Overloading**: Same method name, different parameter lists.
  - **Method Overriding**: Subclass provides a specific implementation of a method from the superclass.

## During the Exam

- **Constructors**: Initialize objects.
- **Static Variables**: Not always given, will need to identify on your own.
- **Methods**: Names are given, code is the task. **Methods team teach** applies here.
- **Levels of Access**: Don’t mess this up, you’ll lose points.

## ArrayList Methods Cheat Sheet

### 1. Creating an ArrayList
- ArrayList is used to store a dynamic list of objects.
- Syntax: `ArrayList<Type> list = new ArrayList<Type>();`

### 2. Common Methods

#### Add Elements
- `list.add(value);` → Appends a value to the end.
- `list.add(index, value);` → Inserts value at a specific index.

#### Access Elements
- `list.get(index);` → Returns the element at the specified index.

#### Update Elements
- `list.set(index, value);` → Replaces the element at index with a new value.

#### Remove Elements
- `list.remove(index);` → Deletes the element at the specified index.
- `list.remove(value);` → Deletes the first occurrence of a value.

#### Size of the List
- `list.size();` → Returns the number of elements in the list.

#### Check for Elements
- `list.contains(value);` → Checks if the list contains a specified value.
- `list.indexOf(value);` → Returns the index of the first occurrence of a value, or -1 if not found.

## ArrayList Loops Cheat Sheet

### 1. Traversing an ArrayList
- Use a regular `for` loop or a `for-each` loop to go through each element in the list.

### 2. Using a For-Each Loop
- Simplified loop, no need to manually access indexes.

### 3. Modifying Elements
- Use a `for` loop to modify elements by index.

### 4. Avoid ConcurrentModificationException
- Cannot modify the ArrayList while using a `for-each` loop. Use a regular `for` loop or an iterator.

### 5. Nested Loops with ArrayLists
- Use nested loops to compare or process multiple elements in the ArrayList.


# Possible Penalties in Coding
Array/Collection Access Confusion

Confusing array access ([]) with collection access (.get()).
Extraneous Code That Causes Side Effects

Adding unnecessary code that affects the program’s behavior (e.g., printing messages inside methods when not needed).
Local Variables Used but None Declared

Using local variables without declaring them first.
Destruction of Persistent Data

Modifying data unintentionally by passing mutable objects (e.g., StringBuilder) to methods.
Void Method or Constructor That Returns a Value

Returning a value from a method or constructor that is declared void.
