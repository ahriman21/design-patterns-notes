# Adapter Design Pattern
The Adapter design pattern allows objects with incompatible interfaces to work together by providing a wrapper with a compatible interface. in other words if you have two classes that need to work with each other but can't, instead of changing the code you can create a third class to enable those classes to collaborate.

* example 
```python
import xmltodict


class Application:
	def send_request(self):
		return 'data.xml'


class Analytic:
	def receive_request(self, json):
		return json


class Adapter:
	def convert_xml_json(self, file):
		with open(file, 'r') as myfile:
			obj = xmltodict.parse(myfile.read())
			return obj


def client_adapter():
	sender = Application().send_request()
	converted_data = Adapter().convert_xml_json(sender)
	receiver = Analytic().receive_request(converted_data)
	print(receiver)


client_adapter()

```

* 2nd example
```python
# Target interface
class Shape:
    def draw(self):
        pass

# Adaptee with incompatible interface
class Square:
    def display(self):
        print("Square: Drawing a square")

# Adapter
class SquareAdapter(Shape):
    def __init__(self, square):
        self.square = square

    def draw(self):
        self.square.display()

# Client code
def draw_shape(shape):
    shape.draw()

square = Square()
adapter = SquareAdapter(square)

draw_shape(adapter)
```

