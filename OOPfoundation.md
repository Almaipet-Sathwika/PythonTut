# Object Oriented Programming

# What is OOP?

→ OOP is a programming paradigm that provides means of structuring programs so that properties and behaviors are bundled into individual objects

→ It models real world entities as software objects that have some data and can perform certain tasks

# Why OOP?

1. Real world modelling - the world is made up of objects 
2. Control over data - OOP lets you control how data is modified Hide internal details and prevent Accidental corruption
3. Court reusability - common behavior of an entity is defined by a parent class and specific behavior is modified in the child class
4. Flexibility -  different objects can behave different using the same interface .That is same method name but different logic

Basic Structure

```python
class definition:
	constructor
		Instance variable
	creting instance 
	accessing attributes and calling methods
	
```

# Classes

→ A class is a user defined data type that encapsulates data and functions into a single unit it enables OOP by allowing abstraction, encapsulation, inheritance and polymorphism.

→ Classes are blueprints for creating objects. A class defines a set of attributes and methods that  the created object can have

→ Class name should follow Pascal case by Python Convention while it is not syntactically mandatory it improves readability and maintains permission coding standards

Syntax:

```python
class ClassName:
	x = 10         #class variable
	def __init__(self, para1, para2,....):
		self.para1 = para1  #instance variables
		selfpara2 = para2 
	def method():  #instance method
		pass
```

**What all can a class contain?**

1. Class Variables
    
    → shared by all objects
    
    → stored at class level
    
    → same value for every instance 
    
2. Instance Variable
    
    → unique to each object
    
    → defined inside constructor
    
3. Instance Methods
    
    → Work with object data
    
    → always take self as 1st parameter
    
    → can access class and instance variable
    
4. Class methods
    
    → works with class level data
    
    → Use @classmethod
    
    → cls is the first parameter in the method definition
    
    → modify class variables
    
5. static methods
    
    → Utility function inside class
    
    → Do not access instance/class dat
    
    → use @staticmethod
    
    → used for logical grouping , helper functions
    
    ```python
    
    class ClassName:
    
        class_variable = "Some Value"             # Class Variable (shared by all objects)
    
        def __init__(self, param1, param2):      # Constructor
            self.instance_var1 = param1             # Instance Variable
     
    
        def instance_method(self):                  # Instance Method
           pass
    
        @classmethod
        def class_method(cls, new_value):        # Class Method
            cls.class_variable = new_value           # Modify class variable
    
        @staticmethod
        def static_method():                             # Static Method
            print("Static method called")           # Utility function
    
    # -------------------- Object Instantiation --------------------
    
    obj1 = ClassName(arguments)   # Creating first object
    
    # -------------------- Using Instance Method --------------------
    
    obj1.instance_method()
    
    # -------------------- Using Class Method --------------------
    
    ClassName.class_method("New Value")
    
    # -------------------- Using Static Method --------------------
    
    ClassName.static_method()
    ```
    

# Object

→ An object is a runtime entity from a class that encapsulates data and behaviour into a single unit

→  Object is an instance of class it represents real world entity and contains data and behaviour defined by the class

→ It is the real implementation of class blueprint

```python
Syntax

obj_name = ClassName(data)

#this calls class constructor
```

# Constructor

→Automatically executes when an object is created 

→ self represents current object and it should be first parameter

 → It cannot return any value used for object initialization and not for logic

→ Constructor is not mandatory, if not defined python provides default empty constructor

→ Types of Constructors

1. Default Constructor
    - Constructor without parameters except self
2. Parameterized Constructor
    - Constructor with parameters along with selfs
    - Constructor can also have default parameters

# **Self**

- Represents current object
- used to access instance variables and methods
- connects objects with its data
- It is not a keyword self can be any naming convention
- Without self variables become local

> Self refers to current instance of class, it is used to access instance variables and methods within a class. Python requires it explicitly because methods are just functions inside a class and must receive the object reference manually
> 

# Task1

## Bank Account System

Create a `BankAccount` class.

**Attributes:**

- account_holder
- balance

**Methods:**

- deposit(amount)
- withdraw(amount)
- check_balance()

👉 Rules:

- No negative deposits.
- Cannot withdraw more than balance.
- Create multiple accounts and perform transactions.

# Task 2

## To-Do List App Model

Create:

- `Task` class
- `TodoList` class

Task:

- title
- is_completed

TodoList:

- add_task()
- complete_task()
- show_pending()
- show_completed()