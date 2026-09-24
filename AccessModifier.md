# 📘 Java OOPs –  Access Modifiers 🔐


# 1️⃣ What are Access Modifiers?

**Access modifiers** are keywords used to control the **visibility and accessibility** of classes, variables, methods, and constructors.

### Simple Definition

> **Access Modifier = Controls who can access a class member.**

Java has four access levels:

```text
1. public
2. private
3. protected
4. default
```

---

# 2️⃣ `public` 🌍

`public` members can be accessed **from anywhere**.

Example:

```java
class Student {

    public String name = "Dharun";

    public void display() {
        System.out.println(name);
    }
}
```

We can access them from another class:

```java
Student s = new Student();

System.out.println(s.name);
s.display();
```

### Memory Trick

```text
public = Accessible everywhere
```

---

# 3️⃣ `private` 🔒

`private` members can be accessed **only inside the same class**.

Example:

```java
class Student {

    private int age = 22;

    void display() {
        System.out.println(age);
    }
}
```

This is valid:

```java
Student s = new Student();

s.display();
```

But this is invalid:

```java
System.out.println(s.age); // ❌ Error
```

### Why?

Because `age` is private.

### Memory Trick

```text
private = Same class only
```

This is commonly used in **encapsulation**.

---

# 4️⃣ `protected` 🛡️

`protected` members can generally be accessed:

1. Inside the same class
2. By classes in the same package
3. By subclasses in other packages, subject to Java's protected-access rules

Example:

```java
class Animal {

    protected void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    void display() {
        sound();
    }
}
```

`Dog` can access the protected method because `Dog` is a subclass of `Animal`.

### Memory Trick

```text
protected = Same package + Subclasses
```

---

# 5️⃣ Default Access / Package-Private 📦

If we do not specify an access modifier, Java uses **default (package-private) access**.

Example:

```java
class Student {

    int age = 22;

    void display() {
        System.out.println(age);
    }
}
```

Here:

```java
int age
```

has default access.

It can be accessed by classes in the **same package**, but not directly from unrelated classes in another package.

### Memory Trick

```text
default = Same package
```

---

# 6️⃣ Access Modifier Comparison ⭐

| Modifier | Same Class | Same Package | Subclass in Different Package | Other Class in Different Package |
|---|---:|---:|---:|---:|
| `public` | ✅ | ✅ | ✅ | ✅ |
| `protected` | ✅ | ✅ | ✅* | ❌ |
| default | ✅ | ✅ | ❌ | ❌ |
| `private` | ✅ | ❌ | ❌ | ❌ |

`*` For `protected` members in a different package, access is available through inheritance/subclass rules.

---

# 7️⃣ Example with All Four

```java
class Student {

    public String name = "Dharun";

    private int age = 22;

    protected String department = "CSE";

    String college = "VSB";
}
```

Here:

```text
name
↓
public

age
↓
private

department
↓
protected

college
↓
default
```

---

# 8️⃣ Access Modifiers and Encapsulation

Access modifiers are very important for **encapsulation**.

Example:

```java
class BankAccount {

    private double balance;

    public void setBalance(double balance) {

        if (balance >= 0) {
            this.balance = balance;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

Here:

```text
balance
   ↓
private
   ↓
Cannot directly access
   ↓
Controlled through methods
```

This protects the data from direct modification.

---

# 9️⃣ Can a Top-Level Class Be `private`?

A normal top-level class cannot be declared:

```java
private class Student {
}
```

❌ Invalid.

A top-level class can generally be:

```java
public class Student {
}
```

or have default/package-private access:

```java
class Student {
}
```

Nested classes can use `private`, `protected`, etc.

---

# 🔟 Can a Top-Level Class Be `protected`?

❌ No.

A top-level class cannot be declared:

```java
protected class Student {
}
```

`protected` is applicable to members and nested classes, but not ordinary top-level classes.

---

# 1️⃣1️⃣ `public` vs `private`

| `public` | `private` |
|---|---|
| Accessible from anywhere | Accessible only inside same class |
| Less restrictive | Most restrictive |
| Often used for public methods/APIs | Often used for data hiding |
| Supports controlled external access when used with methods | Helps implement encapsulation |

Example:

```java
class Student {

    private String name;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

This is a common encapsulation pattern.

---

# 1️⃣2️⃣ `protected` vs `default`

This is an important interview question.

### Default

```text
Same package only
```

### Protected

```text
Same package
+
Subclasses in other packages
```

So:

```text
default   → Package
protected → Package + Inheritance
```

---

# 🧠 Easy Memory Trick

Think of access levels from **most open to most restricted**:

```text
public
  ↓
protected
  ↓
default
  ↓
private
```

Remember:

```text
PUBLIC     → Everywhere
PROTECTED  → Package + Subclass
DEFAULT    → Package
PRIVATE    → Same class
```

---

# 🎯 Interview One-Liners

### What are access modifiers?

> Access modifiers control the visibility and accessibility of classes and class members in Java.

### How many access levels are there in Java?

> Java has four access levels: public, protected, default, and private.

### Which is the most restrictive?

> `private` is the most restrictive access level.

### Which is the least restrictive?

> `public` is the least restrictive.

### What is default access?

> If no access modifier is specified, the member has package-private access and can be accessed within the same package.

### What is protected access?

> A protected member is accessible within the same package and also by subclasses in other packages, subject to protected-access rules.

### Can a top-level class be private?

> No. A normal top-level class cannot be private.

---

# 📝 Practice Questions

### Q1. Which modifier provides the widest access?

A. `private`  
B. `protected`  
C. `default`  
D. `public`

**Answer:** D

---

### Q2. Which modifier allows access only within the same class?

A. `public`  
B. `private`  
C. `protected`  
D. `default`

**Answer:** B

---

### Q3. What is the access level when no modifier is specified?

A. `public`  
B. `private`  
C. `protected`  
D. package-private/default

**Answer:** D

---

### Q4. Which modifier provides package access plus subclass access across packages?

A. `private`  
B. `default`  
C. `protected`  
D. `public`

**Answer:** C

---

### Q5. Which access modifier is commonly used for data hiding?

A. `public`  
B. `private`  
C. `default`  
D. `protected`

**Answer:** B

---

# ⚡ Quick Revision

```text
Access Modifiers
       ↓
Control Access
       ↓
--------------------------------
public     → Everywhere
protected  → Same package + subclass
default    → Same package
private    → Same class
--------------------------------
```

## ⭐ Key Point

> **Access modifiers control who can access a class member. `public` gives broadest access, while `private` gives the most restricted access.**
