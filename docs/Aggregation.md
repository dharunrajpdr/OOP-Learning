# 📘 Java OOPs – 18. Aggregation 🔗

## 🎯 What You Will Learn

- What is Aggregation?
- HAS-A relationship
- Real-world example
- Aggregation in Java
- Aggregation vs Association
- Aggregation vs Composition
- Interview questions

---

# 1️⃣ What is Aggregation?

**Aggregation** is a special type of association that represents a **HAS-A relationship** where the two objects can exist independently.

### Simple Definition

> **Aggregation = Weak HAS-A relationship between two independent objects.**

Example:

```text
Department ───── has ───── Teacher
```

A department has teachers.

But if the department is removed, the teacher can still exist.

---

# 2️⃣ Real-World Example

Consider:

```text
Department
    |
    |── Teacher
    |── Teacher
    |── Teacher
```

A `Department` contains `Teacher` objects.

But:

```text
Department can be removed
        ↓
Teacher can still exist
```

Therefore, this is **Aggregation**.

---

# 3️⃣ Aggregation = HAS-A

Whenever you see:

```text
HAS-A
```

think about aggregation or composition.

Example:

```text
Department HAS-A Teacher
Library HAS-A Book
Team HAS-A Player
```

For aggregation:

```text
Whole HAS-A Part
```

but the **part can exist independently**.

---

# 4️⃣ Aggregation in Java

Aggregation can be represented by having an object of another class as a member.

Example:

```java
class Teacher {

    String name;

    Teacher(String name) {
        this.name = name;
    }
}

class Department {

    String departmentName;
    Teacher teacher;

    Department(String departmentName, Teacher teacher) {
        this.departmentName = departmentName;
        this.teacher = teacher;
    }

    void display() {
        System.out.println("Department: " + departmentName);
        System.out.println("Teacher: " + teacher.name);
    }

    public static void main(String[] args) {

        Teacher t = new Teacher("Ravi");

        Department d = new Department("CSE", t);

        d.display();
    }
}
```

### Output

```text
Department: CSE
Teacher: Ravi
```

Here:

```text
Department HAS-A Teacher
```

This is aggregation.

---

# 5️⃣ Why is it called Weak Relationship?

Because the objects can exist separately.

```text
Teacher
   ↑
   |
Department
```

If the `Department` object is destroyed:

```text
Department ❌
Teacher     ✅
```

The teacher can still exist.

That's why aggregation is called a **weak HAS-A relationship**.

---

# 6️⃣ Important Example

Consider:

```text
Team ───── Player
```

A team has players.

But if the team is dissolved:

```text
Team ❌
Player ✅
```

The player can join another team.

Therefore:

```text
Team HAS-A Player
```

This can be modeled using aggregation.

---

# 7️⃣ Aggregation vs Association

Aggregation is actually a more specific form of association.

```text
Association
     ↓
General relationship

Aggregation
     ↓
Specific HAS-A relationship
     ↓
Independent objects
```

### Example

Association:

```text
Teacher ↔ Student
```

Aggregation:

```text
Department ── HAS-A ── Teacher
```

---

# 8️⃣ Aggregation vs Composition

This is one of the most common interview questions.

| Aggregation | Composition |
|---|---|
| Weak HAS-A | Strong HAS-A |
| Part can exist independently | Part is strongly dependent on whole |
| Weak ownership | Strong ownership |
| Example: Team → Player | Example: House → Room |
| Part can be shared/reassigned | Part normally belongs to one whole |

### Easy Memory

```text
Aggregation
    ↓
Weak HAS-A
    ↓
Part can survive

Composition
    ↓
Strong HAS-A
    ↓
Part depends on whole
```

---

# 9️⃣ Simple Example to Remember

### Aggregation

```text
University ─── Student
```

If the university object is removed from the application:

```text
University ❌
Student    ✅
```

The student can still exist.

### Composition

```text
House ─── Room
```

In a strong composition model:

```text
House ❌
Room ❌
```

The room is treated as a part of that particular house.

---

# 🔟 Aggregation in Java — Important Point

Java does **not** have a special keyword called `aggregation`.

We represent aggregation using **object references**.

Example:

```java
class Engine {
}

class Car {

    Engine engine;

    Car(Engine engine) {
        this.engine = engine;
    }
}
```

Here:

```text
Car HAS-A Engine
```

The `Engine` object can be created separately and passed to the `Car`.

---

# 1️⃣1️⃣ Aggregation Using a List

A common real-world example:

```java
import java.util.*;

class Employee {

    String name;

    Employee(String name) {
        this.name = name;
    }
}

class Department {

    List<Employee> employees;

    Department(List<Employee> employees) {
        this.employees = employees;
    }
}
```

Here:

```text
Department HAS-A Employees
```

The employees can exist independently of the department.

---

# 1️⃣2️⃣ Aggregation vs Inheritance

### Inheritance

```text
Dog IS-A Animal
```

Uses:

```java
class Dog extends Animal {
}
```

### Aggregation

```text
Car HAS-A Engine
```

Uses an object reference:

```java
class Car {
    Engine engine;
}
```

### Memory Trick

```text
IS-A  → Inheritance

HAS-A → Aggregation / Composition
```

---

# 🧠 Easy Memory Trick

Remember:

```text
Aggregation
     ↓
HAS-A
     ↓
Weak ownership
     ↓
Objects can exist independently
```

Example:

```text
Team → Player
Department → Teacher
University → Student
Library → Book
```

---

# 🎯 Interview One-Liners

### What is Aggregation?

> Aggregation is a weak HAS-A relationship where the contained object can exist independently of the container object.

### Give an example of Aggregation.

> A department has teachers, but teachers can exist independently of the department.

### Is Aggregation a type of Association?

> Yes. Aggregation is a specialized form of association representing a HAS-A relationship.

### Does Java have an aggregation keyword?

> No. Aggregation is represented using object references.

### What is the difference between Aggregation and Composition?

> Aggregation represents a weak HAS-A relationship where the part can exist independently, while composition represents a strong HAS-A relationship where the part is strongly dependent on the whole.

### What is the difference between Inheritance and Aggregation?

> Inheritance represents an IS-A relationship, while aggregation represents a HAS-A relationship.

---

# 📝 Practice Questions

### Q1. Aggregation represents which relationship?

A. IS-A  
B. HAS-A  
C. IS-AN  
D. Overrides

**Answer:** B

---

### Q2. In aggregation, can the part exist independently?

A. Yes  
B. No

**Answer:** A

---

### Q3. Which is an example of aggregation?

A. Dog IS-A Animal  
B. Department HAS-A Teacher  
C. Dog extends Animal  
D. Method overriding

**Answer:** B

---

### Q4. Aggregation is considered:

A. Strong HAS-A  
B. Weak HAS-A  
C. IS-A  
D. Compile-time polymorphism

**Answer:** B

---

### Q5. Which is represented using `extends`?

A. Aggregation  
B. Composition  
C. Inheritance  
D. Association

**Answer:** C

---

# ⚡ Quick Revision

```text
Aggregation
     ↓
Special type of Association
     ↓
HAS-A relationship
     ↓
Weak ownership
     ↓
Part can exist independently

Examples:
Department → Teacher
Team → Player
University → Student
Library → Book

Inheritance → IS-A
Aggregation → Weak HAS-A
Composition → Strong HAS-A
```

## ⭐ Key Point

> **Aggregation = Weak HAS-A relationship where the contained object can exist independently.**
