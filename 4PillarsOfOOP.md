# 4 pillars of OOP

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

# ENCAPSULATION

→ Encapsulation is the process of wrapping data and methods into a single unit and restricting direct access to the data to ensure controlled interactions

→ Binding data and methods together inside a class is called encapsulation

### Why encapsulation needed?

→ Protects data from unauthorised access and accidental modifications

→ Control data updates using getter and setter methods

→ Centralised data handling

### Access Specifiers

→ Access specifiers define how class members can be accessed from outside the class. 

→ Controlling the visibility of data 

There are three types of access specifiers

1. Public
- Can be accessed from anywhere inside the class, outside the class or from other modules.
- By default all members in python are public
- ex : [self.name](http://self.name) = name

1. Protected
- Accessed only within the class and its subclasses
- Not strictly private
- Defined with single ‘ _  ‘ prefix
- ex: self._name = name

3. Private

- Cannot be accessed directly from outside the class
- Using to restrict access and protect internal data
- defined with “__” prefix
- ex self.__name = name
- Python applies name mangling by internally renaming them to prevent direct access
    - —name ⇒ _*ClassName*__name

### Getter and Setter methods

→ Getter & Setter methods are used to access and modify private attributes safely 

→ These methods provide controlled access 

→ read using getter 

→ Update using setter

Example

```python
class Student:

    def __init__(self, name, age, marks):

        self.name = name          # Public variable
        self._age = age           # Protected variable
        self.__marks = marks      # Private variable

    # Getter method for private variable
    def get_marks(self):
        return self.__marks

    # Setter method for private variable
    def set_marks(self, new_marks):
        if new_marks >= 0 and new_marks <= 100:
            self.__marks = new_marks
        else:
            print("Invalid marks")

# ---------------- Object Creation ----------------

s = Student("Chinnu", 20, 85)

# ---------------- Accessing Variables ----------------

print(s.name)        # Public → accessible everywhere
print(s._age)        # Protected → accessible but intended for internal use

# print(s.__marks)   # ❌ Error (private variable cannot be accessed directly)

# ---------------- Using Getter ----------------

print(s.get_marks())

# ---------------- Using Setter ----------------

s.set_marks(95)

print(s.get_marks())
```

---

# ABSTRACTION

→ Showing only the essential features and hiding the complex internal details is called abstraction

→ Shows what an object is and hides how it does

→ It defines required behaviour for the subclasses and mandatory implementations for the abstract methods

→ Abstract class cannot be instantiated

→ It defines contract that sub classes must follow

Why abstraction is needed?

- Produces complexity
- improves scalability
- lose coupling
- hides internal logic

Basic syntax

```python
from abc import ABC,abstractmethod
class ClassName(ABC):
    @abstractmethod
    def method(self):
       pass
```

### Abstract Base Classes (ABC)

→ Used to achieve data abstraction by defining common interface for its subclasses 

→ serves as a blueprint for other classes 

→ Cannot instantiate directly 

→ enforce method implementation in sub classes

Components:

1. abstract method
    - declared with @abstractmethod
    - Methods declared without body inside abstract class
    - Force subplaces to provide implementation
    - ensure consistent structure across derived classes
    - obj.method()
2. Concrete method
    - Fully implemented methods within abstract class
    - Subclasses can inherit and use them directly
3. Abstract Properties
    - Declared with @property
    - Turns a method Into attribute like access
    - obj.method
    - ex API → looks like data
4. Class instantiation rules
    - Cannot be instantiated directly because it contains one or more abstract methods
    - If instantiated it raises to type error

Example

```python
from abc import ABC, abstractmethod

class Shape(ABC):                     # Abstract class

    @abstractmethod
    def area(self):                   # Abstract method
        pass

class Circle(Shape):                  # Child class

    def __init__(self, radius):
        self.radius = radius

    def area(self):                   # Implementation
        return 3.14 * self.radius * self.radius

# Creating object
c = Circle(5)

print(c.area())
```

---

# INHERITANCE

→ Allows Atlas to inherit attributes and methods from another class

→ Parent class / base class - Class being inherited from

→ Child glass / derived class - class that inherits from another class

→ represents an “is-a” relationship

Why?

- code reusability
- models real world hierarchies
- enables method overriding

Basic Syntax

```python
class Parent:
   pass
 
class Child(Parent):
    pass
```

### super() function

- Super function is used to call parents class methods
- If a child has no construct, the parent class constructor is invoked

### Types

1. Single Inheritance
    - Inherits from just one parent

```python
class Child(Parent):
   pass
```

1. Multiple Inheritance
    - Can inherit from more than one parent
    - If constructor is not defined in child class it automatically calls to the first parent in the inheritance list according to method resolution order MRO
    
    ```python
    class Child(Parent1,Parent2):
        pass
    ```
    
    <aside>
    💡
    
    > MRO - Method Resolution Order
    > 
    
    It is the order by which searches classes to a method or an attribute
    
    to check the order → Child.__mro__
    
    </aside>
    
2. Multilevel Inheritance
    - A class is derived from another derived class
    
    ```python
    class Parent:
       pass
    class Child1(Parent):
        pass
    class Child2(Child1):
       pass
    ```
    
3. Hierarchical inheritance
    - Multiple child classes can inherit from same parent

```python
class Parent:
	pass
class Child1(Parent):
	pass
class Child2(Parent):
	pass
```

1. Hybrid inheritance
- Combination of one or more types
- it may cause diamond problem

Example

```python
class Person:                          # Parent Class

    def __init__(self, name, age):     # Parent Constructor
        self.name = name
        self.age = age

    def show_info(self):               # Parent Method
        print("Name:", self.name)
        print("Age:", self.age)

class Student(Person):                 # Child Class (inherits Person)

    def __init__(self, name, age, roll):
        super().__init__(name, age)    # Calling parent constructor
        self.roll = roll

    def show_roll(self):               # Child Method
        print("Roll No:", self.roll)

# Object Creation
s = Student("Chinnu", 20, 101)

# Calling methods
s.show_info()      # Inherited method
s.show_roll()      # Child class method
```

---

# POLYMORPHISM

→ Polymorphism means many forms 

→ It refers to the ability of an entity to perform different actions based on the context

→ It allows same method name or operation to behave differently depending on the object

why?

- Code flexibility
- reduces conditional logic
- allows generic code
- enables dynamic method behaviours

### Runtime (Overriding)

- Behaviour of a method is decided while programme is running based on object calling it
- Child declares provides implementation for method that has been implemented in the parent class

### Overloading

- Python does not support method overloading
- If multiple methods have same name the last method overrides the previous one
- Overloading is simulated using default arguments or variable length arguments

Example

```python
class Animal:                     # Parent class

    def speak(self):
        print("Animal makes sound")

class Dog(Animal):                # Child class

    def speak(self):              # Method overriding
        print("Dog barks")

class Cat(Animal):                # Another child class

    def speak(self):
        print("Cat meows")

# Creating objects
a = Animal()
d = Dog()
c = Cat()

# Calling same method
a.speak()
d.speak()
c.speak()
```

### Duck Typing

- Duck typing is a polymorphism concept in python where the suitability of an object is determined by the methods it implements rather than its class type
- The type of the object is less important than the behaviour
- Does not require inheritance and type checking
- It focuses on the object behaviour
- It fails if the method is not implemented

```python
class Dog:
	print("Bow Bow")
class Cat:
	print("meow")
def sound(obj)
	obj.sound()
	
sound(Dog())  #Bow Bow
sound(Cat()) #meow
```