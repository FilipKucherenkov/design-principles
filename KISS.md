## Keep It Simple, Stupid (KISS)
Keep the design and code simple and avoid unnecessary complexity.

### Example (Violates KISS) 
```
class NumberUtils {

    public boolean isEven(int number) {
        // Using over-complicated logic for a simple task
        if (number % 2 == 0) {
            return true;
        } else {
            return false;
        }
    }
}
```
### Example (Adheres to KISS) 
```
class NumberUtils {

    public boolean isEven(int number) {
        // Simple and direct logic
        return number % 2 == 0;
    }
}
```
