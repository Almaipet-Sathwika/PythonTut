# Exception Handling

→ **Exception Handling in Python** is used to handle **runtime errors**

→ Exception Handling allows a program to handle unexpected events without crashing.

→ lets you detect the problem, respond to it, and continue execution when possible.

> Exception handling in Python is a mechanism used to handle runtime errors using try, except, else, and finally blocks so that the program execution continues normally without crashing.
> 

## **Errors v/s Exceptions**

| ERROR | EXCEPTION |
| --- | --- |
| An **error** is a problem in the program that **prevents the program from running correctly** | An **exception** is a runtime problem that occurs during program execution |
| **cannot be handled easily by the programmer**. | **can be handled using exception handling** |
| Types: 
  1. **Syntax Error** 
  2. Logical **Error** 
  3. **Runtime Error**  | Types
  1. ZeroDivisionError
  2.  ValueError
  3. Type error 
etc |

Basic Synatx

```python
try:
      # Code 
except SomeException:
      # Code 
else:
     # Code 
finally:
    # Code 
```

- **try:** Runs the risky code that might cause an error.
- **except:** Catches and handles the error if one occurs.
- **else:** Executes only if no exception occurs in try.
- **finally:** Runs regardless of what happens useful for cleanup tasks like closing files.

## Handling Specific Exceptions

Instead of catching all errors, we can handle **specific exceptions**.

| Exception | Meaning |
| --- | --- |
| ZeroDivisionError | Division by zero |
| ValueError | Invalid value |
| TypeError | Wrong data type |
| IndexError | Index out of range |
| KeyError | Key not found in dictionary |
| FileNotFoundError | File does not exist |

Example

```python
try:
    num = int(input("Enter number: "))
    result = 10 / num
    print(result)

except ZeroDivisionError:
    print("Cannot divide by zero")
```

## Multiple Exceptions

→ We can catch multiple exceptions in a single block if we need to handle them in the same way

example

```python
try:
    a = int(input())
    b = int(input())
    print(a/b)

except (ValueError, ZeroDivisionError):
    print("Error occurred")
```

## Catch-All Handlers

→ A **catch-all handler** is an exception handler that catches **any type of exception**, instead of handling specific exceptions.

→ Using catch-all handlers can cause several problems.

1. Hides the Real Error
2. Makes Debugging Hard
3. Can Hide Critical Bugs

> **Catch-all handlers** are exception handlers that catch all types of exceptions using a general `except` block. They simplify error handling but introduce risks such as hiding the real error, making debugging difficult, masking critical bugs, and reducing code reliability.
> 

```python
#======== Example 1 ===================
try:
    a = int(input("Enter number: "))
    result = 10 / a
    print(result)

except:
    print("Some error occurred")
    
 #o/p -> if a=0 : Some error occurred
 
 
#============== Example 2 ===============   
try:
    a = 10/0
except Exception as e:
    print("Unexpected error:", e)
    
 #o/p -> Unexpected error: division by zero
```

## Raising Exceptions

**→ Raising an exception** means **manually triggering an error** in a program using the “raise” keyword.

→ **We can choose from built-in exceptions or define our own custom exceptions by inheriting from Python's built-in Exception class.**

```python
#Basic Synatx

raise ExceptionType("Error message")
```

- **raise** → keyword used to trigger an exception
- **ExceptionType** → type of exception
- **message** → description of the error

1. Using Built-in Exception

```python
def speed(n):
    if n<0:
        raise ValueError("Speed cannot be negative")
    print(f"The bike is moving at {n}")
    
    
try:
    speed(40)            # The bike is moving at 40
    speed(-10)           # Speed cannot be negative
except ValueError as e:
    print(e)
    

```

1. Custom Exception

→ Custom exceptions can be created by defining a new class that inherits from Python’s built-in Exception class.

```python
class SpeedError(Exception):
    pass

def speed(n):
    if n<0:
        raise SpeedError("Speed cannot be negative")
    print(f"The bike is moving at {n}")
    
    
try:
    speed(40)            # The bike is moving at 40
    speed(-10)           # Speed cannot be negative
except SpeedError as e:
    print(e)
    

```