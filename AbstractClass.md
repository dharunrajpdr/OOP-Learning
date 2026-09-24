# 📘 Java OOPs – Abstract Class

> 💡 **In this lesson:** Learn what an abstract class is, how to use abstract and concrete methods, constructors, variables, and inheritance with abstract classes.

---

# 1️⃣ What is an Abstract Class?

An **abstract class** is a class declared using the `abstract` keyword.

It can contain:

- Abstract methods
- Concrete methods
- Variables
- Constructors
- Static methods
- Final methods

### 🧠 Simple Definition

> An abstract class is a class that cannot be directly instantiated and is used as a base class for other classes.

### Syntax

```java
abstract class ClassName {

    // variables

    // abstract methods

    // concrete methods
}
```

---

# 2️⃣ Simple Example

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Animal eats");
    }
}
```

Here:

```text
Animal → Abstract class
sound() → Abstract method
eat() → Concrete method
```

A child class can extend it:

```java
class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }
}
```

---

# 3️⃣ Why Do We Use Abstract Classes?

Abstract classes are useful when we want to:

- Provide common functionality
- Force child classes to implement specific methods
- Share variables and methods
- Create a common base class
- Achieve partial abstraction

### 🧠 Memory Trick

```text
Abstract Class
      ↓
Common Code + Required Methods
```

---

# 4️⃣ Abstract Method

An abstract method is a method declared without a body.

### Syntax

```java
abstract void sound();
```

Notice:

```text
No { }
No implementation
```

The child class must provide the implementation.

Example:

```java
abstract class Animal {

    abstract void sound();
}
```

Child:

```java
class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }
}
```

---

# 5️⃣ Concrete Method

A **concrete method** is a normal method that contains an implementation.

Example:

```java
void eat() {
    System.out.println("Animal eats");
}
```

An abstract class can contain both:

```text
Abstract method
       +
Concrete method
```

---

# 6️⃣ Complete Example

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        d.sound();
        d.eat();
    }
}
```

### 📤 Output

```text
Dog barks
Animal eats
```

Here:

```text
sound() → Implemented by Dog
eat()   → Inherited from Animal
```

---

# 7️⃣ Can We Create an Object of an Abstract Class?

❌ No.

Example:

```java
abstract class Animal {
}
```

This is not allowed:

```java
Animal a = new Animal();   // ❌ Error
```

Because an abstract class is incomplete and is designed to be extended.

---

# 8️⃣ Can We Create a Reference of an Abstract Class?

✅ Yes.

Example:

```java
Animal a = new Dog();
```

Here:

```text
Animal → Reference
Dog    → Object
```

This is commonly used for **runtime polymorphism**.

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

---

# 9️⃣ Abstract Class Can Have Variables

Yes. ⭐

Example:

```java
abstract class Animal {

    String name = "Animal";

    abstract void sound();
}
```

Child class:

```java
class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        System.out.println(d.name);
        d.sound();
    }
}
```

### 📤 Output

```text
Animal
Dog barks
```

---

# 🔟 Abstract Class Can Have Constructors

Yes. ⭐⭐⭐

An abstract class can have a constructor.

Example:

```java
abstract class Animal {

    Animal() {
        System.out.println("Animal constructor");
    }

    abstract void sound();
}

class Dog extends Animal {

    Dog() {
        System.out.println("Dog constructor");
    }

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
Animal constructor
Dog constructor
Dog barks
```

### Why does the parent constructor execute?

When a child object is created:

```java
new Dog();
```

the parent class constructor runs first.

```text
Dog object creation
       ↓
Animal constructor
       ↓
Dog constructor
```

---

# 1️⃣1️⃣ Abstract Class Can Have Static Methods

Yes.

Example:

```java
abstract class Animal {

    static void show() {
        System.out.println("Static method");
    }
}
```

Call it using:

```java
Animal.show();
```

---

# 1️⃣2️⃣ Abstract Class Can Have Final Methods

Yes.

Example:

```java
abstract class Animal {

    final void eat() {
        System.out.println("Animal eats");
    }
}
```

A child class can use the method but cannot override it.

```java
class Dog extends Animal {
}
```

---

# 1️⃣3️⃣ Can an Abstract Class Have No Abstract Methods?

Yes. ⭐

An abstract class does not necessarily need to contain an abstract method.

Example:

```java
abstract class Animal {

    void eat() {
        System.out.println("Animal eats");
    }
}
```

This is valid.

But because the class is declared `abstract`, we still cannot directly create:

```java
Animal a = new Animal();   // ❌
```

---

# 1️⃣4️⃣ Abstract Class with Multiple Child Classes

Example:

```text
             Animal
            /      \
           /        \
         Dog        Cat
```

Code:

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {

    void sound() {
        System.out.println("Cat meows");
    }
}
```

Usage:

```java
Animal a1 = new Dog();
Animal a2 = new Cat();

a1.sound();
a2.sound();
```

### 📤 Output

```text
Dog barks
Cat meows
```

This demonstrates:

```text
Abstract Class
      +
Inheritance
      +
Runtime Polymorphism
```

---

# 1️⃣5️⃣ Abstract Class vs Normal Class

| Abstract Class | Normal Class |
|---|---|
| Declared using `abstract` | No `abstract` keyword |
| Cannot be directly instantiated | Can be instantiated |
| Can contain abstract methods | Cannot contain abstract methods |
| Can contain concrete methods | Can contain concrete methods |
| Can have constructors | Can have constructors |
| Can have variables | Can have variables |

### Example

```java
abstract class Animal {
}
```

Cannot do:

```java
new Animal();   // ❌
```

Normal class:

```java
class Dog {
}
```

Can do:

```java
new Dog();      // ✅
```

---

# 1️⃣6️⃣ Abstract Class vs Interface

Very important interview question. ⭐⭐⭐

| Abstract Class | Interface |
|---|---|
| Uses `abstract class` | Uses `interface` |
| Class extends it using `extends` | Class implements it using `implements` |
| Can have constructors | Cannot have constructors |
| Can have instance variables | Interface fields are `public static final` by default |
| Can have abstract + concrete methods | Can have abstract, default, static methods |
| A class can extend only one class | A class can implement multiple interfaces |
| Useful for shared base functionality | Useful for contracts/capabilities |

### 🧠 Easy Memory Trick

```text
Abstract Class
      ↓
Common Base + Shared Code

Interface
      ↓
Contract + Capability
```

---

# 1️⃣7️⃣ When Should We Use an Abstract Class?

Use an abstract class when related classes share:

```text
Common variables
Common methods
Common constructor logic
```

and also need some methods to be implemented differently.

### Example

```text
             Employee
             /      \
            /        \
     Developer      Tester
```

All employees may have:

```text
name
salary
login()
logout()
```

But:

```text
Developer → writeCode()
Tester    → testApplication()
```

An abstract class can provide the common functionality while requiring subclasses to implement specific behavior.

---

# 1️⃣8️⃣ Important Interview Questions ⭐

### Q1. What is an abstract class?

> An abstract class is a class declared using the `abstract` keyword that cannot be directly instantiated and can contain abstract as well as concrete methods.

### Q2. Can we create an object of an abstract class?

> No.

### Q3. Can an abstract class have a constructor?

> Yes.

### Q4. Can an abstract class have normal methods?

> Yes.

### Q5. Can an abstract class have variables?

> Yes.

### Q6. Can an abstract class have no abstract methods?

> Yes.

### Q7. Can an abstract class have static methods?

> Yes.

### Q8. Can an abstract class have final methods?

> Yes.

### Q9. Can an abstract class be final?

> No. A `final` class cannot be inherited, while an abstract class is designed to be inherited.

### Q10. Can we have an abstract constructor?

> No. Constructors cannot be abstract.

---

# 🧠 Quick Revision

```text
Abstract Class
      ↓
Cannot create object directly
      ↓
Can contain:
      ↓
Abstract Methods
Concrete Methods
Variables
Constructors
Static Methods
Final Methods
```

### ⭐ Important Rules

```text
abstract class → Cannot instantiate

abstract method → No body

child class → Must implement inherited abstract methods
```

### ⭐ One-Line Memory Trick

```text
Abstract Class = Common Code + Incomplete Methods
```

---

# 📝 Practice Questions

### Basic

1. Create an abstract class `Animal` with:
   ```java
   abstract void sound();
   ```

2. Add a concrete method:
   ```java
   void eat()
   ```

3. Create `Dog` and `Cat` classes extending `Animal`.

4. Create an abstract `Vehicle` class with:
   ```java
   abstract void start();
   void stop()
   ```

5. Create `Car` and `Bike` classes extending `Vehicle`.

### Interview Practice

6. What is an abstract class?

7. Can we create an object of an abstract class?

8. Can an abstract class have a constructor?

9. Can an abstract class have normal methods?

10. Can an abstract class have no abstract methods?

11. Difference between abstract class and interface?

12. Why can't an abstract class be `final`?

---

# ⭐ Key Point

> **An abstract class provides a common base for related classes and can contain both complete and incomplete methods.**

```text
Abstract Class
      ↓
   extends
      ↓
  Child Class
      ↓
Implements abstract methods
```

Remember:

```text
abstract class → Cannot instantiate
abstract method → No body
concrete method → Has body
extends → Inherit abstract class
```
