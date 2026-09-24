# 📘 Java OOPs – `this` Keyword 🔑


# 1️⃣ What is `this`?

`this` is a **reference variable** that refers to the **current object**.

### Simple Definition

> **`this` refers to the current object.**

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

```java
this.name
```

means the `name` variable belonging to the **current object**.

---

# 2️⃣ Why Do We Use `this`?

The most common use of `this` is to differentiate between:

- Instance variable
- Local variable / parameter

Example:

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }
}
```

There are two `name`s:

```java
String name          // instance variable
String name          // constructor parameter
```

So:

```java
this.name = name;
```

means:

```text
current object's name = parameter name
```

---

# 3️⃣ Without `this`

Consider:

```java
class Student {

    String name;

    Student(String name) {
        name = name;
    }
}
```

This does **not** correctly assign the parameter to the instance variable.

Both sides refer to the parameter.

So the object's `name` remains unchanged.

---

# 4️⃣ With `this`

Correct version:

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }

    void display() {
        System.out.println(name);
    }

    public static void main(String[] args) {

        Student s = new Student("Dharun");

        s.display();
    }
}
```

### Output

```text
Dharun
```

### Remember

```text
this.name → object's variable
name      → parameter
```

---

# 5️⃣ `this` Refers to Current Object

Example:

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }

    void display() {
        System.out.println(this.name);
    }
}
```

If we create:

```java
Student s1 = new Student("Dharun");
Student s2 = new Student("Rahul");
```

For `s1`:

```text
this → s1
```

For `s2`:

```text
this → s2
```

So `this` changes depending on the object that is currently executing the method or constructor.

---

# 6️⃣ `this` Can Be Used to Call Current Object's Method

We can use `this` to call another method of the same object.

```java
class Student {

    void display() {
        System.out.println("Display method");
    }

    void show() {
        this.display();
    }

    public static void main(String[] args) {

        Student s = new Student();

        s.show();
    }
}
```

### Output

```text
Display method
```

This:

```java
this.display();
```

means:

> Call the `display()` method of the current object.

Usually, we can simply write:

```java
display();
```

Both work in this situation.

---

# 7️⃣ `this()` – Calling Another Constructor

`this()` is different from `this`.

### `this`

Refers to the current object.

### `this()`

Calls another constructor of the **same class**.

Example:

```java
class Student {

    Student() {
        this("Dharun");
        System.out.println("No-argument constructor");
    }

    Student(String name) {
        System.out.println("Name: " + name);
    }

    public static void main(String[] args) {

        Student s = new Student();
    }
}
```

### Output

```text
Name: Dharun
No-argument constructor
```

### Flow

```text
new Student()
      ↓
Student()
      ↓
this("Dharun")
      ↓
Student(String name)
```

---

# 8️⃣ Important Rule of `this()`

When using `this()` to call another constructor:

> **`this()` must be the first statement inside the constructor.**

Correct:

```java
Student() {
    this("Dharun");
    System.out.println("Hello");
}
```

Incorrect:

```java
Student() {
    System.out.println("Hello");
    this("Dharun");   // ❌ Error
}
```

---

# 9️⃣ Constructor Chaining Using `this()`

Multiple constructors can call each other.

```java
class Student {

    Student() {
        this("Dharun");
    }

    Student(String name) {
        this(name, 22);
    }

    Student(String name, int age) {
        System.out.println(name + " " + age);
    }

    public static void main(String[] args) {

        Student s = new Student();
    }
}
```

### Output

```text
Dharun 22
```

### Flow

```text
Student()
   ↓
this("Dharun")
   ↓
Student(String)
   ↓
this(name, 22)
   ↓
Student(String, int)
```

This is called:

> **Constructor Chaining**

---

# 🔟 `this` as a Method Argument

We can pass the current object using `this`.

```java
class Student {

    void display(Student s) {
        System.out.println("Student object received");
    }

    void show() {
        display(this);
    }

    public static void main(String[] args) {

        Student s = new Student();

        s.show();
    }
}
```

### Output

```text
Student object received
```

Here:

```java
display(this);
```

passes the current object as an argument.

---

# 1️⃣1️⃣ `this` as a Constructor Argument

We can also pass the current object to another constructor.

Example:

```java
class Student {

    Student() {
        StudentHelper helper = new StudentHelper(this);
    }
}

class StudentHelper {

    StudentHelper(Student s) {
        System.out.println("Student object received");
    }
}
```

### Output

```text
Student object received
```

Here:

```java
new StudentHelper(this);
```

passes the current `Student` object.

---

# 1️⃣2️⃣ Returning `this`

A method can return the current object using `this`.

```java
class Student {

    Student getStudent() {
        return this;
    }

    public static void main(String[] args) {

        Student s = new Student();

        Student result = s.getStudent();

        System.out.println(result == s);
    }
}
```

### Output

```text
true
```

This is commonly useful in **method chaining**.

---

# 1️⃣3️⃣ `this` Cannot Be Used in a Static Context

`this` refers to a current object.

But a `static` method belongs to the class, not to a particular object.

Therefore:

```java
class Student {

    static void display() {
        System.out.println(this);
    }
}
```

❌ This gives a compilation error.

### Why?

```text
static method
     ↓
belongs to class
     ↓
no current object
     ↓
this cannot be used
```

---

# 1️⃣4️⃣ `this` vs `this()`

| `this` | `this()` |
|---|---|
| Refers to current object | Calls another constructor |
| Used with variables/methods | Used with constructors |
| Example: `this.name` | Example: `this("Dharun")` |
| Represents current object | Performs constructor chaining |

### Easy Memory Trick

```text
this
 ↓
Current Object

this()
 ↓
Current Class Constructor
```

---

# 1️⃣5️⃣ Common Uses of `this`

The `this` keyword can be used to:

### 1. Access instance variables

```java
this.name
```

### 2. Call current object's method

```java
this.display();
```

### 3. Call another constructor

```java
this("Dharun");
```

### 4. Pass current object as an argument

```java
display(this);
```

### 5. Return current object

```java
return this;
```

---

# 🧠 Easy Memory Trick

Remember:

```text
this = Current Object

this.variable
      ↓
Current object's variable

this.method()
      ↓
Current object's method

this()
      ↓
Another constructor of same class

return this
      ↓
Return current object
```

---

# 🎯 Interview One-Liners

### What is `this`?

> `this` is a reference variable that refers to the current object.

### Why is `this` commonly used in constructors?

> It is commonly used to differentiate instance variables from constructor parameters having the same name.

### What is `this()`?

> `this()` is used to call another constructor of the same class.

### Where should `this()` be placed?

> `this()` must be the first statement inside a constructor.

### Can `this` be used in a static method?

> No, because `this` refers to a current object, while a static method does not belong to a specific object.

### Can `this` be returned?

> Yes, `this` can be returned to return the current object.

---

# 📝 Practice Questions

### Q1. What does `this` refer to?

A. Parent class  
B. Current object  
C. Current class  
D. Static object

**Answer:** B

---

### Q2. What does `this()` do?

A. Creates an object  
B. Calls a method  
C. Calls another constructor  
D. Calls the parent constructor

**Answer:** C

---

### Q3. Where must `this()` appear in a constructor?

A. Last statement  
B. Any position  
C. First statement  
D. Outside the constructor

**Answer:** C

---

### Q4. Can `this` be used inside a static method?

A. Yes  
B. No

**Answer:** B

---

### Q5. What does this statement mean?

```java
this.name = name;
```

A. Both are local variables  
B. Current object's `name` gets the parameter value  
C. Creates a new object  
D. Calls a constructor

**Answer:** B

---

# ⚡ Quick Revision

```text
this
 ↓
Current Object

this.name
 ↓
Current object's variable

this.display()
 ↓
Current object's method

this()
 ↓
Another constructor

display(this)
 ↓
Pass current object

return this
 ↓
Return current object

❌ this cannot be used in static context
```

## ⭐ Key Point

> **`this` refers to the current object, while `this()` is used to call another constructor of the same class.**
