# 📘 Java OOPs – Polymorphism

> 💡 **In this lesson:** Learn how one method or reference can behave in different ways.

---

# 1️⃣ What is Polymorphism?

**Polymorphism** means **"many forms"**.

It allows the same method name or reference to perform different behaviors depending on the situation.

### 🧠 Simple Definition

> Polymorphism allows one interface or method name to have multiple forms of behavior.

### 🧠 Easy Memory Trick

```text
Poly = Many
Morphism = Forms

Polymorphism = Many Forms
```

---

# 2️⃣ Real-World Example

Consider a person.

The same person can have different roles:

```text
Person
  ↓
Student
Employee
Developer
Son
Friend
```

The person is the same, but the behavior can change depending on the role.

Similarly, in Java, the same method name can behave differently.

---

# 3️⃣ Types of Polymorphism in Java

Java mainly has two types:

```text
                 Polymorphism
                      |
             ┌────────┴────────┐
             ↓                 ↓
      Compile-Time        Runtime
      Polymorphism        Polymorphism
             ↓                 ↓
       Method Overloading  Method Overriding
```

### 1. Compile-Time Polymorphism

Achieved using:

```text
Method Overloading
```

### 2. Runtime Polymorphism

Achieved using:

```text
Method Overriding
```

---

# 4️⃣ Compile-Time Polymorphism

Compile-time polymorphism is achieved through **method overloading**.

Method overloading means having multiple methods with the same name but different parameters.

### Example

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    public static void main(String[] args) {

        Calculator c = new Calculator();

        System.out.println(c.add(10, 20));
        System.out.println(c.add(10, 20, 30));
    }
}
```

### 📤 Output

```text
30
60
```

Both methods have the same name:

```text
add()
```

But they accept different parameters.

The compiler decides which method to call.

Therefore:

```text
Method Overloading
        ↓
Compile-Time Polymorphism
```

---

# 5️⃣ Method Overloading

### Definition

> Method overloading means defining multiple methods with the same name but different parameter lists in the same class.

Example:

```java
class Calculator {

    void add(int a, int b) {
        System.out.println(a + b);
    }

    void add(double a, double b) {
        System.out.println(a + b);
    }
}
```

Here:

```text
add(int, int)
add(double, double)
```

are overloaded methods.

---

# 6️⃣ Runtime Polymorphism

Runtime polymorphism is achieved through **method overriding**.

It occurs when a child class provides its own implementation of a method already defined in the parent class.

### Example

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

---

# 7️⃣ Why Does This Happen?

Look at this:

```java
Animal a = new Dog();
```

Here:

```text
Animal → Reference type
Dog    → Actual object type
```

When we call:

```java
a.sound();
```

Java executes the `Dog` version of `sound()`.

So the output is:

```text
Dog barks
```

This decision happens at **runtime**.

Therefore:

```text
Method Overriding
        ↓
Runtime Polymorphism
```

---

# 8️⃣ Important Example

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

class Cat extends Animal {

    @Override
    void sound() {
        System.out.println("Cat meows");
    }

public static void main(String[] args) {

        Animal a1 = new Dog();
        Animal a2 = new Cat();

        a1.sound();
        a2.sound();
    }
}
```

### 📤 Output

```text
Dog barks
Cat meows
```

Same method:

```java
sound()
```

Different behavior:

```text
Dog → barks
Cat → meows
```

This is polymorphism.

---

# 9️⃣ Compile-Time vs Runtime Polymorphism

| Compile-Time | Runtime |
|---|---|
| Method Overloading | Method Overriding |
| Same class usually | Parent-child relationship |
| Different parameters | Same method signature |
| Decided by compiler | Decided at runtime |
| Static binding | Dynamic binding |

### 🧠 Easy Memory Trick

```text
Overloading  → Compile Time
Overriding   → Runtime
```

---

# 🔟 Method Overloading Example

```java
class Printer {

    void print(int value) {
        System.out.println("Integer: " + value);
    }

    void print(String value) {
        System.out.println("String: " + value);
    }

    public static void main(String[] args) {

        Printer p = new Printer();

        p.print(10);
        p.print("Hello");
    }
}
```

### 📤 Output

```text
Integer: 10
String: Hello
```

The compiler chooses the appropriate method based on the arguments.

---

# 1️⃣1️⃣ Method Overriding Example

```java
class Vehicle {

    void start() {
        System.out.println("Vehicle starts");
    }
}

class Car extends Vehicle {

    @Override
    void start() {
        System.out.println("Car starts with key");
    }

    public static void main(String[] args) {

        Vehicle v = new Car();

        v.start();
    }
}
```

### 📤 Output

```text
Car starts with key
```

---

# 1️⃣2️⃣ Upcasting

Runtime polymorphism commonly uses **upcasting**.

```java
Animal a = new Dog();
```

Here:

```text
Dog object
     ↓
Animal reference
```

This is called **upcasting**.

### Example

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

Animal a = new Dog();

a.sound();
```

Output:

```text
Dog barks
```

---

# 1️⃣3️⃣ Why is Polymorphism Useful?

### 🔄 1. Flexible Code

We can use a parent reference to work with different child objects.

```java
Animal a;

a = new Dog();
a = new Cat();
```

---

### ♻️ 2. Code Reusability

Common behavior can be defined in the parent.

---

### 🔧 3. Easy Maintenance

New child classes can be added without changing much existing code.

---

### 🎯 4. Supports Dynamic Behavior

The actual object's method can be selected at runtime.

---

# 1️⃣4️⃣ Real-World Example

Suppose we have:

```text
Payment
   |
   ├── UPI
   ├── CreditCard
   └── Cash
```

Each payment method can have:

```java
pay()
```

But the implementation can be different.

```java
Payment p = new UPI();
p.pay();

p = new CreditCard();
p.pay();
```

The same:

```text
pay()
```

can behave differently depending on the object.

---

# 1️⃣5️⃣ Important Interview Questions ⭐

### Q1. What is polymorphism?

> Polymorphism means one name or interface can have multiple forms of behavior.

### Q2. What are the types of polymorphism in Java?

> Compile-time polymorphism and runtime polymorphism.

### Q3. How is compile-time polymorphism achieved?

> Through method overloading.

### Q4. How is runtime polymorphism achieved?

> Through method overriding.

### Q5. What is method overloading?

> Multiple methods with the same name but different parameter lists.

### Q6. What is method overriding?

> When a child class provides its own implementation of a method inherited from the parent class.

### Q7. Which polymorphism is called dynamic polymorphism?

> Runtime polymorphism.

### Q8. What is upcasting?

> Assigning a child class object to a parent class reference.

Example:

```java
Animal a = new Dog();
```

---

# 🧠 Quick Revision

```text
                 POLYMORPHISM
                       |
              ┌────────┴────────┐
              ↓                 ↓
        Compile-Time        Runtime
              ↓                 ↓
        Overloading        Overriding
              ↓                 ↓
       Same name +       Parent-child
       different args    same method
```

### ⭐ One-Line Memory Trick

```text
Overloading → Same name, different parameters
Overriding  → Same method, different implementation
```

---

# 📝 Practice Questions

### Basic

1. Create a `Calculator` class with overloaded `add()` methods:
   ```text
   add(int, int)
   add(int, int, int)
   ```

2. Create a `Printer` class with overloaded `print()` methods for:
   ```text
   int
   String
   double
   ```

3. Create:
   ```text
   Animal
      ↓
     Dog
      ↓
   Override sound()
   ```

4. Create `Animal`, `Dog`, and `Cat` classes and demonstrate runtime polymorphism.

### Interview Practice

5. What is polymorphism?

6. What is the difference between overloading and overriding?

7. What is compile-time polymorphism?

8. What is runtime polymorphism?

9. What is upcasting?

10. Why is runtime polymorphism useful?

---

# ⭐ Key Point

> **Polymorphism means "many forms". In Java, it is mainly achieved through method overloading and method overriding.**

```text
Overloading
     ↓
Compile Time
     ↓
Same method name
Different parameters
```

```text
Overriding
     ↓
Runtime
     ↓
Parent + Child
Same method
Different implementation
```
