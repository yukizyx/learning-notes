## Polymorphism in Java

### 1. **Introduction to Polymorphism**

- **Definition:** "Poly" means "many," and "morph" means "forms."
- The ability of a method to behave differently based on the object it acts upon.
- Enables programming at a general level instead of a specific one.

### 2. **Key Concepts of Polymorphism**

- **Supertype & Subtype:** A variable of a **superclass** type can reference a **subclass** object.
- **Example:** A `Bird` is a subtype of `AnimalObject`, and `AnimalObject` is a supertype of `Bird`.
- **Animal Simulation Example:** Different animals (`Fish`, `Frog`, `Bird`) override a `move()` method differently.

### 3. **Example of Polymorphism**

- **Base Class:** `Food` with a `taste()` method.
- **Subclasses Override Method:**
  - `Rice` → "Rice is sweet."
  - `Potatoes` → "Potatoes are sour."
  - `Peppers` → "Peppers are spicy."

### 4. **Why Use Polymorphism?**

- **Flexibility & Extensibility:** Allows adding new behavior with minimal changes.
- **Code Reusability:** Enables method overriding without modifying the original class.
- **Simplifies Code:** A single interface can represent multiple behaviors.

### 5. **Polymorphism vs. Inheritance**

- **Inheritance:** Subclasses inherit superclass methods and structure.
- **Polymorphism:** Allows a subclass to modify or override the behavior of a superclass method.

### 6. **Examples of Polymorphism in Java**

- **Shapes:** If `Rectangle` extends `Quadrilateral`, operations on `Quadrilateral` can be applied to `Rectangle`.
- **Video Game Objects:**
  - `SpaceObject` is the superclass.
  - Subclasses (`Martian`, `Venusian`, `SpaceShip`) override `draw()` to display differently.

### 7. **Types of Polymorphism**

- **Static (Compile-time) Polymorphism:** Achieved through method overloading.
- **Dynamic (Run-time) Polymorphism:** Achieved through method overriding.

### 8. **Method Overriding in Java**

- When a subclass provides a different implementation for a method in the superclass.
- **Example:**
  ```java
  class Human {
      public void dress() { System.out.println("Humans wear clothes"); }
  }
  class Girl extends Human {
      @Override
      public void dress() { System.out.println("Girls wear dresses"); }
  }
  ```
- **Rules for Overriding:**
  - Argument list must match exactly.
  - Cannot override `private`, `static`, or `final` methods.
  - Overriding method cannot have a more restrictive access modifier.

### 9. **Binding in Java**

- **Static Binding (Early Binding):** Resolved at **compile-time** (used for `static`, `private`, and `final` methods).
- **Dynamic Binding (Late Binding):** Resolved at **run-time** (used for overridden methods).

### 10. **Conclusion & Tips**

- Polymorphism allows generalization, enabling code to work with different object types.
- It promotes **code maintainability** and **scalability** by minimizing changes in existing code.
- **Example:** An `Employee` superclass with `paySalary()` can be overridden differently in `Manager`, `Intern`, etc.
