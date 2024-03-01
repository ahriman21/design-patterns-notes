# Decorator Design Pattern
in decorator design pattern we can add new features to the functions without making changes in the codebase each time while adding new features.

* exmple
```typescript
// interface 
interface RoomInterface {
  getDescription();
  getPrice();
}


// concrete
class SimpleRoom implements RoomInterface {
  getDescription() {
    return "Base room";
  }

  getPrice() {
    return 2.00;
  }
}


// base decorator
abstract class BaseDecorator implements RoomInterface {
   protected room: RoomInterface;

  constructor(room: RoomInterface) {
    this.room = room;
  }

  public getDescription() {
    return this.room.getDescription();
  }

  public getPrice() {
    return this.room.getPrice();
  }
}


// first decorator : Wifi feature
class WiFiDecorator extends BaseDecorator {
  public getDescription() {
    return `${super.getDescription()} + WiFi`;
  }

  public getPrice() {
    return super.getPrice() + 0.2;
  }
}

// client
var room = new SimpleRoom();
wifiroom = new WiFiDecorator(room);

console.log('Description:', wifiroom.getDescription());
console.log('Price:', wifiroom.getPrice());

// output :
// Description: Base room + WiFi
// Price: 2.2
```






















