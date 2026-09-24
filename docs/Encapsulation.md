# 📘 Java OOPs – Encapsulation

> 💡 **In this lesson:** Learn how to protect data inside a class and access it safely using methods.

---

# 1️⃣ What is Encapsulation?

**Encapsulation** means wrapping **data (variables)** and **methods** together inside a class and restricting direct access to the data.

### 🧠 Simple Definition

> Encapsulation is the process of hiding data and controlling access to it through methods.

### Real-World Example 🔒

Think about an **ATM**.

You can:

```text
Withdraw money
Deposit money
Check balance
```

But you cannot directly access the bank's internal balance data.

Similarly, in Java, we can make variables `private` and access them through methods.

---

# 2️⃣ How to Achieve Encapsulation?

Usually, we use:

```text
1. private variables
2. public getter methods
3. public setter methods
```

Example:

```java
class Student {

    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }
}
```

Here:

```text
private variables
        ↓
   Data is hidden
        ↓
getters / setters
        ↓
Controlled access
```

---

# 3️⃣ Why `private`?

The `private` keyword prevents direct access from outside the class.

Example:

```java
class Student {

    private int age;
}
```

We cannot do:

```java
Student s = new Student();

s.age = 21;   // ❌ Error
```

Because `age` is private.

Instead, we use a setter:

```java
s.setAge(21);
```

---

# 4️⃣ Getter Method

A **getter** is used to get/read the value of a private variable.

### Syntax

```java
public dataType getVariableName() {
    return variableName;
}
```

### Example

```java
public int getAge() {
    return age;
}
```

Usage:

```java
System.out.println(s.getAge());
```

---

# 5️⃣ Setter Method

A **setter** is used to set/update the value of a private variable.

### Syntax

```java
public void setVariableName(dataType value) {
    variableName = value;
}
```

### Example

```java
public void setAge(int age) {
    this.age = age;
}
```

Usage:

```java
s.setAge(21);
```

---

# 6️⃣ Complete Example

```java
class Student {

    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }

    public static void main(String[] args) {

        Student s = new Student();

        s.setName("Dharun");
        s.setAge(21);

        System.out.println("Name: " + s.getName());
        System.out.println("Age: " + s.getAge());
    }
}
```

### 📤 Output

```text
Name: Dharun
Age: 21
```

---

# 7️⃣ How Encapsulation Protects Data

We can also add validation inside setter methods.

Example:

```java
class Student {

    private int age;

    public void setAge(int age) {

        if (age > 0) {
            this.age = age;
        }
    }

    public int getAge() {
        return age;
    }
}
```

Now:

```java
Student s = new Student();

s.setAge(21);
```

✅ Valid value.

But:

```java
s.setAge(-5);
```

The value will not be accepted.

### ⭐ Important

This is one major benefit of encapsulation:

> We can **control how data is modified**.

---

# 8️⃣ Why Do We Use Encapsulation?

### 🔒 1. Data Hiding

Private variables cannot be accessed directly from outside.

### 🛡️ 2. Data Protection

We can control how data is changed.

### ✅ 3. Validation

We can validate values before storing them.

### 🔧 4. Maintainability

Internal implementation can be changed without affecting outside code.

### 🎯 5. Controlled Access

We decide which data can be read or modified.

---

# 9️⃣ Without Encapsulation

```java
class Student {

    public int age;
}
```

Anyone can directly modify it:

```java
Student s = new Student();

s.age = -100;
```

❌ Invalid data can be stored.

---

# 🔟 With Encapsulation

```java
class Student {

    private int age;

    public void setAge(int age) {

        if (age > 0) {
            this.age = age;
        }
    }

    public int getAge() {
        return age;
    }
}
```

Now:

```java
s.setAge(-100);
```

The class can reject the invalid value.

✅ Better control.

---

# 1️⃣1️⃣ Encapsulation vs Data Hiding

These terms are related but not exactly the same.

### Data Hiding

> Preventing direct access to internal data.

Usually achieved using:

```java
private
```

### Encapsulation

> Combining data and methods together and controlling access to the data.

### 🧠 Easy Memory Trick

```text
Data Hiding
     ↓
Hide the data

Encapsulation
     ↓
Hide + Control access
```

---

# 1️⃣2️⃣ Real-World Example

Consider a **Bank Account**.

```java
class BankAccount {

    private double balance;

    public void deposit(double amount) {

        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

Usage:

```java
BankAccount account = new BankAccount();

account.deposit(5000);

System.out.println(account.getBalance());
```

### 📤 Output

```text
5000.0
```

The user cannot directly do:

```java
account.balance = -5000;
```

because `balance` is private.

---

# 1️⃣3️⃣ Encapsulation Structure

Remember this pattern:

```text
             CLASS
               |
       ┌───────┴───────┐
       ↓               ↓
 Private Data       Methods
       ↓               ↓
   Hidden Data    Getter / Setter
                       ↓
                Controlled Access
```

---

# 1️⃣4️⃣ Important Interview Questions ⭐

### Q1. What is encapsulation?

> Encapsulation is the process of wrapping data and methods inside a class and controlling access to the data.

### Q2. How do you achieve encapsulation in Java?

> By declaring variables as `private` and providing public getter and setter methods.

### Q3. Why are variables made private?

> To prevent direct access and provide controlled access to the data.

### Q4. What is a getter?

> A getter method is used to read the value of a private variable.

### Q5. What is a setter?

> A setter method is used to modify the value of a private variable.

### Q6. What is the main benefit of encapsulation?

> Data protection and controlled access.

---

# 🧠 Quick Revision

```text
Encapsulation
      ↓
Data + Methods inside class
      ↓
Make data private
      ↓
Use getter/setter
      ↓
Controlled access
```

### ⭐ One-Line Memory Trick

```text
Encapsulation = Hide Data + Control Access
```

---

