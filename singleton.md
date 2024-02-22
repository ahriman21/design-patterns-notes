# Singelton design pattern ?
    What is singleton design pattern?
    The goal of singelton design pattern is to ensure we can only create one instance of a specific class.
    Because creating new instances will cause more resources and sometimes we don't want that.
    
    If you want to have a clean way of implementing singelton in your python projects you can use meta classes.
    
    A metaclass in python is a class that changes attributes of another class     


## implementing singelton in python (first way)
from typing import Any

```python
class A:
    _instance = None

    def __init__(self) -> None:
        raise RuntimeError('call get_instance() instead')
    
    @classmethod
    def get_instance(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)

        return cls._instance

```

## implementing singelton in python (second way)
```python
class B:
    _instance = None

    def __new__(cls, *args, **kwargs):
        """ 
        __new__ dunder method is called while creating a new object.
        this method gets started even before __init__()
        """
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance
    
    def __init__(self) -> None:
        print(self)

```

## implementing singelton in python (third way)
```python
class Singelton(type):
    _instance = None

    def __call__(self, *args: Any, **kwds: Any) -> Any:
        if self._instance is None:
            self._instance = super().__call__(*args, **kwds)
        return self._instance 
         
class C(metaclass=Singelton):
    pass
```

## now we can create instance of those classes above and see the result
```python
if __name__ == '__main__':
    ## FIRST WAY : A
    # a = A()
    # a = A.get_instance()
    # b = A.get_instance()
    # print(a, '\n', b)



    ## SECOND WAY : B
    # a = B()
    # b = B()



    ## THIRD WAY : C
    a = C()
    b = C()  
    print(a, '\n', b)   

```