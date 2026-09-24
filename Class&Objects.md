# 📘 Java OOPs – Class & Object

> 💡 **In this lesson:** Learn what a class and object are, how to create them, and how they work together.

---

# 1️⃣ What is a Class?

A **class** is a blueprint or template used to create objects.

It defines:

- Data → Variables
- Behavior → Methods

### 🧠 Simple Definition

> A class is a blueprint that defines the properties and behaviors of an object.

### Example

```java
class Student {

    String name;
    int age;

    void study() {
        System.out.println("Student is studying");
    }
}
```

Here:

```text
Student → Class
name    → Variable
age     → Variable
study() → Method
```

---

# 2️⃣ What is an Object?

An **object** is an instance of a class.

It is created using the `new` keyword.

### Syntax

```java
ClassName objectName = new ClassName();
```

### Example

```java
Student s1 = new Student();
```

Here:

```text
Student → Class
s1      → Object
new     → Creates a new object
```

---

# 3️⃣ Simple Example

```java
class Student {

    String name;
    int age;

    void display() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }

    public static void main(String[] args) {

        Student s1 = new Student();

        s1.name = "Dharun";
        s1.age = 21;

        s1.display();
    }
}
```

### 📤 Output

```text
Name: Dharun
Age: 21
```

---

# 4️⃣ How Does It Work?

### Step 1: Create a class

```java
class Student {
    String name;
    int age;
}
```

The class defines what a `Student` object will contain.

---

### Step 2: Create an object

```java
Student s1 = new Student();
```

An object named `s1` is created.

---

### Step 3: Assign values

```java
s1.name = "Dharun";
s1.age = 21;
```

We access object variables using the `.` operator.

---

### Step 4: Call the method

```java
s1.display();
```

The object calls the `display()` method.

---

# 5️⃣ Multiple Objects

One class can be used to create multiple objects.

```java
class Student {

    String name;
    int age;

    void display() {
        System.out.println(name + " - " + age);
    }

    public static void main(String[] args) {

        Student s1 = new Student();
        Student s2 = new Student();

        s1.name = "Dharun";
        s1.age = 21;

        s2.name = "Arun";
        s2.age = 22;

        s1.display();
        s2.display();
    }
}
```

### 📤 Output

```text
Dharun - 21
Arun - 22
```

### Important Point ⭐

Both objects are created from the same class, but each object has its **own data**.

```text
Student
   |
   ├── s1 → Dharun, 21
   |
   └── s2 → Arun, 22
```

---

# 6️⃣ Class vs Object

| Class | Object |
|---|---|
| Blueprint/template | Instance of a class |
| Defines properties and methods | Contains actual values |
| Used to create objects | Created from a class |
| Example: `Student` | Example: `s1` |

### 🧠 Easy Memory Trick

```text
Class  → Blueprint
Object → Real instance
```

### Real-World Example

```text
Class  → Car

Objects:
    car1 → BMW
    car2 → Audi
    car3 → Tesla
```

The class describes what a car can have/do.

Each object represents an individual car.

---

# 7️⃣ What is the `new` Keyword?

The `new` keyword is used to create an object.

```java
Student s1 = new Student();
```

Here:

```text
Student s1
    ↓
Reference variable

new Student()
    ↓
Creates object
```

---

# 8️⃣ What is the `.` Operator?

The dot `.` operator is used to access variables and methods of an object.

### Access variable

```java
s1.name = "Dharun";
```

### Call method

```java
s1.display();
```

So:

```text
object.variable
object.method()
```

---

# 9️⃣ Class with Multiple Methods

```java
class Calculator {

    int a = 10;
    int b = 20;

    void add() {
        System.out.println(a + b);
    }

    void multiply() {
        System.out.println(a * b);
    }

    public static void main(String[] args) {

        Calculator c = new Calculator();

        c.add();
        c.multiply();
    }
}
```

### 📤 Output

```text
30
200
```

---

# 🔟 Important Interview Points ⭐

### Q1. What is a class?

> A class is a blueprint or template used to create objects. It contains variables and methods.

### Q2. What is an object?

> An object is an instance of a class that represents a real entity and can access the class members.

### Q3. How do you create an object in Java?

```java
Student s1 = new Student();
```

### Q4. Which keyword is used to create an object?

> `new`

### Q5. How do you access members of an object?

> Using the dot `.` operator.

Example:

```java
s1.name;
s1.display();
```

---

# 🧠 Quick Revision

```text
Class
  ↓
Blueprint / Template
  ↓
Contains variables + methods
  ↓
Used to create objects
```

```text
Object
  ↓
Instance of a class
  ↓
Created using new
  ↓
Access members using .
```

### ⭐ One-Line Memory Trick

```text
Class = Blueprint
Object = Instance
new = Creates Object
. = Access Object Members
```

---

# 📝 Practice Questions

### Basic

1. Create a `Student` class with:
   - `name`
   - `age`
   - `display()` method

2. Create two `Student` objects and display their details.

3. Create a `Car` class with:
   - `brand`
   - `price`
   - `display()` method

4. Create a `Calculator` class with methods:
   - `add()`
   - `subtract()`
   - `multiply()`

### Interview Practice

5. What is the difference between a class and an object?

6. Why do we use the `new` keyword?

7. Can we create multiple objects from one class?

8. How do we access object variables and methods?

---

# ⭐ Key Point

> **A class is a blueprint, while an object is an instance of that class.**

Example:

```java
class Student {
    String name;
}

Student s1 = new Student();
```

Here:

```text
Student → Class
s1      → Object
name    → Variable
new     → Object creation
.       → Member access
```
