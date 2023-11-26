### [Object-Oriented Programming in Python](https://www.freecodecamp.org/news/object-oriented-programming-in-python/)  
__Date - 26/11/23__  

Python is a great programming language that allows us to use both functional and object-oriented programming paradigms.  

All the core aspects of a generic OOP framework are supported by Python's object-oriented programming system, such as encapsulation, abstraction, inheritance, and polymorphism.  

In Python, built-in classes are the most common data types such as strings, lists, dictionaries, and so on.  

#### **Class:** A class is a collection of instance variables and related methods that define a particular object type.  

We can think of class as an object's blueprint or template. Attributes are the names given to the variables that make up class.

#### **Class Instance:** A class instance with a defined set of properties is called an object. As a result, the same class can be used to construct as many objects as needed.  

#### **Let us define a class named _Book_ for a bookseller's sales software**  

```python3
class Book:
    def__init__(self, title, quantity, author, price):
    self.title = title
    self.quantity = quantity
    self.author = author
    self.price = price
```

The `__init__` is special method, also known as a constructor, is used to initialize the book class with attributes such as title, quantity, author and price.  

In python built-in classes are named in lower case, but user defined classes are named in Camel or Snake case, with the first letter capitalized.  

This class can be instantiated to any number of objects. Three books are instantiated in the following example code:

```python3
book1 = Book('Book 1', 12, 'Author 1', 120)
book2 = Book('Book 2', 18, 'Author 2', 220)
book3 = Book('Book 3', 28, 'Author 3', 320)
```  

book1, book2 and book3 are distinct objects of the class Book. The term self in the attributes refers to the corresponding instances(objects).

```python3
print(book1)
print(book2)
print(book3)
```  

#### Output:

```shell
<__main__.Book object at 0x00000156EE59A9D0>
<__main__.Book object at 0x00000156EE59A8B0>
<__main__.Book object at 0x00000156EE59ADF0>
```

Here the class and memory location of the objects are printed when they are printed. We can't expect them to provide specific information on the qualities, such as the title, author name and so on. But we can use a specific method called `__repr__` to do this.  

In python, a special method is defined function that starts and ends with two underscore and is invoked automatically when certain conditions are met.  

```python3

```  

#### Output:

```shell

```  

#### **What is Encapsulation?**  

Encapsulation is the process of preventing clients from accessing certain properties, which can only be accessed through specific methods.