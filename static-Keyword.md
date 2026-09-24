# 📘 Java OOPs –  `static` Keyword ⚡

# 1️⃣ What is `static`?

`static` is a keyword used to make a member belong to the **class rather than individual objects**.

### Simple Definition

> **`static` = Belongs to the class, not to a particular object.**

Example:

```java
class Student {

    static String college = "VSB";
}
```

The `college` variable belongs to the `Student` class.

We can access it using:

```java
Student.college
```

---

# 2️⃣ Why Do We Use `static`?

Suppose 100 students study in the same college.

Without `static`:

```text
Student 1 → college = VSB
Student 2 → college = VSB
Student 3 → college = VSB
...
```

Each object would have its own copy.

With `static`:

```text
             Student Class
                  |
              college
                  |
        ---------------------
        |        |          |
     Student1 Student2  Student3
```

Only **one shared copy** is associated with the class.

---

# 3️⃣ Static Variable

A variable declared with `static` is called a **static variable** or **class variable**.

Example:

```java
class Student {

    String name;
    static String college = "VSB";
}
```

Here:

```java
name
```

is an instance variable.

```java
college
```

is a static variable.

---

# 4️⃣ Example of Static Variable

```java
class Student {

    String name;
    static String college = "VSB";

    Student(String name) {
        this.name = name;
    }

    void display() {
        System.out.println(name + " - " + college);
    }

    public static void main(String[] args) {

        Student s1 = new Student("Dharun");
        Student s2 = new Student("Rahul");

        s1.display();
        s2.display();
    }
}
```

### Output

```text
Dharun - VSB
Rahul - VSB
```

Both objects share the same `college` value.

---

# 5️⃣ Accessing Static Variables

Recommended way:

```java
Student.college
```

We can also access it through an object:

```java
Student s = new Student("Dharun");

System.out.println(s.college);
```

But using the **class name** is clearer because the variable belongs to the class:

```java
Student.college
```

---

# 6️⃣ Changing a Static Variable

Example:

```java
class Student {

    static String college = "VSB";

    public static void main(String[] args) {

        System.out.println(Student.college);

        Student.college = "ABC";

        System.out.println(Student.college);
    }
}
```

### Output

```text
VSB
ABC
```

Since it is shared, changing it changes the value seen through the class.

---

# 7️⃣ Static Method

A method declared with `static` is called a **static method**.

Example:

```java
class Student {

    static void display() {
        System.out.println("Hello Student");
    }

    public static void main(String[] args) {

        Student.display();
    }
}
```

### Output

```text
Hello Student
```

We don't need to create an object.

```java
Student.display();
```

---

# 8️⃣ Why is `main()` Static?

You have already seen:

```java
public static void main(String[] args)
```

Why is `main()` static?

Because the JVM needs to call `main()` **without first creating an object of the class**.

So:

```text
JVM
 ↓
main()
```

can be called directly through the class.

---

# 9️⃣ Static Method Cannot Directly Access Instance Variables

Example:

```java
class Student {

    int age = 22;

    static void display() {

        System.out.println(age); // ❌ Error
    }
}
```

Why?

Because:

```text
static method
      ↓
belongs to class
      ↓
no specific object
      ↓
which object's age?
      ↓
Cannot access directly
```

---

# 🔟 Correct Way

We can create an object inside the static method:

```java
class Student {

    int age = 22;

    static void display() {

        Student s = new Student();

        System.out.println(s.age);
    }

    public static void main(String[] args) {

        Student.display();
    }
}
```

### Output

```text
22
```

---

# 1️⃣1️⃣ Static Method Can Directly Access Static Members

Example:

```java
class Student {

    static String college = "VSB";

    static void display() {

        System.out.println(college);
    }

    public static void main(String[] args) {

        display();
    }
}
```

### Output

```text
VSB
```

Because both belong to the class.

---

# 1️⃣2️⃣ Static Block

A **static block** is used to initialize static data or perform class-level initialization.

Syntax:

```java
static {
    // code
}
```

Example:

```java
class Student {

    static {
        System.out.println("Static block executed");
    }

    public static void main(String[] args) {
        System.out.println("Main method executed");
    }
}
```

### Output

```text
Static block executed
Main method executed
```

The static block executes when the class is initialized, before `main()` in this example.

---

# 1️⃣3️⃣ Multiple Static Blocks

A class can contain multiple static blocks.

```java
class Student {

    static {
        System.out.println("Block 1");
    }

    static {
        System.out.println("Block 2");
    }

    public static void main(String[] args) {
        System.out.println("Main");
    }
}
```

### Output

```text
Block 1
Block 2
Main
```

They execute in their order of appearance when the class is initialized.

---

# 1️⃣4️⃣ Static vs Instance

| Static | Instance |
|---|---|
| Belongs to class | Belongs to object |
| One shared member per class | Each object has its own instance state |
| Access using class name | Usually access through object |
| Does not require object for access | Requires an object |
| Example: `Student.college` | Example: `s1.name` |

### Memory Trick

```text
static   → Class
instance → Object
```

---

# 1️⃣5️⃣ Static Variable vs Instance Variable

Example:

```java
class Student {

    String name;              // Instance variable
    static String college;   // Static variable
}
```

For:

```java
Student s1 = new Student();
Student s2 = new Student();
```

Conceptually:

```text
s1.name       → separate
s2.name       → separate

college       → shared
```

---

# 1️⃣6️⃣ Important Rules of Static

### Rule 1️⃣

A static method can directly access static members.

```java
static int x = 10;

static void display() {
    System.out.println(x);
}
```

✅ Valid

---

### Rule 2️⃣

A static method cannot directly access instance members.

```java
int x = 10;

static void display() {
    System.out.println(x);
}
```

❌ Invalid

---

### Rule 3️⃣

`this` cannot be used inside a static context.

```java
static void display() {
    System.out.println(this);
}
```

❌ Invalid

Because `this` refers to a current object, while static members belong to the class.

---

### Rule 4️⃣

Static methods can be overloaded.

```java
static void display() {
}

static void display(int x) {
}
```

✅ Valid

---

### Rule 5️⃣

Static methods are **hidden**, not overridden, when a child class declares a static method with the same signature as the parent.

This is called **method hiding**.

---

# 1️⃣7️⃣ Can We Create an Object of a Class Having Static Members?

Yes.

Example:

```java
class Student {

    static String college = "VSB";

    public static void main(String[] args) {

        Student s = new Student();

        System.out.println(Student.college);
    }
}
```

Static members do not prevent object creation.

---

# 1️⃣8️⃣ Real-World Example

Suppose a company has many employees.

```java
class Employee {

    String name;
    static String company = "ABC Technologies";
}
```

Each employee has a different:

```text
name
```

But all employees may share:

```text
company
```

So:

```java
Employee.company
```

is a good candidate for a static variable.

---

# 🧠 Easy Memory Trick

Remember:

```text
STATIC
  ↓
CLASS
  ↓
Shared
```

### Three important forms:

```text
static variable
      ↓
shared class data

static method
      ↓
class-level behavior

static block
      ↓
class initialization
```

---

# 🎯 Interview One-Liners

### What is `static`?

> `static` is a keyword used to make a member belong to the class rather than to individual objects.

### What is a static variable?

> A static variable is a class-level variable shared by instances of that class.

### What is a static method?

> A static method belongs to the class and can be called without creating an object.

### Why is `main()` static?

> `main()` is static so the JVM can invoke it without creating an object of the class.

### Can a static method access an instance variable directly?

> No, because a static method does not have a specific object context.

### Can a static method access static variables?

> Yes, it can directly access static members of the class.

### Can we use `this` inside a static method?

> No, because `this` refers to the current object and a static method is not associated with a specific object.

### Can static methods be overloaded?

> Yes, static methods can be overloaded.

### Are static methods overridden?

> No. Static methods are hidden when a child class declares a matching static method.

---

# 📝 Practice Questions

### Q1. What does `static` mean?

A. Belongs to object  
B. Belongs to class  
C. Creates an object  
D. Creates inheritance

**Answer:** B

---

### Q2. Which method is the entry point of a Java program?

A. `start()`  
B. `run()`  
C. `main()`  
D. `execute()`

**Answer:** C

---

### Q3. Can a static method directly access an instance variable?

A. Yes  
B. No

**Answer:** B

---

### Q4. How should a static variable generally be accessed?

A. `object.variable`  
B. `ClassName.variable`  
C. `this.variable`  
D. `super.variable`

**Answer:** B

---

### Q5. What is the output?

```java
class Test {

    static int count = 0;

    Test() {
        count++;
    }

    public static void main(String[] args) {

        new Test();
        new Test();
        new Test();

        System.out.println(count);
    }
}
```

### Output

```text
3
```

Because `count` is shared by all objects.

---

# ⚡ Quick Revision

```text
static
  ↓
Belongs to Class

static variable
  ↓
Shared class-level data

static method
  ↓
Can call without object

static block
  ↓
Runs during class initialization

static method
  ↓
Can directly access static members
  ↓
Cannot directly access instance members

this
  ↓
Cannot be used in static context
```

## ⭐ Key Point

> **`static` makes a member belong to the class instead of a particular object.**
