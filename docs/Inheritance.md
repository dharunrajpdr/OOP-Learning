# 📘 Java OOPs – Inheritance

> 💡 **In this lesson:** Learn how one class can acquire the properties and methods of another class.

---

# 1️⃣ What is Inheritance?

**Inheritance** is a mechanism where one class acquires the properties and methods of another class.

### 🧠 Simple Definition

> Inheritance allows a child class to reuse the properties and methods of a parent class.

### Real-World Example 👨‍👦

Think about:

```text
Parent
  ↓
Child
```

A child can inherit certain characteristics from their parent.

Similarly, in Java:

```text
Parent Class
      ↓
Child Class
```

The child class can use members of the parent class.

---

# 2️⃣ Basic Syntax

We use the `extends` keyword.

```java
class Parent {
    // properties and methods
}

class Child extends Parent {
    // additional properties and methods
}
```

---

# 3️⃣ Simple Example

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

    public static void main(String[] args) {

        Dog d = new Dog();

        d.eat();
        d.bark();
    }
}
```

### 📤 Output

```text
Animal eats
Dog barks
```

### 🔍 What happened?

```text
Animal
  |
  | extends
  ↓
Dog
```

`Dog` inherits the `eat()` method from `Animal`.

So the `Dog` object can call:

```java
d.eat();
```

even though `eat()` is defined in `Animal`.

---

# 4️⃣ Important Terms

| Term | Meaning |
|---|---|
| Parent Class | Class being inherited from |
| Child Class | Class that inherits |
| Superclass | Another name for parent class |
| Subclass | Another name for child class |
| `extends` | Keyword used for class inheritance |

Example:

```java
class Animal {
}

class Dog extends Animal {
}
```

Here:

```text
Animal → Parent / Superclass
Dog    → Child / Subclass
```

---

# 5️⃣ Why Do We Use Inheritance?

### ♻️ 1. Code Reusability

We can reuse existing code.

```java
class Animal {

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
}
```

`Dog` can directly use:

```java
eat();
```

---

### 🔧 2. Less Code Duplication

Instead of writing the same method again:

```text
Animal
   ↓
Common functionality
   ↓
Dog
Cat
Cow
```

Common functionality can be placed in the parent class.

---

### 🔄 3. Method Overriding

Inheritance allows a child class to provide its own implementation of a parent method.

This is important for **runtime polymorphism**.

Example:

```java
class Animal {

    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

We will study method overriding in detail later.

---

# 6️⃣ Types of Inheritance in Java

Java mainly supports:

```text
1. Single Inheritance
2. Multilevel Inheritance
3. Hierarchical Inheritance
```

Java does **not** support multiple inheritance through classes.

---

# 7️⃣ Single Inheritance

One child inherits from one parent.

```text
Animal
   ↓
 Dog
```

### Example

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
```

Here:

```text
Animal → Parent
Dog    → Child
```

---

# 8️⃣ Multilevel Inheritance

A class inherits from another child class.

```text
Animal
   ↓
 Dog
   ↓
 Puppy
```

### Example

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

class Puppy extends Dog {

    void play() {
        System.out.println("Playing");
    }
}
```

Now `Puppy` can access:

```text
eat()
bark()
play()
```

because:

```text
Puppy
  ↓
Dog
  ↓
Animal
```

---

# 9️⃣ Hierarchical Inheritance

Multiple child classes inherit from the same parent.

```text
          Animal
         /      \
        ↓        ↓
       Dog      Cat
```

### Example

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

Both `Dog` and `Cat` can use:

```java
eat();
```

because both inherit from `Animal`.

---

# 🔟 Multiple Inheritance

Multiple inheritance means one class inherits from multiple classes.

Conceptually:

```text
    Animal     Vehicle
       \        /
        \      /
         ↓    ↓
          ????
```

Java **does not support multiple inheritance using classes**.

Example:

```java
class A {
}

class B {
}

// ❌ Not allowed in Java
class C extends A, B {
}
```

This is not valid Java syntax.

### Why?

One major reason is the **diamond problem**, where the compiler could face ambiguity about which inherited method to use.

Java can achieve multiple inheritance of type using **interfaces**, which we will learn later.

---

# 1️⃣1️⃣ `extends` Keyword

The `extends` keyword is used to inherit from a class.

```java
class Parent {
}

class Child extends Parent {
}
```

### 🧠 Memory Trick

```text
extends → Class Inheritance
```

---

# 1️⃣2️⃣ What Can a Child Class Inherit?

A child class can inherit accessible members of the parent class.

For example:

```java
class Parent {

    int x = 10;

    void display() {
        System.out.println("Parent method");
    }
}

class Child extends Parent {

    void show() {
        System.out.println(x);
        display();
    }
}
```

The child can use:

```text
x
display()
```

---

# 1️⃣3️⃣ What About `private` Members?

Private members belong to the parent class and cannot be accessed directly by the child class.

Example:

```java
class Parent {

    private int x = 10;
}

class Child extends Parent {

    void display() {

        // System.out.println(x); ❌ Error
    }
}
```

The child cannot directly access `x`.

However, the parent can provide a method to access it:

```java
class Parent {

    private int x = 10;

    public int getX() {
        return x;
    }
}

class Child extends Parent {

    void display() {
        System.out.println(getX());
    }
}
```

---

# 1️⃣4️⃣ Inheritance Example with Real-World Design

Consider a company.

```text
             Employee
                |
        ┌───────┴───────┐
        ↓               ↓
    Developer         Manager
```

Common properties:

```text
name
salary
displayDetails()
```

can be placed in `Employee`.

Specific behavior can be placed in:

```text
Developer
Manager
```

This helps avoid duplicate code.

---

# 1️⃣5️⃣ Complete Example

```java
class Employee {

    String name;
    double salary;

    void displayEmployee() {
        System.out.println("Name: " + name);
        System.out.println("Salary: " + salary);
    }
}

class Developer extends Employee {

    String language;

    void displayDeveloper() {
        System.out.println("Language: " + language);
    }

    public static void main(String[] args) {

        Developer d = new Developer();

        d.name = "Dharun";
        d.salary = 50000;
        d.language = "Java";

        d.displayEmployee();
        d.displayDeveloper();
    }
}
```

### 📤 Output

```text
Name: Dharun
Salary: 50000.0
Language: Java
```

---

# 1️⃣6️⃣ Inheritance Structure

```text
                 Parent Class
                     |
                  extends
                     ↓
                 Child Class
                     |
              ┌──────┴──────┐
              ↓             ↓
       Parent Members   Child Members
```

The child can use its own members plus accessible inherited members.

---

# 1️⃣7️⃣ Advantages of Inheritance

### ♻️ Code Reusability

Reuse existing code.

### 🧹 Less Duplication

Common functionality can be placed in the parent.

### 🔧 Easy Maintenance

Changes to common functionality can be managed in one place.

### 🔄 Supports Polymorphism

Inheritance works closely with method overriding and runtime polymorphism.

---

# 1️⃣8️⃣ Inheritance vs Encapsulation

| Encapsulation | Inheritance |
|---|---|
| Protects data | Reuses code |
| Uses private variables and methods | Uses `extends` |
| Focuses on data protection | Focuses on parent-child relationship |
| Example: getter/setter | Example: `Dog extends Animal` |

### 🧠 Memory Trick

```text
Encapsulation → Protect
Inheritance   → Reuse
```

---

# 1️⃣9️⃣ Important Interview Questions ⭐

### Q1. What is inheritance?

> Inheritance is a mechanism where a child class acquires accessible properties and methods from a parent class.

### Q2. Which keyword is used for inheritance?

> `extends`

### Q3. What is the main advantage of inheritance?

> Code reusability.

### Q4. What is a superclass?

> A superclass is another name for the parent class.

### Q5. What is a subclass?

> A subclass is another name for the child class.

### Q6. Does Java support multiple inheritance?

> Java does not support multiple inheritance through classes, but it can be achieved through interfaces.

### Q7. What are the types of inheritance supported through Java classes?

> Single, multilevel, and hierarchical inheritance.

### Q8. Can a child class directly access a private member of its parent?

> No. A private member cannot be directly accessed outside the class where it is declared.

---

# 🧠 Quick Revision

```text
Inheritance
     ↓
Parent → Child relationship
     ↓
extends keyword
     ↓
Code Reusability
```

### Types

```text
Single

A
↓
B
```

```text
Multilevel

A
↓
B
↓
C
```

```text
Hierarchical

    A
   / \
  B   C
```

### ⭐ One-Line Memory Trick

```text
Inheritance = IS-A relationship + Code Reusability
```

Example:

```text
Dog IS-A Animal
Car IS-A Vehicle
Developer IS-A Employee
```

---

# 📝 Practice Questions

### Basic

1. Create an `Animal` class with an `eat()` method and inherit it in a `Dog` class.

2. Create:
   ```text
   Vehicle
      ↓
     Car
   ```
   Add one method to each class.

3. Create multilevel inheritance:
   ```text
   Person → Employee → Developer
   ```

4. Create hierarchical inheritance:
   ```text
          Animal
         /      \
        Dog      Cat
   ```

### Interview Practice

5. What is inheritance?

6. What is the difference between superclass and subclass?

7. Why is inheritance used?

8. What is the `extends` keyword?

9. Does Java support multiple inheritance using classes?

10. What is the difference between single, multilevel, and hierarchical inheritance?

---

# ⭐ Key Point

> **Inheritance allows a child class to reuse accessible properties and methods of a parent class.**

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
```

```text
Animal → Parent
Dog    → Child
extends → Inheritance
```
