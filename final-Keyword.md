# 📘 Java OOPs – `final` Keyword 🔒


# 1️⃣ What is `final`?

`final` is a keyword used to **restrict modification**.

### Simple Definition

> **`final` = Cannot be changed further.**

It can be used with:

```text
1. Variable
2. Method
3. Class
```

---

# 2️⃣ `final` Variable

A variable declared as `final` cannot be reassigned after it has been initialized.

Example:

```java
class Student {

    public static void main(String[] args) {

        final int age = 22;

        System.out.println(age);
    }
}
```

### Output

```text
22
```

But this is not allowed:

```java
final int age = 22;

age = 23;   // ❌ Error
```

Because `age` is final.

---

# 3️⃣ Final Variable Must Be Initialized

A final variable must receive a value before it is read.

This is valid:

```java
final int age = 22;
```

A final instance variable can also be initialized in a constructor:

```java
class Student {

    final int age;

    Student(int age) {
        this.age = age;
    }
}
```

Here, the value is assigned once for each object.

---

# 4️⃣ Final Variable Cannot Be Reassigned

Example:

```java
class Student {

    final String name = "Dharun";

    public static void main(String[] args) {

        Student s = new Student();

        System.out.println(s.name);

        // s.name = "Rahul";  // ❌ Error
    }
}
```

Once assigned:

```text
name = "Dharun"
```

we cannot assign another value to `name`.

---

# 5️⃣ `static final` Constants ⭐

A very common use is:

```java
static final
```

Example:

```java
class MathConstants {

    static final double PI = 3.14159;
}
```

We access it using:

```java
System.out.println(MathConstants.PI);
```

### Meaning

```text
static
  ↓
Belongs to class

final
  ↓
Cannot be reassigned
```

So:

```java
static final
```

is commonly used for **constants**.

### Naming Convention

Constants are usually written in:

```text
UPPER_CASE
```

Example:

```java
static final int MAX_SIZE = 100;
static final double PI = 3.14159;
```

---

# 6️⃣ `final` Method

A method declared with `final` cannot be **overridden** by a subclass.

Example:

```java
class Animal {

    final void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    // ❌ Cannot override
    // void sound() {
    //     System.out.println("Dog sound");
    // }
}
```

### Why?

Because:

```text
final method
     ↓
Cannot be overridden
     ↓
Child must use parent's implementation
```

---

# 7️⃣ `final` Method Can Be Called

`final` does **not** mean the method cannot be used.

It only means it cannot be overridden.

Example:

```java
class Animal {

    final void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    void display() {
        sound();
    }

    public static void main(String[] args) {

        Dog d = new Dog();

        d.display();
    }
}
```

### Output

```text
Animal sound
```

The child can call the method, but cannot provide another implementation for it.

---

# 8️⃣ `final` Class

A class declared as `final` cannot be inherited.

Example:

```java
final class Vehicle {

    void drive() {
        System.out.println("Driving");
    }
}
```

This is not allowed:

```java
class Car extends Vehicle {
}
```

❌ Compilation error.

### Meaning

```text
final class
     ↓
Cannot be extended
```

---

# 9️⃣ Example of Final Class

Java provides some important final classes.

For example:

```java
String
```

is a final class.

So we cannot do:

```java
class MyString extends String {
}
```

❌ Not allowed.

---

# 🔟 Final Reference Variable

This is an important concept.

Consider:

```java
final Student s = new Student();
```

The reference `s` cannot point to another `Student` object.

But if the object's fields are mutable, the object's state can still change.

Example:

```java
class Student {

    String name;
}

class Test {

    public static void main(String[] args) {

        final Student s = new Student();

        s.name = "Dharun";

        System.out.println(s.name);

        // s = new Student();  // ❌ Error
    }
}
```

### Important

```text
final reference
      ↓
Reference cannot be changed
      ↓
Object may still be modified
```

So `final` does not automatically make the entire object immutable.

---

# 1️⃣1️⃣ Final Variable vs Final Reference

### Final primitive

```java
final int x = 10;
```

Cannot change:

```java
x = 20;   // ❌
```

### Final reference

```java
final Student s = new Student();
```

Cannot change the reference:

```java
s = new Student();   // ❌
```

But if allowed by the object's class:

```java
s.name = "Dharun";   // ✅
```

---

# 1️⃣2️⃣ `final` and Inheritance

`final` can restrict inheritance at two levels.

### Final class

```java
final class Animal {
}
```

No class can extend it.

### Final method

```java
class Animal {

    final void sound() {
    }
}
```

A child class can extend `Animal`, but cannot override `sound()`.

### Memory

```text
final class
    ↓
No inheritance

final method
    ↓
No overriding
```

---

# 1️⃣3️⃣ `final` vs `static final`

| `final` | `static final` |
|---|---|
| Value cannot be reassigned | Value cannot be reassigned |
| Can belong to each object | Belongs to class |
| Each object can have its own final value | One class-level value |
| Often used for immutable reference/constant state | Commonly used for constants |

Example:

```java
class Student {

    final int rollNo;

    static final String COLLEGE = "VSB";
}
```

Here:

```text
rollNo
↓
Final instance variable

COLLEGE
↓
Static final class constant
```

---

# 1️⃣4️⃣ `final` vs `finally` vs `finalize`

This is a very common interview question.

| `final` | `finally` | `finalize` |
|---|---|---|
| Keyword | Block | Method |
| Used for restriction | Used with exception handling | Legacy GC-related method |
| `final int x` | `finally { }` | `finalize()` |
| Prevents reassignment/overriding/inheritance | Usually executes after try/catch processing | Deprecated and should not be relied upon |

### Example

```java
final int x = 10;
```

`final` → keyword

```java
try {
    // code
}
finally {
    // cleanup
}
```

`finally` → exception-handling block

`finalize()` was an old object-cleanup mechanism and is **deprecated in modern Java**. It should not be used for resource cleanup.

---

# 1️⃣5️⃣ Can a Constructor Be `final`?

❌ No.

Example:

```java
class Student {

    final Student() {
    }
}
```

This is invalid.

### Why?

Constructors are not inherited or overridden, so making a constructor `final` has no purpose.

---

# 1️⃣6️⃣ Can an Abstract Class Be Final?

❌ No.

Example:

```java
abstract final class Animal {
}
```

This is invalid.

### Why?

The concepts conflict:

```text
abstract class
    ↓
Designed to be extended

final class
    ↓
Cannot be extended
```

---

# 🧠 Easy Memory Trick

Remember:

```text
final variable
      ↓
Cannot reassign

final method
      ↓
Cannot override

final class
      ↓
Cannot extend
```

### One-line memory

> **Variable → Value, Method → Override, Class → Inheritance**

---

# 🎯 Interview One-Liners

### What is `final`?

> `final` is a keyword used to restrict modification of variables, methods, and classes.

### What is a final variable?

> A final variable cannot be reassigned after it has been initialized.

### What is a final method?

> A final method cannot be overridden by a subclass.

### What is a final class?

> A final class cannot be inherited or extended.

### Can a final variable be changed?

> No, it cannot be reassigned after initialization.

### Can a final object be modified?

> A final reference cannot point to another object, but the referenced object's mutable state can still change.

### Can a constructor be final?

> No, constructors cannot be declared final.

### Can an abstract class be final?

> No, because an abstract class is designed for inheritance while a final class cannot be inherited.

---

# 📝 Practice Questions

### Q1. What does `final` do to a variable?

A. Makes it static  
B. Prevents reassignment  
C. Makes it private  
D. Deletes it

**Answer:** B

---

### Q2. What does `final` do to a method?

A. Prevents overriding  
B. Prevents calling  
C. Makes it static  
D. Makes it private

**Answer:** A

---

### Q3. What does `final` do to a class?

A. Prevents object creation  
B. Prevents inheritance  
C. Prevents methods  
D. Makes it abstract

**Answer:** B

---

### Q4. Which is commonly used to declare a constant?

A. `private static`  
B. `static final`  
C. `public volatile`  
D. `protected final static` only

**Answer:** B

---

### Q5. Can a constructor be final?

A. Yes  
B. No

**Answer:** B

---

### Q6. What is the output?

```java
class Test {

    static final int VALUE = 100;

    public static void main(String[] args) {

        System.out.println(VALUE);
    }
}
```

### Output

```text
100
```

---

# ⚡ Quick Revision

```text
final
  ↓
Restriction
  ↓
--------------------------------
final variable
→ Cannot be reassigned

final method
→ Cannot be overridden

final class
→ Cannot be inherited
--------------------------------

static final
→ Commonly used for constants

final reference
→ Reference cannot change,
  object state may still change
```

## ⭐ Key Point

> **`final` restricts change: a final variable cannot be reassigned, a final method cannot be overridden, and a final class cannot be extended.**
