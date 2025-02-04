## Inheritance in Java

### 1. **Introduction to Inheritance**

- Inheritance allows a class to acquire properties (methods and fields) of another.
- **Superclass (Parent class):** The class whose properties are inherited.
- **Subclass (Child class):** The class that inherits the properties.
- Purpose: Model objects with different behaviors while avoiding redundancy.

### 2. **Inheritance Hierarchies**

- Relationship between a more general class (**suprclass**) and a more specialized class (**subclass**).
- Example: `Car` class inherits from `Vehicle` class.
- Substitution Principle: A subclass object can always be used when a superclass object is expected.

### 3. **Types of Inheritance & Syntax**

- Use the `extends` keyword to implement inheritance.
- **Syntax:**
  
  ```java
  class Superclass {
      // Fields and methods
  }
  class Subclass extends Superclass {
      // Additional fields and methods
  }
  ```

### 4. **Using Inheritance in Java**

- Enables **code reuse** by allowing subclasses to inherit superclass methods.
- Example: Handling different question types (Multiple choice, Numeric, etc.) via subclassing.

### 5. **Implementing Subclasses**

- **What subclasses inherit:**
  - Instance variables (except private ones).
  - Methods (unless overridden).
- **Defining a subclass:**
  
  ```java
  public class ChoiceQuestion extends Question {
      private ArrayList<String> choices;
  }
  ```
- **Overriding Methods:** Change implementation of inherited methods.

### 6. **Method Overriding and `super` Keyword**

- **Overriding Methods:** Modify inherited methods to customize behavior.
- **Syntax:**
  
  ```java
  @Override
  public void display() {
      super.display(); // Calls superclass method
      // Additional behavior
  }
  ```
- **Common Errors:**
  - Overloading instead of overriding.
  - Forgetting `super` when calling superclass methods.

### 7. **The `Object` Class (Cosmic Superclass)**

- Every Java class extends `Object` by default.
- Important methods:
  - `toString()`: Returns a string representation of the object.
  - `equals(Object obj)`: Compares object content.
  - `hashCode()`: Returns numerical code for object storage.

### 8. **Using `instanceof` and Type Casting**

- **Type Checking:** Use `instanceof` to check object type before casting.
  
  ```java
  if (obj instanceof Question) {
      Question q = (Question) obj;
  }
  ```
- **ClassCastException:** Thrown if an object is cast to an unrelated class.

### 9. **Final Classes and Inheritance**

- **Final classes** (`final class ClassName {}`) **cannot be inherited**.
- Prevents modifications in subclasses.

### 10. **Common Errors & Best Practices**

- **Replicating instance variables**: Do not redefine superclass variables in the subclass.
- **Accidental method overloading**: Ensure method signatures match exactly when overriding.
- **Using `super` correctly**: Always use `super.methodName()` when calling superclass methods.
