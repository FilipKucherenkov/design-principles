# design-principles
SOLID, YAGNI, KISS with simple examples

## SOLID 

### Single Responcibility Principle
A Class should have 1 reason to change it should have 1 responcibility.
```
class Invoice {
    public void generateInvoice() {
        System.out.println("Generating invoice...");
    }
}

class InvoicePrinter {
    public void printInvoice(Invoice invoice) {
        System.out.println("Printing invoice...");
    }
}
```
In this example invoice generation and printing have been identified as 2 separate responcilities which are managed by separate classes respectively. 

### Open-Closed Principle
Classes should be open for extension, but closed for modification.
```
abstract class Discount {
    abstract double apply(double price);
}

class SeasonalDiscount extends Discount {
    double apply(double price) {
        return price * 0.9; // 10% off
    }
}

class LoyaltyDiscount extends Discount {
    double apply(double price) {
        return price * 0.8; // 20% off
    }
}
```
Here we add new discount types without the need to change existing ones. 

### Liskov's Substitution Principle 
Subtypes must be substistutable with their base types. 
```
class Vehicle {
    void startEngine() {
        System.out.println("Engine started!");
    }
}

class Car extends Vehicle {
    void startEngine() {
        System.out.println("Car engine started!");
    }
}
```
We should be able to use `Vehicle car = new Car()` without any issues. 

### Interface Segregation Principle
Interfaces should only have methods that are relevant to the implementing class.
```
interface Printer {
    void print();
}

interface Scanner {
    void scan();
}

class MultiFunctionPrinter implements Printer, Scanner {
    public void print() {
        System.out.println("Printing...");
    }
    public void scan() {
        System.out.println("Scanning...");
    }
}
```
As opposed to having a single interface providing both `scan()` and `print()`.
This ensure if we were to add a printer that supports only printing we could only implement `Printer` interface and omit the `Scanner`.

### Dependency Inversion Principle
High-level modules should not depend on low-level modules. Both should rely on abstractions. 
```
interface MessageSender {
    void sendMessage(String message);
}

class EmailSender implements MessageSender {
    public void sendMessage(String message) {
        System.out.println("Email sent: " + message);
    }
}

class Notification {
    private MessageSender sender;

    public Notification(MessageSender sender) {
        this.sender = sender;
    }

    public void notify(String message) {
        sender.sendMessage(message);
    }
}
```
In this example, adhering to the principle allows us to switch the MessageSender implementation without changing the Notification class.
Another example is the Repository layer (JPA) in Spring applications - it provides an abstraction over interactions with the DB (it won't matter whether you use MySQL or PostgreSQL to execute a `findById` and query a record.) 

