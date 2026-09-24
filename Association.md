# 📘 Java OOPs – 17. Association 🤝

## 🎯 What You Will Learn

- What is Association?
- Real-world example
- Association in Java
- Types of Association
- One-to-One
- One-to-Many
- Many-to-Many
- Association vs Inheritance
- Association vs Aggregation vs Composition
- Interview questions

---

# 1️⃣ What is Association?

**Association** represents a relationship between two independent classes/objects.

### Simple Definition

> **Association = Relationship between two independent objects.**

Example:

```text
Teacher ───── teaches ───── Student
```

A teacher can teach a student, and both can exist independently.

---

# 2️⃣ Real-World Example

Think about:

```text
Doctor ───── treats ───── Patient
```

The doctor and patient are two separate entities.

If the doctor no longer exists in the system, the patient can still exist.

Similarly, the patient can exist without that particular doctor.

This is an **Association**.

---

# 3️⃣ Association in Java

Association can be represented by one class having a reference to another class.

Example:

```java
class Teacher {

    void teach() {
        System.out.println("Teacher is teaching");
    }
}

class Student {

    void learn(Teacher teacher) {
        teacher.teach();
    }
}
```

Here:

```text
Student → Teacher
```

The `Student` interacts with the `Teacher`.

Both classes can exist independently.

---

# 4️⃣ Simple Example

```java
class Teacher {

    String name;

    Teacher(String name) {
        this.name = name;
    }
}

class Student {

    String name;

    Student(String name) {
        this.name = name;
    }

    void showTeacher(Teacher teacher) {
        System.out.println(
            name + " is learning from " + teacher.name
        );
    }

    public static void main(String[] args) {

        Teacher t = new Teacher("Ravi");
        Student s = new Student("Dharun");

        s.showTeacher(t);
    }
}
```

### Output

```text
Dharun is learning from Ravi
```

Here:

```text
Student ───── learns from ───── Teacher
```

This is an association.

---

# 5️⃣ Important Point

In Association:

```text
Object A
   ↕
Object B
```

Both objects can exist independently.

Example:

```text
Teacher
   ↕
Student
```

The teacher doesn't own the student.

The student doesn't own the teacher.

They simply have a relationship.

---

# 6️⃣ Types of Association

Association can be described based on how many objects participate in the relationship.

### 1️⃣ One-to-One

```text
Person ───── Passport
```

One person has one passport.

---

### 2️⃣ One-to-Many

```text
Teacher
   |
   |──── Student
   |──── Student
   |──── Student
```

One teacher can teach many students.

---

### 3️⃣ Many-to-One

```text
Student ──┐
Student ──┼── Teacher
Student ──┘
```

Many students can be taught by one teacher.

---

### 4️⃣ Many-to-Many

```text
Student ───── Course
   ↕             ↕
Multiple      Multiple
```

A student can enroll in multiple courses, and a course can have multiple students.

---

# 7️⃣ Association vs Inheritance

This is important.

### Inheritance

Represents:

```text
IS-A
```

Example:

```text
Dog IS-A Animal
```

Java:

```java
class Dog extends Animal {
}
```

### Association

Represents a relationship such as:

```text
USES
WORKS WITH
KNOWS
TEACHES
```

Example:

```text
Teacher teaches Student
```

### Memory Trick

```text
Inheritance → IS-A

Association → HAS-A / USES / RELATIONSHIP
```

---

# 8️⃣ Association vs Aggregation vs Composition

These three are related to object relationships.

| Association | Aggregation | Composition |
|---|---|---|
| General relationship | Weak HAS-A relationship | Strong HAS-A relationship |
| Objects are independent | Objects can exist independently | Part usually depends on whole |
| No ownership implied | Weak ownership | Strong ownership |
| Teacher ↔ Student | Department ↔ Teacher | House ↔ Room |

### Easy Memory

```text
Association
    ↓
General relationship

Aggregation
    ↓
Weak HAS-A

Composition
    ↓
Strong HAS-A
```

---

# 9️⃣ Real-World Comparison

### Association

```text
Teacher ↔ Student
```

Both can exist independently.

### Aggregation

```text
Department ◇──── Teacher
```

A department has teachers, but teachers can exist independently of that department.

### Composition

```text
House ◆──── Room
```

A room is treated as a strongly owned part of the house in the model.

---

# 🔟 Association Does Not Mean Ownership

This is an important point.

If:

```text
Teacher ───── Student
```

it does not necessarily mean:

```text
Teacher owns Student
```

It simply means there is a relationship between them.

---

# 1️⃣1️⃣ Association Through Method Parameter

One simple way to represent association:

```java
class Student {

    void studyWith(Teacher teacher) {
        teacher.teach();
    }
}
```

Here `Student` interacts with a `Teacher`.

The teacher object is passed into the method.

---

# 1️⃣2️⃣ Association Through Instance Variable

Association can also be represented using a reference variable.

```java
class Engine {

    void start() {
        System.out.println("Engine started");
    }
}

class Driver {

    Engine engine;

    Driver(Engine engine) {
        this.engine = engine;
    }

    void drive() {
        engine.start();
        System.out.println("Driver is driving");
    }
}
```

Here:

```text
Driver ───── uses ───── Engine
```

The `Driver` has a reference to an `Engine`.

---

# 🧠 Easy Memory Trick

Remember:

```text
Association
      ↓
Relationship
      ↓
Independent Objects
```

Examples:

```text
Teacher ↔ Student
Doctor ↔ Patient
Driver ↔ Car
Customer ↔ Bank
```

---

# 🎯 Interview One-Liners

### What is Association?

> Association is a relationship between two independent classes or objects.

### Give an example of Association.

> A teacher and student have an association because a teacher teaches a student, while both can exist independently.

### What is the difference between Association and Inheritance?

> Inheritance represents an IS-A relationship, while association represents a general relationship between objects.

### What are common types of Association?

> One-to-one, one-to-many, many-to-one, and many-to-many.

### Does Association imply ownership?

> No. Association represents a relationship but does not necessarily imply ownership.

### Is Association important for a fresher?

> Yes, but only the basic concept and its difference from aggregation and composition are usually enough.

---

# 📝 Practice Questions

### Q1. What does Association represent?

A. Inheritance  
B. Relationship between objects  
C. Data hiding  
D. Method overriding

**Answer:** B

---

### Q2. Which relationship represents IS-A?

A. Association  
B. Inheritance  
C. Aggregation  
D. Composition

**Answer:** B

---

### Q3. Which is an example of Association?

A. Dog IS-A Animal  
B. Teacher teaches Student  
C. Class extends Object  
D. Method overriding

**Answer:** B

---

### Q4. Does Association necessarily mean ownership?

A. Yes  
B. No

**Answer:** B

---

### Q5. One teacher teaching many students is:

A. One-to-One  
B. One-to-Many  
C. Many-to-One  
D. Many-to-Many

**Answer:** B

---

# ⚡ Quick Revision

```text
Association
     ↓
General relationship
     ↓
Between independent objects
     ↓
Examples:
Teacher ↔ Student
Doctor ↔ Patient
Driver ↔ Car

Types:
1. One-to-One
2. One-to-Many
3. Many-to-One
4. Many-to-Many

Inheritance → IS-A
Association → Relationship
Aggregation → Weak HAS-A
Composition → Strong HAS-A
```

## ⭐ Key Point

> **Association is a general relationship between two independent objects. For fresher interviews, understand its basic meaning and how it differs from aggregation and composition.**
