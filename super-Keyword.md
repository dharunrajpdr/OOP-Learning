# 📘 Java OOPs – `super` Keyword 🔼

# 1️⃣ What is `super`?

`super` is a keyword used to refer to the **immediate parent class object/member**.

### Simple Definition

> **`super` is used to access members of the immediate parent class.**

It is mainly used in inheritance.

Example:

```java
class Animal {

    String name = "Animal";
}

class Dog extends Animal {

    String name = "Dog";

    void display() {
        System.out.println(name);
        System.out.println(super.name);
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        d.display();
    }
}
```

### Output

```text
Dog
Animal
```

Here:

```java
name
```

refers to the child class variable.

```java
super.name
```

refers to the parent class variable.

---

# 2️⃣ Why Do We Use `super`?

The most common uses of `super` are:

1. Access parent class variable
2. Call parent class method
3. Call parent class constructor

Remember:

```text
super.variable
super.method()
super()
```

---

# 3️⃣ `super` with Variables

Suppose both parent and child have a variable with the same name.

```java
class Animal {

    String color = "White";
}

class Dog extends Animal {

    String color = "Black";

    void display() {

        System.out.println(color);
        System.out.println(super.color);
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        d.display();
    }
}
```

### Output

```text
Black
White
```

### Explanation

```java
color
```

→ Child class variable

```java
super.color
```

→ Parent class variable

---

# 4️⃣ `super` with Methods

`super` can be used to call a method from the parent class.

Example:

```java
class Animal {

    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }

    void display() {

        sound();
        super.sound();
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        d.display();
    }
}
```

### Output

```text
Dog barks
Animal makes sound
```

### Explanation

```java
sound();
```

calls the child version.

```java
super.sound();
```

calls the parent version.

---

# 5️⃣ `super()` – Calling Parent Constructor

`super()` is used to call the constructor of the immediate parent class.

Example:

```java
class Animal {

    Animal() {
        System.out.println("Animal constructor");
    }
}

class Dog extends Animal {

    Dog() {
        super();
        System.out.println("Dog constructor");
    }

    public static void main(String[] args) {

        Dog d = new Dog();
    }
}
```

### Output

```text
Animal constructor
Dog constructor
```

### Flow

```text
new Dog()
    ↓
super()
    ↓
Animal constructor
    ↓
Dog constructor
```

---

# 6️⃣ `super()` Must Be the First Statement

Just like `this()`, `super()` must be the **first statement** inside a constructor.

Correct:

```java
Dog() {
    super();
    System.out.println("Dog");
}
```

Incorrect:

```java
Dog() {
    System.out.println("Dog");
    super();   // ❌ Error
}
```

---

# 7️⃣ `super()` Is Automatically Added

If you don't explicitly write `super()` in a child constructor, Java implicitly adds it **when the parent has an accessible no-argument constructor**.

Example:

```java
class Animal {

    Animal() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {

    Dog() {
        System.out.println("Dog");
    }
}
```

Conceptually, Java treats the child constructor like:

```java
Dog() {
    super();
    System.out.println("Dog");
}
```

### Output

```text
Animal
Dog
```

---

# 8️⃣ Calling a Parameterized Parent Constructor

Suppose the parent has a parameterized constructor.

```java
class Animal {

    String name;

    Animal(String name) {
        this.name = name;
    }
}

class Dog extends Animal {

    Dog(String name) {
        super(name);
    }

    void display() {
        System.out.println(name);
    }

    public static void main(String[] args) {

        Dog d = new Dog("Tommy");

        d.display();
    }
}
```

### Output

```text
Tommy
```

Here:

```java
super(name);
```

calls:

```java
Animal(String name)
```

---

# 9️⃣ Important Constructor Rule ⚠️

Consider:

```java
class Animal {

    Animal(String name) {
        System.out.println(name);
    }
}

class Dog extends Animal {

    Dog() {
        System.out.println("Dog");
    }
}
```

This causes a compilation error.

### Why?

Java tries to insert:

```java
super();
```

But the parent class has:

```java
Animal(String name)
```

and does not have an accessible no-argument constructor.

So we must explicitly call:

```java
Dog() {
    super("Animal");
    System.out.println("Dog");
}
```

---

# 🔟 `super` with Method Overriding

`super` is very useful when a child overrides a parent method but still wants to use the parent's implementation.

```java
class Animal {

    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {

        super.sound();

        System.out.println("Dog barks");
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        d.sound();
    }
}
```

### Output

```text
Animal sound
Dog barks
```

This allows the child to **extend the parent's behavior** instead of completely replacing it.

---

# 1️⃣1️⃣ `super` vs `this`

| `this` | `super` |
|---|---|
| Refers to current object/current class members | Refers to immediate parent class members |
| Used for current class | Used for parent class |
| `this.name` | `super.name` |
| `this.display()` | `super.display()` |
| `this()` calls current class constructor | `super()` calls parent class constructor |

### Easy Example

```java
this.name
```

→ Current class

```java
super.name
```

→ Parent class

```java
this()
```

→ Current class constructor

```java
super()
```

→ Parent class constructor

---

# 1️⃣2️⃣ `super` vs `this` – Memory Trick 🧠

```text
this
 ↓
ME
 ↓
Current Class/Object
```

```text
super
 ↓
PARENT
 ↓
Parent Class
```

Think:

```text
this = Me
super = My Parent
```

---

# 1️⃣3️⃣ Can `super` Access Private Members?

❌ No.

A child class cannot directly access a parent's private variable or method using `super`.

Example:

```java
class Animal {

    private int age = 10;
}

class Dog extends Animal {

    void display() {
        System.out.println(super.age); // ❌ Error
    }
}
```

Private members are accessible only within their declaring class.

---

# 1️⃣4️⃣ Can `super` Access Static Members?

Static members belong to the class, so they can be accessed through the parent class name.

Although Java may allow some static member access through `super`, using the class name is clearer:

```java
ParentClass.staticMember
```

rather than relying on:

```java
super.staticMember
```

For interviews, remember that `super` is primarily used for accessing the **immediate parent's accessible instance members and constructors**.

---

# 1️⃣5️⃣ Three Main Uses of `super`

### 1. Parent variable

```java
super.name;
```

### 2. Parent method

```java
super.display();
```

### 3. Parent constructor

```java
super();
```

### Memory Trick

```text
super.variable
       ↓
Parent variable

super.method()
       ↓
Parent method

super()
       ↓
Parent constructor
```

---

# 🎯 Interview One-Liners

### What is `super`?

> `super` is a Java keyword used to access members of the immediate parent class.

### What are the main uses of `super`?

> It is used to access parent variables, call parent methods, and call the parent constructor.

### What is `super()`?

> `super()` calls the constructor of the immediate parent class.

### Where must `super()` be placed?

> `super()` must be the first statement inside a constructor.

### Is `super()` automatically called?

> Yes, Java implicitly inserts `super()` in a child constructor when an accessible no-argument parent constructor exists and no explicit constructor call is written.

### Can `super` access private members?

> No, private members of the parent class cannot be directly accessed by the child class.

### What is the difference between `this` and `super`?

> `this` refers to the current class/object, while `super` refers to the immediate parent class.

---

# 📝 Practice Questions

### Q1. What does `super` refer to?

A. Current class  
B. Child class  
C. Immediate parent class  
D. Static class

**Answer:** C

---

### Q2. What does `super()` call?

A. Current method  
B. Parent constructor  
C. Child constructor  
D. Parent variable

**Answer:** B

---

### Q3. Which statement accesses the parent class variable?

A. `this.name`  
B. `parent.name`  
C. `super.name`  
D. `name.super`

**Answer:** C

---

### Q4. Can `super()` appear after another statement in a constructor?

A. Yes  
B. No

**Answer:** B

---

### Q5. What is the output?

```java
class A {

    void show() {
        System.out.println("A");
    }
}

class B extends A {

    void show() {
        System.out.println("B");
        super.show();
    }

    public static void main(String[] args) {

        B obj = new B();

        obj.show();
    }
}
```

**Output:**

```text
B
A
```

---

# ⚡ Quick Revision

```text
super
  ↓
Immediate Parent Class

super.variable
  ↓
Parent variable

super.method()
  ↓
Parent method

super()
  ↓
Parent constructor

super()
  ↓
Must be first statement in constructor
```

## ⭐ Key Point

> **`this` means current object/class, while `super` is used to access the immediate parent's accessible members and constructor.**
