# 📘 Java Exception Handling – Complete Learning Order

> Beginner-friendly Java Exception Handling notes for learning and fresher interviews.

---

# 📚 Exception Handling Learning Order

```text
1.  What is Exception Handling?
        ↓
2.  Types of Exceptions
        ↓
3.  try-catch
        ↓
4.  Multiple catch
        ↓
5.  finally
        ↓
6.  throw
        ↓
7.  throws
        ↓
8.  throw vs throws
        ↓
9.  Checked vs Unchecked Exceptions
        ↓
10. Custom Exceptions
        ↓
11. Exception Hierarchy
        ↓
12. try-with-resources
        ↓
13. Common Interview Questions
```

---

# 1️⃣ What is Exception Handling?

## 📌 Definition

An **exception** is an unexpected event that occurs during program execution and can interrupt the normal flow of the program.

### Example

```java
int a = 10;
int b = 0;

System.out.println(a / b);
```

This causes:

```text
ArithmeticException
```

Without exception handling, the program may terminate abnormally.

### 🧠 Easy Memory

```text
Exception
    ↓
Unexpected problem during execution
    ↓
Can disturb normal program flow
```

---

# 2️⃣ Why Do We Need Exception Handling?

Consider:

```java
int a = 10;
int b = 0;

System.out.println(a / b);

System.out.println("Hello");
```

The second statement may not execute because the exception interrupts the normal flow.

Using exception handling:

```java
try {
    System.out.println(a / b);
}
catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}

System.out.println("Hello");
```

Output:

```text
Cannot divide by zero
Hello
```

### Benefits

```text
✔ Prevent abnormal program termination
✔ Handle runtime problems
✔ Maintain normal program flow
✔ Display meaningful error messages
✔ Separate error-handling code from normal code
```

---

# 3️⃣ Types of Exceptions

Java exceptions are broadly classified into:

```text
Exceptions
   |
   ├── Checked Exceptions
   |
   └── Unchecked Exceptions
```

There are also serious problems represented by `Error`.

```text
Throwable
   |
   ├── Error
   |
   └── Exception
```

---

# 4️⃣ Checked Exceptions

Checked exceptions are checked by the compiler.

The programmer must handle them or declare them using `throws`.

Examples:

```text
IOException
SQLException
FileNotFoundException
```

Example:

```java
import java.io.*;

class Main {

    public static void main(String[] args) {

        try {
            FileReader file = new FileReader("data.txt");
        }
        catch (FileNotFoundException e) {
            System.out.println("File not found");
        }
    }
}
```

### 🧠 Easy Memory

```text
Checked Exception
      ↓
Compiler checks it
```

---

# 5️⃣ Unchecked Exceptions

Unchecked exceptions are generally detected during runtime.

They are subclasses of `RuntimeException`.

Examples:

```text
ArithmeticException
NullPointerException
ArrayIndexOutOfBoundsException
NumberFormatException
```

Example:

```java
int a = 10;
int b = 0;

System.out.println(a / b);
```

Result:

```text
ArithmeticException
```

### 🧠 Easy Memory

```text
Unchecked Exception
      ↓
Runtime
      ↓
RuntimeException
```

---

# 6️⃣ try-catch

## 📌 Syntax

```java
try {
    // risky code
}
catch (ExceptionType e) {
    // handling code
}
```

### Example

```java
class Main {

    public static void main(String[] args) {

        try {
            int result = 10 / 0;
            System.out.println(result);
        }
        catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
    }
}
```

### Output

```text
Cannot divide by zero
```

---

# 7️⃣ How try-catch Works

```text
try
 ↓
Execute risky code
 ↓
Exception occurs?
 ↓
Yes
 ↓
catch executes
 ↓
Program continues
```

If no exception occurs:

```text
try
 ↓
No exception
 ↓
catch is skipped
 ↓
Continue
```

---

# 8️⃣ Multiple catch Blocks

We can use multiple `catch` blocks to handle different exceptions.

Example:

```java
class Main {

    public static void main(String[] args) {

        try {

            int[] arr = {10, 20, 30};

            System.out.println(arr[5]);

        }
        catch (ArithmeticException e) {

            System.out.println("Arithmetic error");

        }
        catch (ArrayIndexOutOfBoundsException e) {

            System.out.println("Invalid array index");
        }
    }
}
```

### Output

```text
Invalid array index
```

---

# 9️⃣ Important Rule for Multiple catch

Specific exceptions should generally come before their broader parent exception.

Correct:

```java
try {
}
catch (ArithmeticException e) {
}
catch (Exception e) {
}
```

Incorrect:

```java
try {
}
catch (Exception e) {
}
catch (ArithmeticException e) {
}
```

Why?

Because:

```text
Exception
   ↓
is parent of
   ↓
ArithmeticException
```

The first `catch` would already catch the child exception.

---

# 🔟 finally

## 📌 Definition

`finally` is a block that is generally used for cleanup code.

It normally executes whether an exception occurs or not.

### Syntax

```java
try {
    // risky code
}
catch (Exception e) {
    // handling
}
finally {
    // cleanup
}
```

### Example

```java
class Main {

    public static void main(String[] args) {

        try {
            int result = 10 / 0;
        }
        catch (ArithmeticException e) {
            System.out.println("Error occurred");
        }
        finally {
            System.out.println("Finally executed");
        }
    }
}
```

### Output

```text
Error occurred
Finally executed
```

### Common Use

```text
Close files
Close database resources
Release resources
Cleanup operations
```

---

# 1️⃣1️⃣ try-catch-finally

```java
try {

    // risky code

}
catch (Exception e) {

    // handle exception

}
finally {

    // cleanup code

}
```

### Flow

```text
          try
           |
      Exception?
       /       \
     Yes        No
      |          |
    catch        |
       \         /
        finally
           |
        Continue
```

---

# 1️⃣2️⃣ throw

## 📌 Definition

`throw` is used to **explicitly throw an exception**.

### Syntax

```java
throw new ExceptionType();
```

Example:

```java
class Main {

    public static void main(String[] args) {

        int age = 15;

        if (age < 18) {
            throw new ArithmeticException("Not eligible");
        }

        System.out.println("Eligible");
    }
}
```

Output:

```text
Exception in thread "main" java.lang.ArithmeticException: Not eligible
```

### 🧠 Easy Memory

```text
throw
   ↓
Actually throws an exception
```

---

# 1️⃣3️⃣ throws

## 📌 Definition

`throws` is used in a method declaration to indicate that the method may pass an exception to its caller.

### Syntax

```java
returnType methodName() throws ExceptionType {
}
```

Example:

```java
import java.io.*;

class Main {

    static void readFile() throws FileNotFoundException {

        FileReader file = new FileReader("data.txt");
    }

    public static void main(String[] args) {

        try {
            readFile();
        }
        catch (FileNotFoundException e) {
            System.out.println("File not found");
        }
    }
}
```

### 🧠 Easy Memory

```text
throws
   ↓
Declares possible exception
```

---

# 1️⃣4️⃣ throw vs throws

| `throw` | `throws` |
|---|---|
| Used to actually throw an exception | Used to declare possible exceptions |
| Used inside method/block | Used in method declaration |
| Throws one exception object at a time | Can declare multiple exception types |
| Example: `throw new Exception()` | Example: `method() throws Exception` |

### 🧠 Easy Memory

```text
throw  → Throw it

throws → Declare it
```

---

# 1️⃣5️⃣ Checked vs Unchecked Exceptions

| Checked | Unchecked |
|---|---|
| Checked by compiler | Occur/detected during runtime |
| Must be handled or declared | No mandatory handling requirement |
| Usually subclasses of `Exception` excluding `RuntimeException` | Subclasses of `RuntimeException` |
| IOException | ArithmeticException |
| SQLException | NullPointerException |
| FileNotFoundException | ArrayIndexOutOfBoundsException |

### 🧠 Easy Memory

```text
Checked
   ↓
Compiler checks

Unchecked
   ↓
Runtime
```

---

# 1️⃣6️⃣ Custom Exceptions

Sometimes built-in exceptions are not enough.

We can create our own exception class.

### Example

```java
class InvalidAgeException extends Exception {

    InvalidAgeException(String message) {
        super(message);
    }
}
```

Use it:

```java
class Main {

    static void checkAge(int age)
            throws InvalidAgeException {

        if (age < 18) {
            throw new InvalidAgeException(
                "Age must be 18 or above"
            );
        }

        System.out.println("Eligible");
    }

    public static void main(String[] args) {

        try {
            checkAge(15);
        }
        catch (InvalidAgeException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

### Output

```text
Age must be 18 or above
```

### 🧠 Easy Memory

```text
Custom Exception
       ↓
Our own exception class
```

---

# 1️⃣7️⃣ Exception Hierarchy

Java exception hierarchy starts from:

```text
Object
   ↓
Throwable
   ├── Error
   │
   └── Exception
        ├── RuntimeException
        │      ├── ArithmeticException
        │      ├── NullPointerException
        │      ├── ArrayIndexOutOfBoundsException
        │      └── NumberFormatException
        │
        ├── IOException
        ├── SQLException
        └── Other Checked Exceptions
```

---

# 1️⃣8️⃣ Error vs Exception

## Error

Errors usually represent serious problems that applications generally should not try to handle as normal application exceptions.

Examples:

```text
OutOfMemoryError
StackOverflowError
```

## Exception

Exceptions represent conditions that applications can often handle.

Examples:

```text
IOException
SQLException
ArithmeticException
NullPointerException
```

### 🧠 Easy Memory

```text
Error     → Serious system/JVM problem
Exception → Usually application-level problem
```

---

# 1️⃣9️⃣ try-with-resources

`try-with-resources` is used to automatically close resources that implement `AutoCloseable`.

Common resources:

```text
Files
Streams
Database connections
Readers
```

Example:

```java
import java.io.*;

class Main {

    public static void main(String[] args) {

        try (FileReader file =
                 new FileReader("data.txt")) {

            System.out.println("File opened");

        }
        catch (IOException e) {

            System.out.println("File error");
        }
    }
}
```

The resource is automatically closed after the `try` block.

### 🧠 Easy Memory

```text
try-with-resources
        ↓
Use resource
        ↓
Automatically close resource
```

---

# 2️⃣0️⃣ Common Exception Methods

An exception object provides useful methods.

### `getMessage()`

Returns the exception message.

```java
catch (Exception e) {
    System.out.println(e.getMessage());
}
```

### `printStackTrace()`

Prints information about where the exception occurred.

```java
catch (Exception e) {
    e.printStackTrace();
}
```

### `toString()`

Returns exception class name and message.

```java
catch (Exception e) {
    System.out.println(e.toString());
}
```

---

# 2️⃣1️⃣ Nested try

A `try` block can exist inside another `try` block.

```java
try {

    try {
        int x = 10 / 0;
    }
    catch (ArithmeticException e) {
        System.out.println("Inner catch");
    }

}
catch (Exception e) {

    System.out.println("Outer catch");
}
```

Output:

```text
Inner catch
```

---

# 2️⃣2️⃣ Can We Have try Without catch?

Yes, if it is followed by `finally`.

```java
try {
    System.out.println("Hello");
}
finally {
    System.out.println("Finally");
}
```

Output:

```text
Hello
Finally
```

But this is invalid:

```java
try {
    System.out.println("Hello");
}
```

A `try` must be followed by at least:

```text
catch
OR
finally
```

---

# 2️⃣3️⃣ Can We Have catch Without try?

No.

This is invalid:

```java
catch (Exception e) {
}
```

A `catch` must always be associated with a `try`.

---

# 2️⃣4️⃣ Common Exceptions You Should Know

| Exception | Example |
|---|---|
| `ArithmeticException` | Division by zero |
| `NullPointerException` | Using a null reference |
| `ArrayIndexOutOfBoundsException` | Invalid array index |
| `NumberFormatException` | Invalid string-to-number conversion |
| `StringIndexOutOfBoundsException` | Invalid string index |
| `ClassCastException` | Invalid object casting |
| `IOException` | Input/output problem |
| `FileNotFoundException` | File does not exist |
| `SQLException` | Database-related problem |

---

# 🧠 Complete Exception Handling Flow

```text
                Exception Handling
                       |
          ┌────────────┴────────────┐
          ↓                         ↓
      try-catch                  finally
          |
     Multiple catch
          |
    ┌─────┴─────┐
    ↓           ↓
  throw       throws
    |
Custom Exception
    |
Checked / Unchecked
    |
Exception Hierarchy
    |
try-with-resources
```

---

# 🎯 Most Important Topics for Freshers

## ⭐ High Priority

```text
1. Exception Handling basics
2. try-catch
3. Multiple catch
4. finally
5. throw
6. throws
7. throw vs throws
8. Checked vs Unchecked
9. Common Exceptions
10. Custom Exceptions
11. Exception Hierarchy
12. try-with-resources
13. Exception methods
14. Nested try
```

---

# 🎤 Common Interview Questions

### Q1. What is an exception?

> An exception is an unexpected event during program execution that can disrupt the normal flow of the program.

---

### Q2. What is exception handling?

> Exception handling is a mechanism used to handle runtime problems and maintain the normal flow of a program.

---

### Q3. What is the purpose of try-catch?

> `try` contains risky code and `catch` handles the exception if it occurs.

---

### Q4. What is finally?

> `finally` is a block generally used for cleanup code and normally executes whether an exception occurs or not.

---

### Q5. What is the difference between throw and throws?

> `throw` is used to explicitly throw an exception, while `throws` is used to declare exceptions that a method may pass to its caller.

---

### Q6. What is a checked exception?

> A checked exception is an exception that the compiler requires the program to handle or declare.

---

### Q7. What is an unchecked exception?

> An unchecked exception is a runtime exception that does not have a compile-time handling requirement.

---

### Q8. Can we have multiple catch blocks?

> Yes, we can use multiple catch blocks to handle different exception types.

---

### Q9. Can we have try without catch?

> Yes, a `try` can be followed by `finally` without a `catch`.

---

### Q10. Can we have catch without try?

> No, a `catch` must always be associated with a `try`.

---

### Q11. What is a custom exception?

> A custom exception is a user-defined exception class created for application-specific error conditions.

---

### Q12. What is try-with-resources?

> It is a feature that automatically closes resources implementing `AutoCloseable` after use.

---

# 📝 Practice Questions

### Q1. Which block contains code that may cause an exception?

A. `catch`  
B. `try`  
C. `finally`  
D. `throws`

**Answer:** B

---

### Q2. Which block handles an exception?

A. `try`  
B. `catch`  
C. `finally`  
D. `throw`

**Answer:** B

---

### Q3. Which keyword explicitly throws an exception?

A. `throws`  
B. `throw`  
C. `throwsException`  
D. `catch`

**Answer:** B

---

### Q4. Which keyword declares an exception?

A. `throw`  
B. `throws`  
C. `catch`  
D. `final`

**Answer:** B

---

### Q5. Which exception occurs when dividing an integer by zero?

A. `NullPointerException`  
B. `ArithmeticException`  
C. `IOException`  
D. `SQLException`

**Answer:** B

---

### Q6. Which is an unchecked exception?

A. `IOException`  
B. `SQLException`  
C. `ArithmeticException`  
D. `FileNotFoundException`

**Answer:** C

---

### Q7. Which block is generally used for cleanup?

A. `try`  
B. `catch`  
C. `finally`  
D. `throw`

**Answer:** C

---

### Q8. Can constructors throw exceptions?

A. Yes  
B. No

**Answer:** A

---

# ⚡ Quick Revision

```text
Exception
   ↓
Unexpected problem during execution

try
   ↓
Risky code

catch
   ↓
Handles exception

finally
   ↓
Cleanup code

throw
   ↓
Explicitly throws exception

throws
   ↓
Declares possible exception

Checked
   ↓
Compiler checks

Unchecked
   ↓
RuntimeException

Custom Exception
   ↓
User-defined exception

try-with-resources
   ↓
Automatically closes resources
```

---

# ⭐ Super Easy Memory Trick

```text
try     → Try this code
catch   → Catch the problem
finally → Finally clean up
throw   → Throw the problem
throws  → Tell others about the problem
```

---

# 🎯 Interview Priority

```text
                    Exception Handling
                           |
              ┌────────────┴────────────┐
              ↓                         ↓
          Must Know                 Good to Know
              |                         |
        try-catch                  Exception Hierarchy
        finally                    Nested try
        throw                      Exception methods
        throws
        Checked/Unchecked
        Custom Exception
        Common Exceptions
        try-with-resources
```
