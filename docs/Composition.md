# 📘 Java OOPs –  Composition 🧩

# 1️⃣ What is Composition?

**Composition** is a strong form of association where one object is strongly dependent on another object.

### Simple Definition

> **Composition = Strong HAS-A relationship where the part strongly depends on the whole.**

Example:

```text
House ───── has ───── Room
```

A room is considered a part of a particular house.

---

# 2️⃣ Real-World Example

Think about:

```text
House
  |
  |── Room
  |── Kitchen
  |── Bathroom
```

These are parts of the house.

In a composition model:

```text
House exists → Room exists as its part
House is removed → Room is also removed
```

Therefore, this is a **strong HAS-A relationship**.

---

# 3️⃣ Composition = Strong HAS-A

Remember:

```text
Composition
     ↓
Strong HAS-A
     ↓
Strong ownership
     ↓
Part depends on whole
```

Example:

```text
House HAS-A Room
Car HAS-A Engine
Order HAS-A OrderItem
```

The exact ownership semantics depend on how the application models the objects.

---

# 4️⃣ Composition in Java

Composition is commonly implemented by creating the dependent object **inside the containing class**.

Example:

```java
class Engine {

    void start() {
        System.out.println("Engine started");
    }
}

class Car {

    private Engine engine;

    Car() {
        engine = new Engine();
    }

    void drive() {
        engine.start();
        System.out.println("Car is moving");
    }

    public static void main(String[] args) {

        Car car = new Car();
        car.drive();
    }
}
```

### Output

```text
Engine started
Car is moving
```

Here:

```text
Car HAS-A Engine
```

The `Car` creates and manages its `Engine`.

---

# 5️⃣ Why is it called a Strong Relationship?

Consider:

```java
class Car {

    Engine engine = new Engine();
}
```

The `Engine` is created as part of the `Car`.

The `Car` controls the lifecycle of that `Engine` in this design.

Conceptually:

```text
Car
 |
 └── Engine
```

This represents strong ownership.

---

# 6️⃣ Composition vs Aggregation

This is **very important for interviews**.

| Aggregation | Composition |
|---|---|
| Weak HAS-A | Strong HAS-A |
| Weak ownership | Strong ownership |
| Part can exist independently | Part is strongly dependent on whole |
| Object can be supplied from outside | Object is commonly created/managed by the whole |
| Example: Department → Teacher | Example: House → Room |

### Easy Memory

```text
Aggregation → Weak HAS-A
Composition → Strong HAS-A
```

---

# 7️⃣ Simple Example

### Aggregation

```text
Department ─── Teacher
```

Teacher can exist without that department.

```text
Department ❌
Teacher    ✅
```

### Composition

```text
House ─── Room
```

In a strong composition model, the room is treated as a part of that particular house.

```text
House ❌
Room  ❌
```

---

# 8️⃣ Composition vs Inheritance

### Inheritance

```text
Dog IS-A Animal
```

Example:

```java
class Dog extends Animal {
}
```

### Composition

```text
Car HAS-A Engine
```

Example:

```java
class Car {
    Engine engine = new Engine();
}
```

### Memory Trick

```text
IS-A  → Inheritance
HAS-A → Composition / Aggregation
```

---

# 9️⃣ Another Real-World Example

Consider an `Order`.

```text
Order
 |
 ├── OrderItem
 ├── OrderItem
 └── OrderItem
```

An order contains order items.

In an application where `OrderItem` belongs specifically to that `Order`, this can be modeled using composition.

```java
class OrderItem {

    String product;

    OrderItem(String product) {
        this.product = product;
    }
}

class Order {

    private OrderItem item;

    Order() {
        item = new OrderItem("Laptop");
    }

    void display() {
        System.out.println(item.product);
    }
}
```

---

# 🔟 Important Java Point

Java does **not** have a special keyword called `composition`.

Composition is a **design concept**.

It is commonly implemented using:

```java
class A {
    B b = new B();
}
```

This means:

```text
A HAS-A B
```

with strong ownership when `A` controls the lifecycle of `B`.

---

# 1️⃣1️⃣ Composition and Encapsulation

Composition is often used together with encapsulation.

Example:

```java
class Car {

    private Engine engine;

    Car() {
        engine = new Engine();
    }
}
```

The `engine` is:

```text
private
```

So the outside code cannot directly manipulate the reference.

This helps the `Car` control its internal component.

---

# 🧠 Easy Memory Trick

Remember these three:

```text
Association
     ↓
General relationship

Aggregation
     ↓
Weak HAS-A
     ↓
Part can exist independently

Composition
     ↓
Strong HAS-A
     ↓
Strong ownership
```

---

# 🎯 Interview One-Liners

### What is Composition?

> Composition is a strong HAS-A relationship where one object strongly owns and manages another object.

### Give an example of Composition.

> A house containing rooms can be modeled as composition when the rooms are treated as parts owned by that particular house.

### What is the difference between Aggregation and Composition?

> Aggregation is a weak HAS-A relationship where the part can exist independently, while composition is a strong HAS-A relationship with stronger ownership and lifecycle dependency.

### Does Java have a composition keyword?

> No. Composition is a design concept implemented using object references.

### What is the difference between Composition and Inheritance?

> Composition represents a HAS-A relationship, while inheritance represents an IS-A relationship.

### Which is stronger: Aggregation or Composition?

> Composition represents stronger ownership than aggregation.

---

# 📝 Practice Questions

### Q1. Composition represents which relationship?

A. IS-A  
B. Weak HAS-A  
C. Strong HAS-A  
D. Method overriding

**Answer:** C

---

### Q2. Which is stronger?

A. Association  
B. Aggregation  
C. Composition  
D. Inheritance

**Answer:** C

---

### Q3. Which relationship represents IS-A?

A. Composition  
B. Aggregation  
C. Inheritance  
D. Association

**Answer:** C

---

### Q4. Which is commonly used to implement composition?

A. `extends`  
B. Object references  
C. `implements` only  
D. `static`

**Answer:** B

---

### Q5. What is the easiest way to remember composition?

A. IS-A  
B. Strong HAS-A  
C. Compile-time polymorphism  
D. Data hiding

**Answer:** B

---

# ⚡ Quick Revision

```text
Composition
     ↓
Strong HAS-A
     ↓
Strong ownership
     ↓
Part strongly depends on whole

Example:
House → Room
Order → OrderItem

Aggregation:
Weak HAS-A
Part can exist independently

Composition:
Strong HAS-A
Strong ownership

Inheritance:
IS-A
```

## ⭐ Key Point

> **Composition = Strong HAS-A relationship where the whole strongly owns and manages the part.**
