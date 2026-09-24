# 📘 Java OOPs – Interface

> 💡 **In this lesson:** Learn what an interface is, how to create and implement one, and why interfaces are used in Java.

---

# 1️⃣ What is an Interface?

An **interface** is a blueprint that defines a contract for a class.

It specifies what a class should do, while the implementing class provides the actual implementation.

### 🧠 Simple Definition

> An interface is a contract that contains method declarations and is implemented by classes.

### Easy Example

Think of a **remote control** 📺.

A remote may define:

```text
powerOn()
powerOff()
increaseVolume()
```

Different TVs can implement these operations differently.

```text
          Remote Interface
          /       |       \
         ↓        ↓        ↓
       Sony      LG     Samsung
```

---

# 2️⃣ Why Do We Use Interfaces?

Interfaces are mainly used for:

- Abstraction
- Achieving multiple inheritance of type
- Loose coupling
- Defining common behavior
- Supporting polymorphism

### 🧠 Memory Trick

```text
Interface = Contract
```

If a class implements an interface, it agrees to provide the required behavior.

---

# 3️⃣ Basic Syntax

```java
interface Animal {

    void sound();
}
```

A class implements an interface using:

```java
class Dog implements Animal {

    public void sound() {
        System.out.println("Dog barks");
    }
}
```

### Important

```text
Class → extends → Class

Class → implements → Interface
```

---

# 4️⃣ Simple Example

```java
interface Animal {

    void sound();
}

class Dog implements Animal {

    public void sound() {
        System.out.println("Dog barks");
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        d.sound();
    }
}
```

### 📤 Output

```text
Dog barks
```

---

# 5️⃣ How Does It Work?

The interface defines:

```java
void sound();
```

It says:

> Any class implementing `Animal` must provide `sound()`.

The `Dog` class provides the implementation:

```java
public void sound() {
    System.out.println("Dog barks");
}
```

So:

```text
Interface
    ↓
Defines WHAT
    ↓
Implementing Class
    ↓
Defines HOW
```

---

# 6️⃣ `implements` Keyword

A class uses the `implements` keyword to implement an interface.

Example:

```java
interface Vehicle {

    void start();
}

class Car implements Vehicle {

    public void start() {
        System.out.println("Car starts");
    }
}
```

### 🧠 Memory Trick

```text
extends    → Class inheritance
implements → Interface implementation
```

---

# 7️⃣ Interface Reference

We can create an interface reference pointing to an implementing class object.

```java
Animal a = new Dog();
```

Here:

```text
Animal → Interface reference
Dog    → Actual object
```

Example:

```java
interface Animal {

    void sound();
}

class Dog implements Animal {

    public void sound() {
        System.out.println("Dog barks");
    }

    public static void main(String[] args) {

        Animal a = new Dog();

        a.sound();
    }
}
```

### 📤 Output

```text
Dog barks
```

This is also an example of **runtime polymorphism**.

---

# 8️⃣ Multiple Interfaces

A class can implement multiple interfaces.

This is one important feature of Java.

Example:

```java
interface A {

    void methodA();
}

interface B {

    void methodB();
}

class C implements A, B {

    public void methodA() {
        System.out.println("Method A");
    }

    public void methodB() {
        System.out.println("Method B");
    }

    public static void main(String[] args) {

        C obj = new C();

        obj.methodA();
        obj.methodB();
    }
}
```

### 📤 Output

```text
Method A
Method B
```

The class:

```java
class C implements A, B
```

implements both interfaces.

---

# 9️⃣ Interface and Multiple Inheritance

Java does not allow:

```java
class C extends A, B
```

❌ Not allowed.

But Java allows:

```java
class C implements A, B
```

✅ Allowed.

Therefore, interfaces provide a way to achieve **multiple inheritance of type**.

### 🧠 Remember

```text
Multiple Classes
      ↓
❌ Not allowed

Multiple Interfaces
      ↓
✅ Allowed
```

---

# 🔟 Interface Variables

Variables declared in an interface are implicitly:

```text
public
static
final
```

Example:

```java
interface Constants {

    int MAX = 100;
}
```

This is treated approximately as:

```java
public static final int MAX = 100;
```

So:

```java
System.out.println(Constants.MAX);
```

is valid.

But:

```java
Constants.MAX = 200;
```

❌ Not allowed because it is `final`.

---

# 1️⃣1️⃣ Interface Methods

Traditionally, interface methods were mainly abstract methods.

Example:

```java
interface Animal {

    void sound();
}
```

The method:

```java
void sound();
```

is implicitly:

```java
public abstract void sound();
```

### Important ⭐

When a class implements an interface, the implemented method should normally be declared `public`.

```java
class Dog implements Animal {

    public void sound() {
        System.out.println("Dog barks");
    }
}
```

---

# 1️⃣2️⃣ Default Methods

Modern Java interfaces can contain `default` methods with implementation.

Example:

```java
interface Animal {

    void sound();

    default void eat() {
        System.out.println("Animal eats");
    }
}
```

A class can implement the interface:

```java
class Dog implements Animal {

    public void sound() {
        System.out.println("Dog barks");
    }
}
```

Now:

```java
Dog d = new Dog();

d.sound();
d.eat();
```

### 📤 Output

```text
Dog barks
Animal eats
```

---

# 1️⃣3️⃣ Static Methods in Interfaces

Interfaces can also contain static methods.

Example:

```java
interface Utility {

    static void show() {
        System.out.println("Static method");
    }
}
```

Call it using the interface name:

```java
Utility.show();
```

### 📤 Output

```text
Static method
```

We don't call interface static methods through an object.

---

# 1️⃣4️⃣ Interface Cannot Be Instantiated

We cannot create an object directly from an interface.

Example:

```java
interface Animal {

    void sound();
}
```

This is invalid:

```java
Animal a = new Animal();   // ❌ Error
```

But this is valid:

```java
Animal a = new Dog();
```

where `Dog` implements `Animal`.

---

# 1️⃣5️⃣ Interface vs Abstract Class

This is a very common interview question. ⭐⭐⭐

| Interface | Abstract Class |
|---|---|
| Uses `interface` keyword | Uses `abstract class` |
| Class uses `implements` | Class uses `extends` |
| Supports multiple interfaces | A class can extend only one class |
| Variables are `public static final` by default | Can have normal instance variables |
| Traditionally used for contracts | Can provide partial implementation |
| Cannot be directly instantiated | Cannot be directly instantiated |

### 🧠 Easy Memory Trick

```text
Interface
    ↓
Contract / Capability

Abstract Class
    ↓
Common Base / Partial Implementation
```

---

# 1️⃣6️⃣ Interface Example – Payment

Consider a payment system.

```java
interface Payment {

    void pay();
}
```

Different classes can implement it:

```java
class UPI implements Payment {

    public void pay() {
        System.out.println("Payment using UPI");
    }
}

class CreditCard implements Payment {

    public void pay() {
        System.out.println("Payment using Credit Card");
    }
}
```

Usage:

```java
Payment p1 = new UPI();
Payment p2 = new CreditCard();

p1.pay();
p2.pay();
```

### 📤 Output

```text
Payment using UPI
Payment using Credit Card
```

Same interface:

```text
Payment
```

Different implementations:

```text
UPI
CreditCard
```

This demonstrates:

```text
Abstraction + Polymorphism
```

---

# 1️⃣7️⃣ Interface and Loose Coupling

Interfaces help create **loosely coupled** code.

Example:

```java
Payment payment = new UPI();
```

The code depends on:

```text
Payment interface
```

rather than directly depending on the specific implementation.

We can later change:

```java
Payment payment = new CreditCard();
```

without changing the overall design.

### 🧠 Simple Meaning

> Loose coupling means reducing direct dependency between classes.

---

# 1️⃣8️⃣ Important Interview Questions ⭐

### Q1. What is an interface?

> An interface is a contract that defines behavior that implementing classes must provide.

### Q2. Which keyword is used to implement an interface?

> `implements`

### Q3. Can we create an object of an interface?

> No, an interface cannot be directly instantiated.

### Q4. Can a class implement multiple interfaces?

> Yes.

Example:

```java
class C implements A, B {
}
```

### Q5. Can an interface extend another interface?

> Yes.

Example:

```java
interface A {
}

interface B extends A {
}
```

### Q6. Can an interface extend multiple interfaces?

> Yes.

Example:

```java
interface C extends A, B {
}
```

### Q7. Can a class extend a class and implement an interface?

> Yes.

Example:

```java
class Dog extends Animal implements Pet {
}
```

### Q8. What is the difference between `extends` and `implements`?

> `extends` is used for class inheritance or interface-to-interface inheritance, while `implements` is used when a class implements an interface.

### Q9. Can an interface have variables?

> Yes. Interface fields are implicitly `public`, `static`, and `final`.

### Q10. Can an interface have method implementations?

> Yes. Modern Java interfaces can have `default` and `static` methods with implementations.

---

# 🧠 Quick Revision

```text
Interface
    ↓
Contract
    ↓
Defines required behavior
    ↓
Class implements interface
    ↓
Class provides implementation
```

### Keywords

```text
interface
    ↓
Creates interface

implements
    ↓
Class implements interface

extends
    ↓
Class extends class
Interface extends interface
```

### ⭐ One-Line Memory Trick

```text
Interface = Contract
implements = Fulfills the Contract
```

---

# 📝 Practice Questions

### Basic

1. Create an interface `Animal` with:
   ```java
   void sound();
   ```

2. Create `Dog` and `Cat` classes that implement `Animal`.

3. Create two interfaces:
   ```text
   Flyable
   Swimmable
   ```
   and implement both in a `Duck` class.

4. Create a `Payment` interface with `pay()` and implement it using:
   ```text
   UPI
   CreditCard
   Cash
   ```

### Interview Practice

5. What is an interface?

6. Why do we use interfaces?

7. What is the difference between an interface and an abstract class?

8. Can a class implement multiple interfaces?

9. Can an interface extend another interface?

10. Can we create an object of an interface?

11. What is the difference between `extends` and `implements`?

12. What are default methods in interfaces?

---

# ⭐ Key Point

> **An interface defines a contract, and the implementing class provides the implementation.**

```text
Interface
    ↓
WHAT to do
    ↓
implements
    ↓
Class
    ↓
HOW to do it
```

Remember:

```text
extends    → Inheritance
implements → Interface
Interface  → Contract
```
