# 📘 Java OOPs – Method Overriding

# 1️⃣ What is Method Overriding?

**Method Overriding** occurs when a child class provides its own implementation of a method that is already defined in the parent class.

### Simple Definition

> **Method Overriding = Same method signature + Different implementation in child class**

Example:

```java
class Animal {

    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

Here:

```text
Animal → sound()
Dog    → sound()
```

The `Dog` provides its own implementation of `sound()`.

Therefore, this is **Method Overriding**.

---

# 2️⃣ Why Do We Use Method Overriding?

Method overriding allows a child class to provide **specific behavior** for a method inherited from its parent.

For example:

```text
Animal → sound()

Dog → Bark
Cat → Meow
Cow → Moo
```

All animals have:

```text
sound()
```

But each animal can implement it differently.

---

# 3️⃣ Basic Example

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

    public static void main(String[] args) {

        Dog d = new Dog();

        d.sound();
    }
}
```

### Output

```text
Bark
```

The `Dog` version of `sound()` is executed.

---

# 4️⃣ Runtime Polymorphism

Method overriding is an example of:

> **Runtime Polymorphism**

Example:

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

class Main {

    public static void main(String[] args) {

        Animal a = new Dog();

        a.sound();
    }
}
```

### Output

```text
Bark
```

---

# 5️⃣ Why Does `Bark` Execute?

Look at:

```java
Animal a = new Dog();
```

There are two important things:

```text
Animal → Reference Type
Dog    → Actual Object
```

When:

```java
a.sound();
```

is called, Java uses the **actual object type** at runtime.

Actual object:

```text
Dog
```

Therefore:

```text
Dog's sound() → Bark
```

### 🧠 Easy Memory

```text
Reference → Animal
Object    → Dog

Runtime → Dog's method
```

---

# 6️⃣ `@Override` Annotation

We commonly use:

```java
@Override
```

Example:

```java
class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

`@Override` tells the compiler:

> "I intend to override a parent class method."

It helps detect mistakes.

Example:

```java
class Dog extends Animal {

    @Override
    void sounds() {   // ❌ Different method name
    }
}
```

The compiler will report an error because `sounds()` does not override `sound()`.

---

# 7️⃣ Rules of Method Overriding

## Rule 1️⃣ Same Method Name

Parent:

```java
void sound()
```

Child:

```java
void sound()
```

---

## Rule 2️⃣ Same Parameters

Parent:

```java
void display(int x)
```

Child:

```java
void display(int x)
```

This is overriding.

But:

```java
void display(double x)
```

is **overloading**, not overriding.

---

## Rule 3️⃣ Requires Inheritance

Method overriding occurs between a parent and child class.

Example:

```java
class Dog extends Animal {
}
```

Without inheritance, it is not method overriding.

---

# 8️⃣ Return Type Rule

The child method must have the **same or a compatible return type**.

Example:

```java
class Animal {

    Animal getAnimal() {
        return new Animal();
    }
}

class Dog extends Animal {

    @Override
    Dog getAnimal() {
        return new Dog();
    }
}
```

This is valid because `Dog` is a subclass of `Animal`.

This is called a **covariant return type**.

### Simple Rule

```text
Same return type → ✅

Compatible/covariant return type → ✅

Unrelated return type → ❌
```

---

# 9️⃣ Access Modifier Rule

A child class cannot reduce the visibility of an overridden method.

Example:

```java
class Animal {

    public void sound() {
    }
}

class Dog extends Animal {

    public void sound() {
    }
}
```

✅ Valid.

But:

```java
class Animal {

    public void sound() {
    }
}

class Dog extends Animal {

    private void sound() {
    }
}
```

❌ Invalid.

### Easy Rule

```text
Parent: public
Child : public     ✅

Parent: protected
Child : protected  ✅
Child : public     ✅

Child cannot make access more restrictive.
```

---

# 🔟 Can We Override a `final` Method?

No.

```java
class Animal {

    final void sound() {
    }
}

class Dog extends Animal {

    void sound() {     // ❌
    }
}
```

A `final` method cannot be overridden.

### Memory

```text
final method
     ↓
Cannot Override
```

---

# 1️⃣1️⃣ Can We Override a `private` Method?

No.

Private methods are not accessible to child classes, so they cannot be overridden.

```java
class Animal {

    private void sound() {
    }
}

class Dog extends Animal {

    void sound() {
    }
}
```

This is **not overriding**.

The child method is simply a separate method.

---

# 1️⃣2️⃣ Can We Override a `static` Method?

Static methods are **not overridden**.

They are **hidden**.

Example:

```java
class Parent {

    static void display() {
        System.out.println("Parent");
    }
}

class Child extends Parent {

    static void display() {
        System.out.println("Child");
    }
}
```

This is called **method hiding**, not overriding.

### Important

```text
Instance method → Can be overridden

Static method → Hidden
```

---

# 1️⃣3️⃣ Can Constructors Be Overridden?

No.

Constructors are not inherited, so they cannot be overridden.

```text
Constructor → Cannot be overridden
```

But constructors **can be overloaded**.

---

# 1️⃣4️⃣ Using `super` with Overriding

Sometimes the child wants to call the parent's implementation.

We can use:

```java
super.method();
```

Example:

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

        System.out.println("Bark");
    }
}
```

### Output

```text
Animal sound
Bark
```

Here:

```java
super.sound();
```

calls the parent version.

---

# 1️⃣5️⃣ Real-World Example

Consider a payment system.

```text
Payment
   |
   ├── UPI
   ├── CreditCard
   └── NetBanking
```

Parent:

```java
class Payment {

    void pay() {
        System.out.println("Making payment");
    }
}
```

Child:

```java
class UPI extends Payment {

    @Override
    void pay() {
        System.out.println("Payment using UPI");
    }
}
```

Another child:

```java
class CreditCard extends Payment {

    @Override
    void pay() {
        System.out.println("Payment using Credit Card");
    }
}
```

Now:

```java
Payment p = new UPI();
p.pay();
```

Output:

```text
Payment using UPI
```

And:

```java
Payment p = new CreditCard();
p.pay();
```

Output:

```text
Payment using Credit Card
```

This is **runtime polymorphism**.

---

# 1️⃣6️⃣ Overloading vs Overriding

This is one of the **most important Java interview questions**.

| Method Overloading | Method Overriding |
|---|---|
| Same method name | Same method name |
| Different parameters | Same parameters |
| Usually same class | Parent-child classes |
| Inheritance not required | Inheritance required |
| Compile-time polymorphism | Runtime polymorphism |
| Return type alone cannot differentiate | Return type must be same/compatible |
| Example: `add(int,int)` and `add(int,int,int)` | Parent `sound()` → Child `sound()` |

### 🧠 Easy Memory

```text
OVERLOADING
     ↓
Different Parameters
     ↓
Compile Time


OVERRIDING
     ↓
Same Parameters
     ↓
Different Implementation
     ↓
Runtime
```

---

# 1️⃣7️⃣ Method Overriding Flow

```text
Parent Class
     |
     | defines
     ↓
sound()
     |
     ↓
Child Class
     |
     | overrides
     ↓
sound()
     |
     ↓
Runtime
     |
     ↓
Child implementation executes
```

---

# 🎯 Interview One-Liners

### What is Method Overriding?

> Method overriding occurs when a child class provides its own implementation of a method inherited from its parent class.

### What type of polymorphism is Method Overriding?

> Method overriding is runtime polymorphism.

### Is inheritance required for overriding?

> Yes, method overriding requires a parent-child relationship through inheritance.

### What is `@Override`?

> `@Override` is an annotation used to indicate that a child method is intended to override a parent method.

### Can a final method be overridden?

> No, a final method cannot be overridden.

### Can a private method be overridden?

> No, because private methods are not accessible to the child class.

### Can a static method be overridden?

> No. Static methods are hidden rather than overridden.

### Can constructors be overridden?

> No, constructors are not inherited and therefore cannot be overridden.

### Can constructors be overloaded?

> Yes, constructors can be overloaded.

### What is runtime polymorphism?

> Runtime polymorphism occurs when the method implementation is determined based on the actual object at runtime.

---

# 📝 Practice Questions

### Q1. Method Overriding represents:

A. Compile-time polymorphism  
B. Runtime polymorphism  
C. Encapsulation  
D. Abstraction

**Answer:** B

---

### Q2. Is inheritance required for method overriding?

A. Yes  
B. No

**Answer:** A

---

### Q3. Which annotation is commonly used for overriding?

A. `@Overload`  
B. `@Override`  
C. `@Method`  
D. `@Inherited`

**Answer:** B

---

### Q4. Can a final method be overridden?

A. Yes  
B. No

**Answer:** B

---

### Q5. Can a constructor be overridden?

A. Yes  
B. No

**Answer:** B

---

### Q6. What happens to static methods?

A. They are overridden  
B. They are hidden  
C. They are deleted  
D. They become abstract

**Answer:** B

---

# ⚡ Quick Revision

```text
Method Overriding
       ↓
Child class provides its own implementation
       ↓
Same method name
       +
Same parameter list
       ↓
Requires inheritance
       ↓
Runtime Polymorphism
```

### Important Rules

```text
Same method signature       → ✅
Inheritance required        → ✅
@return type compatible     → ✅
Access cannot be more strict → ✅
final method                → Cannot override
private method              → Cannot override
static method               → Hidden, not overridden
constructor                 → Cannot override
```

## ⭐ Key Point

> **Method Overriding = Child class gives a specific implementation of a parent method, resulting in runtime polymorphism.**
