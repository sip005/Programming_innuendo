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
class Book():
    def __init__(self, title, quantity, author, price):
        self.title = title
        self.quantity = quantity
        self.author = author
        self.price = price
        
    def __repr__(self):
        return f"Book Title: {self.title}, quantity: {self.quantity}, Author: {self.author}, Price: {self.price}"

book1 = Book('Book 1', 12, 'Author 1', 120)
book2 = Book('Book 2', 18, 'Author 2', 220)
book3 = Book('Book 3', 28, 'Author 3', 320)

print(book1)
print(book2)
print(book3)

```  

#### Output:

```shell
Book: Book 1, Quantity: 12, Author: Author 1, Price: 120
Book: Book 2, Quantity: 18, Author: Author 2, Price: 220
Book: Book 3, Quantity: 28, Author: Author 3, Price: 320
```  

#### **What is Encapsulation?**  

Encapsulation is the process of preventing clients from accessing certain properties, which can only be accessed through specific methods.  

Private attributes are incaccessible attributes and information hiding is the process of making particular attributes private. We use two underscore to declare private characteristics.  

Let's introduce a private attribute called __discount in the Book class.

```python3
class Book:
    def __init__(self, title, quantity, author, price):
        self.title = title
        self.quantity = quantity
        self.author = author
        self.price = price
        self.__discount = 0.10

    def __repr__(self):
        return f"Book: {self.title}, Quantity: {self.quantity}, Author: {self.author}, Price: {self.price}"


book1 = Book('Book 1', 12, 'Author 1', 120)

print(book1.title)
print(book1.quantity)
print(book1.author)
print(book1.price)
print(book1.__discount)
```

#### Output:

```shell
Book 1
12
Author 1
120
Traceback (most recent call last):
  File "C:\Users\ashut\Desktop\Test\hello\test.py", line 19, in <module>
    print(book1.__discount)
AttributeError: 'Book' object has no attribute '__discount'
```

From the above output we can observe that the attibutes are printed except for the private attribute `__discount`.  

__We can use getter and setter method to access the private attribute.__  

We make the price property private in the following code example, and we use a setter method to assign the discount attribute and a getter function to get the price attribute.

```python3
class Book:
    def __init__(self, title, quantity, author, price):
        self.title = title
        self.quantity = quantity
        self.author = author
        self.__price = price
        self.__discount = None

    def set_discount(self, discount):
        self.__discount = discount

    def get_price(self):
        if self.__discount:
            return self.__price * (1-self.__discount)
        return self.__price

    def __repr__(self):
        return f"Book: {self.title}, Quantity: {self.quantity}, Author: {self.author}, Price: {self.get_price()}"
```  

This time we'll create two objects, one for the purchase of single book and another for the purchase of books in bulk quantity. While purchasing books in bulk quantity, we get a discount of 20%, so we'll use the set_discount() method to set the discount to 20% in that case.  

```python3
single_book = Book('Two States', 1, 'Chetan Bhagat', 200)

bulk_books = Book('Two States', 25, 'Chetan Bhagat', 200)
bulk_books.set_discount(0.20)

print(single_book.get_price())
print(bulk_books.get_price())
print(single_book)
print(bulk_books)
```

#### Output:

```shell
200
160.0
Book: Two States, Quantity: 1, Author: Chetan Bhagat, Price: 200
Book: Two States, Quantity: 25, Author: Chetan Bhagat, Price: 160.0
```

#### **What is Inheritance?**  
Inheritence is regarded as one of the important characteristics of the OOP. A class's ability to inherit methods and/or characteristics from anther classes is known as inheritance.  

Here's an example to illustrate inheritance in Python:
```python3
class Animal:
    def __init__(self, species):
        self.species = species

    def make_sound(self):
        pass  # Placeholder method to be overridden in subclasses


class Dog(Animal):  # Dog class inherits from Animal
    def make_sound(self):
        return "Woof!"


class Cat(Animal):  # Cat class inherits from Animal
    def make_sound(self):
        return "Meow!"


# Creating instances of the derived classes
dog = Dog("Canine")
cat = Cat("Feline")

# Accessing attributes and methods inherited from the base class
print(dog.species)  # Output: Canine
print(cat.species)  # Output: Feline

# Calling overridden method in the derived classes
print(dog.make_sound())  # Output: Woof!
print(cat.make_sound())  # Output: Meow!
```  

The subclass or child class is the class that inherits. The superclass or parent class is the class from which methods and/or attributes are inherited.

Two new classes have been added to our bookseller's sales software: a Novel class and Academic class.  

We can see that regardless of whether a book is classified as novel or academic, it may have some similar attributes like title and author, as well as common methods like get_price() and set_discount(). Rewriting all that code for each new class is a waste of time, effort, and memory.  

```python3
class Book:
    def __init__(self, title, quantity, author, price):
        self.title = title
        self.quantity = quantity
        self.author = author
        self.__price = price
        self.__discount = None

    def set_discount(self, discount):
        self.__discount = discount

    def get_price(self):
        if self.__discount:
            return self.__price * (1-self.__discount)
        return self.__price

    def __repr__(self):
        return f"Book: {self.title}, Quantity: {self.quantity}, Author: {self.author}, Price: {self.get_price()}"


class Novel(Book):
    def __init__(self, title, quantity, author, price, pages):
        super().__init__(title, quantity, author, price)
        self.pages = pages


class Academic(Book):
    def __init__(self, title, quantity, author, price, branch):
        super().__init__(title, quantity, author, price)
        self.branch = branch
```
Let's create objects for these classes to visualize them.  

```python3
novel1 = Novel('Two States', 20, 'Chetan Bhagat', 200, 187)
novel1.set_discount(0.20)

academic1 = Academic('Python Foundations', 12, 'PSF', 655, 'IT')

print(novel1)
print(academic1)
```  

#### Output:  

```shell
Book: Two States, Quantity: 20, Author: Chetan Bhagat, Price: 160.0
Book: Python Foundations, Quantity: 12, Author: PSF, Price: 655
```

#### **What is Polymorphism?**  

The term 'polymorphism' comes from the Greek language and means 'something that takes on multiple forms.'  

