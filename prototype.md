# Prototype Design Pattern:
This is a creational design pattern. it enables the creation of new object by copying an existing object instead of creating new object from a class that has high cost.The concept is to copy an existing object rather than create a new instance from scratch, something that may include costly operations

Instead of starting from scratch each time, the user can use the Prototype pattern. The original document becomes the prototype, and new documents are created by cloning this prototype. This approach ensures that the new documents inherit the structure and styling of the original document while allowing for customization.

* example
```python
# concrete
class Book:

    def __init__(self, name, author):
        self.name = name
        self.author = author


    def clone(self):
        return Book(self.name, self.author)

# client
if '__name__' == '__main__':
    # existing instance
    book = Book('how to influence people', 'Dale Carengie')

    # clone
    book2 = book.clone()
```

> note : in python you can use `cloned_instance = copy.deepcopy(object)` to clone an instance

    
