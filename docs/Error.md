# 📘 Java – Types of Errors

## 1. What is an Error?

An **error** is a problem in a program that prevents the program from working correctly.

In Java, errors can broadly be understood as:

1. Compile-Time Errors
2. Runtime Errors

> ⚠️ In Java's technical hierarchy, `Error` is also a specific class under `Throwable`. Runtime problems are commonly represented by `Exception` or `Error`.

---

# 2. Compile-Time Error

A **compile-time error** occurs when the Java compiler finds a problem **before the program runs**.

### Common Causes

- Syntax error
- Missing semicolon
- Undeclared variable
- Wrong data type
- Incorrect method usage

### Example

```java
public class Main {
    public static void main(String[] args) {

        int a = 10
        System.out.println(a);

    }
}
```

### Error

```text
';' expected
```

The program will not run until the error is fixed.

---

# 3. Runtime Error

A **runtime error** occurs **while the program is executing**.

The program may compile successfully, but a problem occurs during execution.

### Example

```java
public class Main {
    public static void main(String[] args) {

        int a = 10;
        int b = 0;

        System.out.println(a / b);

    }
}
```

### Output

```text
ArithmeticException: / by zero
```

The program compiles successfully but fails during execution.

---

# 4. Compile-Time vs Runtime Error

| Compile-Time Error | Runtime Error |
|---|---|
| Occurs during compilation | Occurs during execution |
| Detected by compiler | Occurs while program is running |
| Program cannot run until fixed | Program may start but fail during execution |
| Example: missing `;` | Example: divide by zero |
| Often related to syntax/type problems | Often caused by exceptions or runtime conditions |

---

# 5. Examples of Common Runtime Problems

### ArithmeticException

```java
int result = 10 / 0;
```

---

### NullPointerException

```java
String name = null;

System.out.println(name.length());
```

---

### ArrayIndexOutOfBoundsException

```java
int[] arr = {10, 20, 30};

System.out.println(arr[5]);
```

---

### NumberFormatException

```java
String str = "abc";

int num = Integer.parseInt(str);
```

---

# 6. Java Throwable Hierarchy

Java represents serious problems and exceptions using the `Throwable` hierarchy.

```text
Throwable
│
├── Error
│   ├── StackOverflowError
│   └── OutOfMemoryError
│
└── Exception
    ├── Checked Exceptions
    │   ├── IOException
    │   └── SQLException
    │
    └── RuntimeException
        ├── ArithmeticException
        ├── NullPointerException
        ├── ArrayIndexOutOfBoundsException
        └── NumberFormatException
```

---

# 7. Error vs Exception

| Error | Exception |
|---|---|
| Usually serious JVM/system-level problem | Usually a condition that application code can handle |
| Generally not meant to be handled | Can often be handled |
| Example: `OutOfMemoryError` | Example: `IOException` |
| Example: `StackOverflowError` | Example: `NullPointerException` |

### Important

```text
Error     → Serious problem
Exception → Problem that can often be handled
```

---

# 8. Compile-Time Error Example

```java
public class Main {
    public static void main(String[] args) {

        int number = "Hello";

    }
}
```

### Error

```text
incompatible types
```

A `String` cannot be directly assigned to an `int`.

---

# 9. Runtime Error Example

```java
public class Main {
    public static void main(String[] args) {

        int[] numbers = {10, 20, 30};

        System.out.println(numbers[10]);

    }
}
```

### Output

```text
ArrayIndexOutOfBoundsException
```

---

# 10. Easy Memory Trick

```text
Compile-Time
     ↓
Before Program Runs
     ↓
Compiler Finds Problem


Runtime
     ↓
Program Is Running
     ↓
Problem Occurs
```

---

# 11. Interview One-Liners

### What is a compile-time error?

> A compile-time error is an error detected by the compiler before program execution.

### What is a runtime error?

> A runtime error occurs while the program is executing.

### Give an example of a compile-time error.

> Missing semicolon or incompatible data type.

### Give an example of a runtime error.

> Dividing a number by zero causes `ArithmeticException`.

### What is the difference between Error and Exception?

> `Error` usually represents serious JVM-level problems, while `Exception` represents conditions that application code can often handle.

---

# 12. Quick Revision

```text
Compile-Time Error
→ Found by compiler
→ Before execution
→ Example: missing ;

Runtime Error
→ Occurs during execution
→ Example: ArithmeticException

Error
→ Serious JVM-level problem
→ Example: OutOfMemoryError

Exception
→ Usually handleable application problem
→ Example: IOException
```

# ⭐ Key Point

> **Compile-time error → Before running**
>
> **Runtime error → During running**
>
> **Error → Serious JVM-level problem**
>
> **Exception → Usually handleable problem**
