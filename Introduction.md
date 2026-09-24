# 📘 Java OOPs – Complete Learning Order

> A beginner-friendly roadmap to learn Java Object-Oriented Programming step by step.

---

# 📚 OOPs Learning Order

```text
1.  OOPs Introduction
        ↓
2.  Class & Object
        ↓
3.  Encapsulation
        ↓
4.  Inheritance
        ↓
5.  Polymorphism
        ↓
6.  Abstraction
        ↓
7.  Interface
        ↓
8.  Abstract Class
        ↓
9.  Constructor
        ↓
10. this Keyword
        ↓
11. super Keyword
        ↓
12. Method Overloading
        ↓
13. Method Overriding
        ↓
14. Access Modifiers
        ↓
15. static Keyword
        ↓
16. final Keyword
        ↓
17. Association
        ↓
18. Aggregation
        ↓
19. Composition
        ↓
20. OOPs Interview Questions
```

---

# 1️⃣ OOPs Introduction

## 📌 What is OOPs?

**OOPs = Object-Oriented Programming System**

OOP is a programming approach where we organize programs using **classes and objects**.

### 🧠 Four Main Pillars

```text
Encapsulation
Inheritance
Polymorphism
Abstraction
```

### Easy Memory

```text
Encapsulation → Hide Data + Control Access

Inheritance → Reuse Existing Code

Polymorphism → One Name → Many Forms

Abstraction → Hide Implementation Details
```

---

# 2️⃣ Class & Object

## 📌 Class

A **class** is a blueprint or template used to create objects.

```java
class Student {
    String name;
    int age;
}
```

## 📌 Object

An **object** is an instance of a class.

```java
Student s = new Student();
```

### 🧠 Easy Memory

```text
Class  → Blueprint
Object → Real Instance
new    → Creates Object
.      → Accesses Members
```

---

# 3️⃣ Encapsulation

## 📌 Definition

Encapsulation means **wrapping data and methods inside a class and controlling access to the data**.

Usually achieved using:

```text
private variables
+
public getters/setters
```

Example:

```java
class Student {

    private String name;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

### 🧠 Easy Memory

```text
Encapsulation
      ↓
Hide Data
      +
Control Access
```

---

# 4️⃣ Inheritance

## 📌 Definition

Inheritance allows a child class to acquire accessible properties and methods from a parent class.

Syntax:

```java
class Child extends Parent {
}
```

Example:

```java
class Animal {

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
}
```

### 🧠 Easy Memory

```text
Inheritance
     ↓
IS-A
     ↓
Code Reusability
```

Example:

```text
Dog IS-A Animal
```

---

# 5️⃣ Polymorphism

## 📌 Definition

Polymorphism means **one name can have multiple forms**.

There are two main types:

```text
Compile-time Polymorphism
        ↓
Method Overloading

Runtime Polymorphism
        ↓
Method Overriding
```

### Example

```java
Animal a = new Dog();
```

The reference is `Animal`, but the actual object is `Dog`.

### 🧠 Easy Memory

```text
Overloading → Compile Time
Overriding  → Runtime
```

---

# 6️⃣ Abstraction

## 📌 Definition

Abstraction means **hiding unnecessary implementation details and showing only essential functionality**.

Mainly achieved using:

```text
Abstract Class
Interface
```

Example:

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Eating");
    }
}
```

### 🧠 Easy Memory

```text
Abstraction
     ↓
WHAT to do
     ↓
Hide HOW it is done
```

---

# 7️⃣ Interface

## 📌 Definition

An interface is a **contract** that defines behavior a class should provide.

Example:

```java
interface Animal {
    void sound();
}

class Dog implements Animal {

    public void sound() {
        System.out.println("Bark");
    }
}
```

### Important Keyword

```text
interface → creates interface

implements → class implements interface
```

### Multiple Interfaces

```java
class C implements A, B {
}
```

### 🧠 Easy Memory

```text
Interface
     ↓
Contract
     ↓
implements
```

---

# 8️⃣ Abstract Class

## 📌 Definition

An abstract class is a class declared using the `abstract` keyword.

It can contain:

```text
Abstract methods
Concrete methods
Variables
Constructors
Static methods
Final methods
```

Example:

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Eating");
    }
}
```

### Important Point

You cannot directly create an object of an abstract class.

```java
Animal a = new Animal(); // ❌
```

But you can use it as a reference:

```java
Animal a = new Dog(); // ✅
```

### 🧠 Easy Memory

```text
Abstract Class
      ↓
Common Code
      +
Incomplete Methods
```

---

# 9️⃣ Constructor

## 📌 Definition

A constructor is a special block used to initialize an object.

### Rules

```text
Same name as class
No return type
Automatically called
Can be overloaded
Not inherited
```

Example:

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }
}
```

### 🧠 Easy Memory

```text
Constructor
     ↓
Initializes Object
```

---

# 🔟 this Keyword

## 📌 Definition

`this` refers to the **current object**.

Example:

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }
}
```

Here:

```text
this.name → instance variable
name      → parameter
```

### Other Uses

```java
this.method();
this();
return this;
```

### 🧠 Easy Memory

```text
this
 ↓
Current Object
```

---

# 1️⃣1️⃣ super Keyword

## 📌 Definition

`super` refers to the **immediate parent class**.

### Uses

```java
super.variable;
super.method();
super();
```

Example:

```java
class Animal {

    String name = "Animal";
}

class Dog extends Animal {

    String name = "Dog";

    void display() {
        System.out.println(super.name);
    }
}
```

Output:

```text
Animal
```

### 🧠 Easy Memory

```text
this  → Current Class
super → Parent Class
```

---

# 1️⃣2️⃣ Method Overloading

## 📌 Definition

Method overloading means having **multiple methods with the same name but different parameter lists**.

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

### Can Change

```text
Number of parameters
Type of parameters
Order of parameters
```

### Cannot Change Only

```text
Return type
```

Example:

```java
int add(int a, int b)
double add(int a, int b)  // ❌
```

### 🧠 Easy Memory

```text
Overloading
     ↓
Same Method Name
     +
Different Parameters
     ↓
Compile Time
```

---

# 1️⃣3️⃣ Method Overriding

## 📌 Definition

Method overriding occurs when a child class provides its own implementation of a method inherited from the parent class.

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
        System.out.println("Bark");
    }
}
```

### Important

```java
Animal a = new Dog();
a.sound();
```

Output:

```text
Bark
```

### 🧠 Easy Memory

```text
Overriding
     ↓
Same Method Signature
     +
Different Implementation
     ↓
Runtime
```

---

# 1️⃣4️⃣ Access Modifiers

Java has four main access levels:

```text
public
protected
default
private
```

| Modifier | Same Class | Same Package | Subclass | Other Package |
|---|---|---|---|---|
| `public` | ✅ | ✅ | ✅ | ✅ |
| `protected` | ✅ | ✅ | ✅* | ❌* |
| default | ✅ | ✅ | ❌ | ❌ |
| `private` | ✅ | ❌ | ❌ | ❌ |

### 🧠 Easy Memory

```text
public    → Everywhere
protected → Package + Subclass
default   → Same Package
private   → Same Class
```

---

# 1️⃣5️⃣ static Keyword

## 📌 Definition

`static` means the member belongs to the **class rather than individual objects**.

Example:

```java
class Student {

    static String college = "VSB";
}
```

Access:

```java
System.out.println(Student.college);
```

### Static Method

```java
static void display() {
    System.out.println("Hello");
}
```

### Important

A static method can directly access static members.

```text
static → class-level
```

### 🧠 Easy Memory

```text
static
   ↓
Class / Shared
```

---

# 1️⃣6️⃣ final Keyword

## 📌 Definition

`final` is used to restrict modification.

### Final Variable

```java
final int x = 10;
```

Cannot reassign:

```java
x = 20; // ❌
```

### Final Method

Cannot be overridden.

```java
final void display() {
}
```

### Final Class

Cannot be inherited.

```java
final class Animal {
}
```

### 🧠 Easy Memory

```text
final variable → Cannot reassign

final method → Cannot override

final class → Cannot extend
```

---

# 1️⃣7️⃣ Association

## 📌 Definition

Association represents a **relationship between two independent objects**.

Example:

```text
Teacher ↔ Student
```

A teacher teaches a student, but both can exist independently.

### Types

```text
One-to-One
One-to-Many
Many-to-One
Many-to-Many
```

### 🧠 Easy Memory

```text
Association
     ↓
General Relationship
     ↓
Independent Objects
```

---

# 1️⃣8️⃣ Aggregation

## 📌 Definition

Aggregation is a **weak HAS-A relationship** where the contained object can exist independently.

Example:

```text
Department ─── Teacher
```

A department has teachers, but teachers can exist independently.

### 🧠 Easy Memory

```text
Aggregation
     ↓
Weak HAS-A
     ↓
Independent Part
```

---

# 1️⃣9️⃣ Composition

## 📌 Definition

Composition is a **strong HAS-A relationship** where the whole strongly owns and manages the part.

Example:

```text
House ─── Room
```

### 🧠 Easy Memory

```text
Composition
     ↓
Strong HAS-A
     ↓
Strong Ownership
```

---

# 🔥 Association vs Aggregation vs Composition

| Concept | Relationship | Ownership | Example |
|---|---|---|---|
| Association | General relationship | No ownership necessarily | Teacher ↔ Student |
| Aggregation | Weak HAS-A | Weak | Department → Teacher |
| Composition | Strong HAS-A | Strong | House → Room |

### Super Easy Memory

```text
Association
     ↓
Relationship

Aggregation
     ↓
Weak HAS-A

Composition
     ↓
Strong HAS-A
```

---

# 🧠 Complete OOPs Memory Map

```text
                    OOPs
                     |
        ┌────────────┴────────────┐
        ↓                         ↓
     Classes                   Objects
        |
        ↓
    4 Pillars
        |
   ┌────┼────┬────┐
   ↓    ↓    ↓    ↓
  Enc  Inh  Poly  Abs
   |    |    |     |
   |    |    |     ├── Interface
   |    |    |     └── Abstract Class
   |    |    |
   |    |    ├── Overloading
   |    |    └── Overriding
   |    |
   |    └── extends
   |
   └── Getters / Setters

Other Important Concepts
        |
        ├── Constructor
        ├── this
        ├── super
        ├── Access Modifiers
        ├── static
        ├── final
        ├── Association
        ├── Aggregation
        └── Composition
```

---

# 🎯 Most Important Topics for Interviews

## ⭐ High Priority

```text
1. Class & Object
2. Encapsulation
3. Inheritance
4. Polymorphism
5. Abstraction
6. Interface
7. Abstract Class
8. Constructor
9. Method Overloading
10. Method Overriding
```

## 🟢 Basic Understanding is Enough

```text
11. this
12. super
13. Access Modifiers
14. static
15. final
16. Association
17. Aggregation
18. Composition
```

---

# ⚡ Final OOPs Revision

```text
Class       → Blueprint
Object      → Instance

Encapsulation → Hide + Control Data

Inheritance → IS-A

Polymorphism → Many Forms
              ├── Overloading → Compile Time
              └── Overriding  → Runtime

Abstraction → Hide Implementation

Interface → Contract

Abstract Class → Common Code + Abstract Methods

Constructor → Initialize Object

this → Current Object

super → Parent Class

static → Class Level

final → Restriction

Association → General Relationship

Aggregation → Weak HAS-A

Composition → Strong HAS-A
```

---
