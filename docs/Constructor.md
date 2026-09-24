# 📘 Java OOPs – Constructor 🏗️

# 1️⃣ What is a Constructor?

A **constructor** is a special block in Java that is used to **initialize an object**.

### Simple Definition

> **Constructor = Special block used to initialize an object.**

A constructor is automatically called when we create an object using `new`.

### Example

```java
class Student {

    String name;
    int age;

    Student() {
        name = "Dharun";
        age = 22;
    }
}
```

Creating the object:

```java
Student s = new Student();
```

The constructor `Student()` is automatically called.

---

# 2️⃣ Why Do We Need a Constructor?

Suppose we create a Student object:

```java
Student s = new Student();
```

We may want the object to start with some initial values.

Instead of:

```java
s.name = "Dharun";
s.age = 22;
```

We can initialize them directly using a constructor:

```java
Student s = new Student("Dharun", 22);
```

This makes object creation easier and cleaner.

---

# 3️⃣ Constructor Syntax

```java
class ClassName {

    ClassName() {
        // initialization
    }
}
```

### Important

The constructor name **must be the same as the class name**.

Example:

```java
class Student {

    Student() {
        System.out.println("Constructor called");
    }
}
```

---

# 4️⃣ Important Properties of a Constructor

A constructor:

1. Has the **same name as the class**
2. Does **not have a return type**
3. Is automatically called when an object is created
4. Is mainly used for object initialization
5. Can be overloaded
6. Cannot be inherited
7. Can have access modifiers like `public`, `private`, etc.

---

# 5️⃣ Simple Constructor Example

```java
class Student {

    String name;
    int age;

    Student() {
        name = "Dharun";
        age = 22;
    }

    void display() {
        System.out.println(name);
        System.out.println(age);
    }

    public static void main(String[] args) {

        Student s = new Student();

        s.display();
    }
}
```

### Output

```text
Dharun
22
```

### Flow

```text
new Student()
      ↓
Constructor called
      ↓
name = "Dharun"
age = 22
      ↓
Object initialized
```

---

# 6️⃣ Types of Constructors

For interview purposes, commonly discuss:

### 1. No-Argument Constructor

Constructor with no parameters.

```java
Student() {
    System.out.println("Hello");
}
```

### 2. Parameterized Constructor

Constructor that accepts parameters.

```java
Student(String name, int age) {
    this.name = name;
    this.age = age;
}
```

### 3. Default Constructor

A constructor automatically provided by the compiler **only when you do not declare any constructor**.

Example:

```java
class Student {

    String name;
}
```

Here, Java provides a default constructor.

Conceptually:

```java
Student() {
}
```

---

# 7️⃣ No-Argument Constructor

A no-argument constructor does not receive any parameters.

```java
class Student {

    String name;

    Student() {
        name = "Dharun";
    }

    public static void main(String[] args) {

        Student s = new Student();

        System.out.println(s.name);
    }
}
```

### Output

```text
Dharun
```

---

# 8️⃣ Parameterized Constructor

A parameterized constructor receives values during object creation.

```java
class Student {

    String name;
    int age;

    Student(String name, int age) {

        this.name = name;
        this.age = age;
    }

    void display() {
        System.out.println(name);
        System.out.println(age);
    }

    public static void main(String[] args) {

        Student s1 = new Student("Dharun", 22);
        Student s2 = new Student("Rahul", 21);

        s1.display();
        s2.display();
    }
}
```

### Output

```text
Dharun
22
Rahul
21
```

Here:

```java
new Student("Dharun", 22);
```

passes values directly to the constructor.

---

# 9️⃣ Why Do We Use `this` in Constructor?

Consider:

```java
class Student {

    String name;
    int age;

    Student(String name, int age) {

        this.name = name;
        this.age = age;
    }
}
```

Here we have two `name`s:

```java
String name;       // instance variable

Student(String name)  // parameter
```

`this.name` means:

> Current object's `name`

So:

```java
this.name = name;
```

means:

```text
object's name = parameter name
```

---

# 🔟 Constructor Overloading

Just like method overloading, we can have multiple constructors with different parameter lists.

Example:

```java
class Student {

    String name;
    int age;

    Student() {
        name = "Unknown";
        age = 0;
    }

    Student(String name) {
        this.name = name;
        age = 0;
    }

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Now we can create objects in different ways:

```java
Student s1 = new Student();

Student s2 = new Student("Dharun");

Student s3 = new Student("Dharun", 22);
```

This is called:

> **Constructor Overloading**

---

# 1️⃣1️⃣ Constructor vs Method

| Constructor | Method |
|---|---|
| Initializes an object | Performs an operation |
| Same name as class | Can have any valid name |
| No return type | Can have a return type |
| Automatically called during object creation | Usually called explicitly |
| Cannot be inherited | Methods can be inherited |
| Can be overloaded | Can be overloaded |

### Example

```java
class Student {

    Student() {
        System.out.println("Constructor");
    }

    void display() {
        System.out.println("Method");
    }
}
```

```java
Student s = new Student(); // Constructor automatically called

s.display();              // Method explicitly called
```

---

# 1️⃣2️⃣ Can a Constructor Have a Return Type?

❌ No.

This is a constructor:

```java
Student() {
}
```

This is a method:

```java
void Student() {
}
```

Because `void` is present, it is **not a constructor**.

---

# 1️⃣3️⃣ Can a Constructor Be Private?

Yes.

Example:

```java
class Student {

    private Student() {
        System.out.println("Constructor");
    }
}
```

A private constructor prevents other classes from directly creating objects using `new`.

This concept is commonly used in patterns such as the **Singleton pattern**.

---

# 1️⃣4️⃣ Constructor and Inheritance

Constructors are **not inherited** by child classes.

But when a child object is created, the parent constructor is called first.

Example:

```java
class Animal {

    Animal() {
        System.out.println("Animal Constructor");
    }
}

class Dog extends Animal {

    Dog() {
        System.out.println("Dog Constructor");
    }
}
```

```java
Dog d = new Dog();
```

### Output

```text
Animal Constructor
Dog Constructor
```

### Flow

```text
new Dog()
   ↓
Animal constructor
   ↓
Dog constructor
```

This happens because the child constructor implicitly calls the parent constructor using `super()` when applicable.

---

# 1️⃣5️⃣ Default Constructor — Important Interview Point ⚠️

If you don't write **any constructor**:

```java
class Student {

    String name;
}
```

Java provides a default constructor.

But if you write your own constructor:

```java
class Student {

    Student(String name) {
        // ...
    }
}
```

Java **does not automatically provide** a no-argument constructor.

Therefore this causes an error:

```java
Student s = new Student();
```

unless you explicitly define:

```java
Student() {
}
```

---

# 🧠 Easy Memory Trick

```text
Constructor
     ↓
Initialize Object
     ↓
Same name as class
     ↓
No return type
     ↓
Automatically called
     ↓
Can be overloaded
```

### Remember:

> **Constructor = Object Initialization**

---

# 🎯 Interview One-Liners

### What is a constructor?

> A constructor is a special block in Java used to initialize an object, and it is automatically called when an object is created.

### Does a constructor have a return type?

> No, a constructor does not have a return type, not even `void`.

### Can constructors be overloaded?

> Yes, constructors can be overloaded by having different parameter lists.

### Are constructors inherited?

> No, constructors are not inherited by child classes.

### When is a constructor called?

> A constructor is automatically called when an object is created using `new`.

### What is a parameterized constructor?

> A constructor that accepts parameters to initialize an object with specific values.

### What happens if no constructor is written?

> Java provides a default no-argument constructor, provided that no constructor is explicitly declared.

---

# 📝 Practice Questions

### Q1. What is the main purpose of a constructor?

A. Delete an object  
B. Initialize an object  
C. Inherit a class  
D. Create a method

**Answer:** B

---

### Q2. Can a constructor have a return type?

A. Yes  
B. Only `void`  
C. No  
D. Only `int`

**Answer:** C

---

### Q3. Which keyword is used to create an object?

A. `class`  
B. `object`  
C. `new`  
D. `create`

**Answer:** C

---

### Q4. Can constructors be overloaded?

A. Yes  
B. No

**Answer:** A

---

### Q5. Which one is a constructor?

```java
class Student {

    Student() {
    }
}
```

A. Method  
B. Constructor  
C. Object  
D. Variable

**Answer:** B

---

# ⚡ Quick Revision

```text
Constructor
    ↓
Special block
    ↓
Initializes object
    ↓
Same name as class
    ↓
No return type
    ↓
Automatically called
    ↓
Can be overloaded
    ↓
Not inherited
```

## ⭐ Key Point

> **Constructor is mainly used to initialize an object when the object is created.**
