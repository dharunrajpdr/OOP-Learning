# 📘 Java OOPs – Method Overloading

# 1️⃣ What is Method Overloading?

**Method Overloading** means having multiple methods with the **same name but different parameters** in the same class.

### Simple Definition

> **Method Overloading = Same method name + Different parameter list**

Example:

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

Here both methods are named:

```text
add()
```

But their parameters are different.

Therefore, this is **Method Overloading**.

---

# 2️⃣ Why Do We Use Method Overloading?

It allows us to use the **same method name for similar operations** with different inputs.

Without overloading:

```java
addTwoNumbers();
addThreeNumbers();
addDoubleNumbers();
```

With overloading:

```java
add();
add();
add();
```

This makes the code easier to understand and use.

---

# 3️⃣ Basic Example

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

### Output

```text
30
60
```

Java decides which `add()` method to call based on the arguments.

---

# 4️⃣ How Can We Overload a Method?

A method can be overloaded by changing:

```text
1. Number of parameters
2. Type of parameters
3. Order of parameters
```

---

# 5️⃣ Change Number of Parameters

Example:

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

Here:

```text
add(int, int)
add(int, int, int)
```

The number of parameters is different.

✅ Valid overloading.

---

# 6️⃣ Change Type of Parameters

Example:

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

Here:

```text
add(int, int)
add(double, double)
```

The parameter types are different.

✅ Valid overloading.

---

# 7️⃣ Change Order of Parameters

Example:

```java
class Demo {

    void display(int a, double b) {
        System.out.println("int, double");
    }

    void display(double a, int b) {
        System.out.println("double, int");
    }
}
```

Here:

```text
display(int, double)
display(double, int)
```

The order of parameter types is different.

✅ Valid overloading.

---

# 8️⃣ ❌ Cannot Overload Only by Return Type

This is NOT valid:

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    double add(int a, int b) {
        return a + b;
    }
}
```

Both methods have:

```text
add(int, int)
```

Only the return type is different.

❌ This is not method overloading.

### Important

> **Return type alone cannot be used for method overloading.**

---

# 9️⃣ Method Signature

For method overloading, the important part is the:

```text
Method Name
+
Parameter List
```

Example:

```java
add(int, int)
add(int, int, int)
add(double, double)
```

These have different parameter lists.

---

# 🔟 Compile-Time Polymorphism

Method overloading is called:

> **Compile-Time Polymorphism**

Why?

Because the compiler determines which method should be called based on the arguments.

Example:

```java
Calculator c = new Calculator();

c.add(10, 20);
```

The compiler selects:

```java
add(int, int)
```

And:

```java
c.add(10, 20, 30);
```

selects:

```java
add(int, int, int)
```

### 🧠 Easy Memory

```text
Overloading
     ↓
Compile Time
```

---

# 1️⃣1️⃣ Real-World Example

Think about a printer.

It may print:

```text
print(String text)
print(String text, int copies)
print(String text, String format)
```

The operation is still:

```text
print()
```

but the input parameters are different.

This is method overloading.

---

# 1️⃣2️⃣ Constructor Overloading

Overloading is not limited to methods.

Constructors can also be overloaded.

Example:

```java
class Student {

    String name;
    int age;

    Student() {
        System.out.println("Default constructor");
    }

    Student(String name) {
        this.name = name;
    }

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Here we have:

```text
Student()
Student(String)
Student(String, int)
```

This is **Constructor Overloading**.

---

# 1️⃣3️⃣ Method Overloading with Different Data Types

```java
class Calculator {

    void display(int value) {
        System.out.println("Integer: " + value);
    }

    void display(double value) {
        System.out.println("Double: " + value);
    }

    void display(String value) {
        System.out.println("String: " + value);
    }

    public static void main(String[] args) {

        Calculator c = new Calculator();

        c.display(10);
        c.display(10.5);
        c.display("Hello");
    }
}
```

### Output

```text
Integer: 10
Double: 10.5
String: Hello
```

---

# 1️⃣4️⃣ Important Rules

### Rule 1️⃣

Same method name:

```java
add()
add()
```

### Rule 2️⃣

Parameter list must be different:

```java
add(int, int)
add(int, int, int)
```

### Rule 3️⃣

Return type alone cannot differentiate methods:

```java
int add(int, int)
double add(int, int)  // ❌
```

### Rule 4️⃣

Access modifiers can be different.

```java
public void display(int x) {
}

private void display(String x) {
}
```

This is valid overloading because the parameter types differ.

---

# 1️⃣5️⃣ Overloading vs Overriding

This is a **very common interview question**.

| Method Overloading | Method Overriding |
|---|---|
| Same class is enough | Requires inheritance |
| Same method name | Same method name |
| Different parameters | Same parameters |
| Compile-time polymorphism | Runtime polymorphism |
| Usually within the same class | Parent-child classes |
| Return type alone cannot overload | Return type must be compatible |

### 🧠 Easy Memory

```text
Overloading
     ↓
Different Parameters
     ↓
Compile Time


Overriding
     ↓
Same Signature
     ↓
Different Implementation
     ↓
Runtime
```

---

# 1️⃣6️⃣ Simple Comparison

### Overloading

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

### Overriding

```java
class Animal {

    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

---

# 🧠 Easy Memory Trick

Remember:

```text
OVERLOADING
     ↓
Same Name
     +
Different Parameters
     ↓
Compile Time
```

```text
OVERRIDING
     ↓
Same Signature
     +
Different Implementation
     ↓
Runtime
```

---

# 🎯 Interview One-Liners

### What is Method Overloading?

> Method overloading is defining multiple methods with the same name but different parameter lists.

### What type of polymorphism is Method Overloading?

> Method overloading is compile-time polymorphism.

### Can we overload a method by changing only the return type?

> No, return type alone cannot be used for method overloading.

### How can we overload a method?

> By changing the number, type, or order of parameters.

### Can constructors be overloaded?

> Yes, constructors can be overloaded.

### Can static methods be overloaded?

> Yes, static methods can be overloaded.

### Can private methods be overloaded?

> Yes, private methods can be overloaded within the same class.

### Is inheritance required for method overloading?

> No, inheritance is not required for method overloading.

---

# 📝 Practice Questions

### Q1. What is Method Overloading?

A. Same method with same parameters  
B. Same method name with different parameters  
C. Different method names  
D. Method hiding

**Answer:** B

---

### Q2. Method Overloading represents:

A. Runtime polymorphism  
B. Compile-time polymorphism  
C. Encapsulation  
D. Abstraction

**Answer:** B

---

### Q3. Can methods be overloaded only by changing return type?

A. Yes  
B. No

**Answer:** B

---

### Q4. Which can be changed for method overloading?

A. Number of parameters  
B. Type of parameters  
C. Order of parameters  
D. All of the above

**Answer:** D

---

### Q5. Is inheritance required for method overloading?

A. Yes  
B. No

**Answer:** B

---

# ⚡ Quick Revision

```text
Method Overloading
        ↓
Same Method Name
        +
Different Parameter List
        ↓
Compile-Time Polymorphism
```

### Ways to Overload

```text
1. Different number of parameters
2. Different parameter types
3. Different order of parameter types
```

### Cannot

```text
Only return type ❌
```

### Example

```java
add(int, int)
add(int, int, int)
add(double, double)
```

## ⭐ Key Point

> **Method Overloading = Same method name + Different parameters + Compile-time polymorphism.**
