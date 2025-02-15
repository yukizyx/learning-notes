### **1. Introduction to Interface**

- **Definition**:
  - A collection of abstract methods and constants
  - Abstract methods have no body
  - Interfaces define expected behavior for classes
- **Syntax of Interfaces**
  - Declared using the `interface` keyword
  - All methods are implicitly `public` and `abstract`
  - Example:
    ```java
    public interface Doable {
        void doThis();
        int doThat();
        void doThis2(float value, char ch);
        boolean doTheOther(int num);
    }
    ```
- **Key Properties of Interfaces**
  - Cannot be instantiated
  - Methods have `public` visibility by default
  - A class implements an interface using `implements` keyword
  - Must provide implementations for all interface methods

### **2. Implementing Interfaces in Java**

- **Syntax for Implementation**
  ```java
  public class CanDo implements Doable {
      public void doThis() { /* Implementation */ }
      public int doThat() { return 0; }
  }
  ```
- A class implementing an interface:
  - Must implement all its methods
  - Can implement additional methods
  - Gains access to all interface constants
- **Example: Encryptable Interface**
  - Declaring the `Encryptable` interface:
    ```java
    public interface Encryptable {
        void encrypt();
        String decrypt();
    }
    ```
  - Implementing it in the `Secret` class
    ```java
    public class Secret implements Encryptable {
        private String message;
        public void encrypt() { /* Caesar cipher logic */ }
        public String decrypt() { /* Decryption logic */ }
    }
    ```
- **UML Representation**
  - UML uses a **dotted arrow** to indicate interface implementation

### **3. Multiple Interfaces Implementation**

- **A class can implement multiple interfaces**
  ```java
  class ManyThings implements Interface1, Interface2 {
      // Must implement all methods from both interfaces
  }
  ```
- Benefits:
  - Allows unrelated classes to implement a common set of methods
  - Supports **loose coupling** and **dynamic method resolution**

### **4. Why Use Interfaces?**

- **Facilitate abstraction**
- **Promote standardization** for classes
- **Enable polymorphism**
- **Support multiple inheritance (via interfaces)**

### **5. Real-World Examples of Interfaces**

- **Example 1: Payroll System**
  - Employees and invoices both require a `getPaymentAmount()` method
  - Instead of using inheritance, both can implement the `Payable` interface
- **Example 2: Radio Controls**
  - Different radios have different implementations, but all must have `changeStation()`, `adjustVolume()`, etc.
- **Example 3: Car Driving Interface**
  - A car can have different braking systems but must have a `brake()` method

### **6. Interfaces vs Abstract Classes**

- **Key Differences**
  | Feature              | Interface                      | Abstract Class                       |
  | -------------------- | ------------------------------ | ------------------------------------ |
  | Methods              | Only abstract                  | Can have abstract & concrete methods |
  | Fields               | Static & final only            | Can have instance variables          |
  | Multiple Inheritance | A class can implement multiple | A class can extend only one          |
  | Default Methods      | Supported (from Java 8)        | Not needed                           |
- **When to Use Each?**
  - Use **abstract class** when default behavior is needed
  - Use **interface** when multiple unrelated classes share a behavior

### **7. Common Interfaces in Java API**

- **Comparable Interface**
  - Used to compare objects
  - Example:
    ```java
    public class Employee implements Comparable<Employee> {
        public int compareTo(Employee other) {
            return this.salary - other.salary;
        }
    }
    ```
- **Iterator Interface**
  - `hasNext()`, `next()`, and `remove()` methods
  - Used to traverse collections

### **8. Polymorphism via Interfaces**

- Using an interface as a reference type:
  ```java
  Speaker guest = new Philosopher();
  guest.speak(); // Calls Philosopher’s implementation
  guest = new Dog();
  guest.speak(); // Calls Dog’s implementation
  ```
- Allows **dynamic method dispatch**

### **9. Advanced Features of Interfaces (Java 8 & Later)**

- **Default Methods**
  - Interfaces can have concrete method implementations
  - Example:
    ```java
    public interface MyInterface {
        default void sayHello() {
            System.out.println("Hello from MyInterface");
        }
    }
    ```
- **Static Methods**
  - Can be used to provide utility methods within an interface
- **Functional Interfaces (Single Abstract Method - SAM)**
  - Example: `Runnable`, `Comparator`
  - Used in **lambda expressions**
