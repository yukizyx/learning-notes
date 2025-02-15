### **1. Relationships in Object-Oriented Programming**

- **Association**
  - General relationship between two classes
  - Represented by a straight-line arrow
  - Classes communicate through objects
- **Aggregation ("Has-a" Relationship)**
  - Objects own a collection of other objects
  - One-way relationship (e.g., Professor has many Students)
  - Represented as a data field in the aggregating class
- **Composition (Strong "Has-a" Relationship)**
  - Objects are dependent on each other (e.g., Room has a Door)
  - Stronger than aggregation; child object cannot exist without parent
- **Composition vs. Aggregation**
  - **Composition**: Strong association – dependent relationship
  - **Aggregation**: Weak association – independent objects

### **2. Inheritance ("Is-a" Relationship)**

- **Definition**
  - Subclass is a specialization of the superclass
  - Subclass inherits characteristics of the superclass
- **Examples**
  - A Car is-a Vehicle
  - A Truck is-a Vehicle
- **Conceptual Questions**
  - Can every class be inherited?
  - Can a class inherit from multiple classes?
  - When to use `super` keyword?
  - How to prevent method overriding?

### **3. Method Overloading vs. Method Overriding**

- **Method Overriding**
  - Occurs in subclass with the same method signature as the superclass
  - Happens at runtime
- **Method Overloading**
  - Same method name with different parameters
  - Happens at compile-time
- **Key Differences**
  - Constructors can be overloaded but cannot be inherited
  - Overloading occurs at compile-time, overriding occurs at runtime

### **4. Abstraction**

- **Definition**
  - Hiding complexity and showing only relevant features
  - Implementation details are hidden
- **Ways to Implement Abstraction in Java**
  - **Interfaces**: Defines expected behavior
  - **Abstract Classes**: Provides incomplete functionality
- **Abstract Class Characteristics**
  - Cannot be instantiated
  - May contain abstract methods
  - Abstract methods have no body
  - If a class has at least one abstract method, it must be declared as abstract
- **Abstract Methods**
  - Enforces implementation in subclasses
  - Supports defining expected behavior across subclasses
- **Rules for Abstract Classes and Methods**
  - A class containing an abstract method must be abstract
  - A subclass must implement all abstract methods or be declared abstract itself
  - Constructors and static methods cannot be abstract

### **5. Encapsulation & Class Abstraction**

- **Encapsulation**
  - Separating implementation details from usage
  - Users interact with a class without knowing internal workings
- **Encapsulation and Information Hiding**
  - Implementation details are hidden from the user
  - Supports modular programming

### **6. Protected Access Modifiers**

- **Access Modifiers in Java**
  - **Public**: Visible to all classes
  - **Protected**: Accessible within the same package and in subclasses
  - **Private**: Accessible only within the class
- **Protected Constructors in Abstract Classes**
  - Prevents instantiation of an abstract class
  - Can be accessed via `super` in subclass
