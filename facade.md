# Facade Design Patterns
Facade is a structural design pattern that enables us to set up a simple interface to a library or a class. for example if you use a library to send emails to users and to send the email it takes multiple lines of codes, by using facade design pattern you can hide the complexity of that lines and just send the email.

* first example :
using sms library without facade
```typescript
// library/class
class SmsLibrary {
  constructor(client_id, client_secret, driver) {
    // ...
  }

  public recipient(phone_number) {
    // ...
  }

  public send(text) {
    // send
  }
}


// using the library (CLIENT)
const client_id     = config('sms.client_id');
const client_secret = config('sms.client_secret');
const sms_driver    = config('sms.driver');

const sms = new SmsLibrary(client_id, client_secret, sms_driver);

sms.recipient('+989...');
sms.send('Welcome. Our app is great!');
```

using sms library with facade
```typescript
// library/class
class SmsLibrary {
  constructor(client_id, client_secret, driver) {
    // ...
  }

  public recipient(phone_number) {
    // ...
  }

  public send(text) {
    // send
  }
}


//facade
class SmsFacade {
  public static send(text, recipient) {
    const client_id     = config('sms.client_id');
    const client_secret = config('sms.client_secret');
    const sms_driver    = config('sms.driver');
    
    const sms = new SmsLibrary(client_id, client_secret, sms_driver);
    
    sms.recipient(recipient);
    sms.send(text);
  }
}


// uing library (CLIENT)
SmsFacade.send('Welcome!', '+989...');
// ...
SmsFacade.send('Your 2FA code', '+001...');
```

* second example:
turn a computer on using facade
```python

class CPU: # Subsystem 1
	def execute(self):
		print('Executing')


class Memory: # Subsystem 2
	def load(self):
		print('Loading data.')


class SSD: # Subsystem 3
	def read(self):
		print('Some data from ssd')


class Computer: # Facade
	def __init__(self, sub1, sub2):
		self.cpu = sub1()
		self.memory = sub2()

	def start(self):
		self.memory.load()
		self.cpu.execute()


def client_facade():
	computer_facade = Computer(CPU, Memory)
	computer_facade.start()


client_facade()

```












