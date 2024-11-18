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
