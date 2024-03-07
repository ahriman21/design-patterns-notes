# Factory Design Pattern
Factory design pattern is a Creational design pattern.
allows you to create objects of different types without specifying the exact class to use at the time of creation.
when you have several classes or several functions that are similar to each other, instead of using if statements to determine the object type you can use factory design pattern.


* classes :
```python
from abc import ABC


class Shape(ABC):
	def draw(self):
		pass


class Rectangle(Shape):
	def draw(self):
		print('a rectangle is drewn')


class Circle(Shape):
	def draw(self):
		print('a circle is drewn')
```


* factory :
```python
class ShapeFactory:
	@staticmethod
	def shape_factory(type: str):
		if type == 'circle':
			return Circle()

		elif type == 'rectangle':
			return Rectangle()

		else:
			return None

```

* entry poing
```python
import ShapeFactory

if __name__ == '__main__':
	shape1 = ShapeFactory.shape_factory(type='circle')
	shape2 = ShapeFactory.shape_factory(type='rectangle')

	# this code below will call the method draw of Circle class because shape1 is an instance of class Circle
	shape1.draw()

	# because shape2 is an instance of Rectangle, the draw method of Rectangle will be called
	shape2.draw()

```

