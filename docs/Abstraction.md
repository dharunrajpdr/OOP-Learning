# 📘 Java OOPs – Abstraction

> 💡 **In this lesson:** Learn how Java hides implementation details and exposes only the necessary functionality.

---

# 1️⃣ What is Abstraction?

**Abstraction** means hiding unnecessary implementation details and showing only the essential features to the user.

### 🧠 Simple Definition

> Abstraction is the process of hiding implementation details and showing only the required functionality.

---

# 2️⃣ Real-World Example 🚗

When you drive a car:

```text
You use:
    → Start
    → Accelerate
    → Brake
    → Steering

You don't need to know:
    → How the engine works internally
    → How fuel is injected
    → How the transmission works
```

You only interact with the necessary features.

That is **abstraction**.

### 🧠 Easy Memory Trick

```text
Abstraction = Hide implementation + Show functionality
```

---

# 3️⃣ Why Do We Need Abstraction?

Abstraction helps us:

- Hide complex implementation
- Show only important functionality
- Reduce complexity
- Improve security
- Make code easier to use
- Separate what an object does from how it does it

---

# 4️⃣ How is Abstraction Achieved in Java?

Java mainly provides two ways:

```text
1. Abstract Class
2. Interface
```

```text
             Abstraction
                  |
          ┌───────┴───────┐
          ↓               ↓
   Abstract Class      Interface
```

We will study both separately.

---

# 5️⃣ Abstract Method

An **abstract method** is a method that has a declaration but no implementation.

### Syntax

```java
abstract void sound();
```

Notice:

```text
No method body
No { }
```

The child class must provide the implementation.

---

# 6️⃣ Abstract Class

A class declared using the `abstract` keyword is called an **abstract class**.

### Syntax

```java
abstract class Animal {

    abstract void sound();
}
```

Here:

```text
abstract class → Abstract class
abstract void sound() → Abstract method
```

---

# 7️⃣ Simple Example

```java
abstract class Animal {

    abstract void sound();
}

class Dog extends Animal {

    void sound() {
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

# 8️⃣ How Does It Work?

The parent class says:

```java
abstract void sound();
```

It tells the child:

> "Every Animal must have a sound(), but I am not defining how it works."

The child class decides the implementation:

```java
void sound() {
    System.out.println("Dog barks");
}
```

So:

```text
Animal
   ↓
What to do?
sound()
   ↓
Dog
   ↓
How to do?
Dog barks
```

---

# 9️⃣ Abstraction Example with Payment

Consider a payment system.

Different payment methods have different implementations.

```text
Payment
   |
   ├── UPI
   ├── Credit Card
   └── Net Banking
```

All payments need:

```text
pay()
```

But the implementation can be different.

### Example

```java
abstract class Payment {

    abstract void pay();
}

class UPI extends Payment {

    void pay() {
        System.out.println("Payment using UPI");
    }
}

class CreditCard extends Payment {

    void pay() {
        System.out.println("Payment using Credit Card");
    }
}
```

Usage:

```java
UPI u = new UPI();
u.pay();

CreditCard c = new CreditCard();
c.pay();
```

### 📤 Output

```text
Payment using UPI
Payment using Credit Card
```

The parent defines **what should be done**.

The child defines **how it should be done**.

---

# 🔟 "What" vs "How"

This is one of the easiest ways to understand abstraction.

```text
Abstraction
     ↓
WHAT to do
```

Implementation:

```text
Child Class
     ↓
HOW to do
```

Example:

```java
abstract class Vehicle {

    abstract void start();   // WHAT
}
```

```java
class Car extends Vehicle {

    void start() {            // HOW
        System.out.println("Car starts");
    }
}
```

### 🧠 Memory Trick

```text
Abstraction → WHAT
Implementation → HOW
```

---

# 1️⃣1️⃣ Can an Abstract Class Have Normal Methods?

Yes. ⭐

An abstract class can contain:

```text
Abstract methods
Concrete methods
Variables
Constructors
```

Example:

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Animal eats");
    }
}
```

Child class:

```java
class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }
}
```

Now `Dog` gets:

```text
sound() → Child implements it
eat()   → Already implemented
```

---

# 1️⃣2️⃣ Can We Create an Object of an Abstract Class?

❌ No.

Example:

```java
abstract class Animal {

    abstract void sound();
}
```

We cannot do:

```java
Animal a = new Animal();
```

This gives a compilation error.

But we can create a reference:

```java
Animal a = new Dog();
```

This is allowed.

Here:

```text
Animal → Reference type
Dog    → Actual object
```

---

# 1️⃣3️⃣ Abstract Class Reference

Example:

```java
abstract class Animal {

    abstract void sound();
}

class Dog extends Animal {

    void sound() {
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

This also demonstrates **runtime polymorphism**.

---

# 1️⃣4️⃣ Abstraction vs Encapsulation

These two concepts are often confused.

| Abstraction | Encapsulation |
|---|---|
| Hides implementation | Hides/protects data |
| Focuses on what an object does | Focuses on controlling access |
| Achieved using abstract classes/interfaces | Commonly achieved using private variables + methods |
| Reduces complexity | Protects data |

### 🧠 Easy Memory Trick

```text
Abstraction  → Hide HOW
Encapsulation → Hide/Protect DATA
```

Example:

```text
Abstraction:
"How does the car engine work?"
→ Hidden

Encapsulation:
"Can I directly change the car's internal data?"
→ Controlled
```

---

# 1️⃣5️⃣ Abstraction vs Inheritance

| Abstraction | Inheritance |
|---|---|
| Hides implementation details | Reuses existing code |
| Focuses on design | Focuses on parent-child relationship |
| Uses abstract classes/interfaces | Uses `extends` for classes |
| Defines required behavior | Provides inherited behavior |

They are often used together.

Example:

```java
abstract class Animal {
    abstract void sound();
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```

Here:

```text
Abstraction → abstract sound()
Inheritance → Dog extends Animal
```

---

# 1️⃣6️⃣ Advantages of Abstraction

### 🎯 1. Reduces Complexity

Users don't need to understand internal implementation.

### 🔒 2. Hides Implementation

Internal details can remain hidden.

### 🔧 3. Easy Maintenance

Implementation can change without changing how users interact with it.

### ♻️ 4. Supports Reusability

Common design can be defined at a higher level.

### 🔄 5. Supports Polymorphism

Abstract references can refer to different child objects.

---

# 1️⃣7️⃣ Real-World Example

Think about a **remote control** 📺.

You press:

```text
Power ON
Volume +
Volume -
Channel +
```

You don't need to know how the TV internally processes those commands.

```text
Remote
  ↓
Exposes functionality
  ↓
Internal implementation hidden
```

This is the basic idea of abstraction.

---

# 1️⃣8️⃣ Important Interview Questions ⭐

### Q1. What is abstraction?

> Abstraction is the process of hiding implementation details and exposing only the necessary functionality.

### Q2. How is abstraction achieved in Java?

> Mainly using abstract classes and interfaces.

### Q3. What is an abstract method?

> An abstract method is a method declared without an implementation/body.

Example:

```java
abstract void sound();
```

### Q4. Can we create an object of an abstract class?

> No, we cannot directly instantiate an abstract class.

### Q5. Can an abstract class have normal methods?

> Yes. An abstract class can have both abstract and concrete methods.

### Q6. Can an abstract class have a constructor?

> Yes, an abstract class can have a constructor.

### Q7. What is the main purpose of abstraction?

> To hide implementation details and expose only essential functionality.

### Q8. Difference between abstraction and encapsulation?

> Abstraction hides implementation complexity, while encapsulation controls access to data.

---

# 🧠 Quick Revision

```text
Abstraction
     ↓
Hide unnecessary implementation
     ↓
Show essential functionality
     ↓
Achieved using
     ↓
Abstract Class + Interface
```

### ⭐ Important Rules

```text
Abstract class
    ↓
Cannot be directly instantiated

Abstract method
    ↓
No method body

Child class
    ↓
Must implement inherited abstract methods
```

### ⭐ One-Line Memory Trick

```text
Abstraction = WHAT to do, not HOW to do it
```

---

# 📝 Practice Questions

### Basic

1. Create an abstract class `Animal` with an abstract method `sound()`.

2. Create `Dog` and `Cat` classes that extend `Animal`.

3. Implement different `sound()` methods for `Dog` and `Cat`.

4. Create an abstract `Vehicle` class with:
   ```java
   abstract void start();
   ```

5. Create `Car` and `Bike` classes and implement `start()` differently.

### Interview Practice

6. What is abstraction?

7. How is abstraction achieved in Java?

8. What is an abstract method?

9. Can we create an object of an abstract class?

10. Can an abstract class have normal methods?

11. Can an abstract class have a constructor?

12. What is the difference between abstraction and encapsulation?

---

# ⭐ Key Point

> **Abstraction hides implementation details and shows only the required functionality.**

```text
              ABSTRACTION
                   ↓
        ┌──────────┴──────────┐
        ↓                     ↓
 Abstract Class          Interface
        ↓
     "WHAT"
        ↓
 Child Class
     "HOW"
```

Remember:

```text
Abstraction  → Hide HOW
Encapsulation → Protect DATA
Inheritance   → Reuse CODE
Polymorphism  → MANY FORMS
```
