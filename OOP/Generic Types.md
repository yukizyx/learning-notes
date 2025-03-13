# **Java Generics**

## **1. Java 泛型 (Generics) 概述**

### **1.1 泛型的目标**

- 允许使用不同的数据类型实现相同的代码，提高**代码复用性**和**类型安全性**。
- 主要用于**类 (Generic Classes)** 和 **方法 (Generic Methods)**。

### **1.2 为什么需要泛型？**

- **避免类型转换问题**
  - 传统 `ArrayList` 只能存储 `Object`，需要手动类型转换，容易导致运行时错误。
- **提高代码可读性**
  - 泛型使代码更易理解，无需强制类型转换。
- **提升类型安全性**
  - 泛型在编译时检查类型错误，避免 `ClassCastException`。

## **2. 泛型类 (Generic Classes)**

### **2.1 泛型类的定义**

- 通过**类型参数 (Type Parameter)** 创建泛型类，例如 `ArrayList<T>`。
- 语法：

  ```java
  public class Pair<T, S> {
      private T first;
      private S second;

      public Pair(T firstElement, S secondElement) {
          first = firstElement;
          second = secondElement;
      }

      public T getFirst() { return first; }
      public S getSecond() { return second; }
  }
  ```

- 使用：

  ```java
  Pair<String, Integer> result = new Pair<>("Alice", 100);
  String name = result.getFirst();
  int score = result.getSecond();
  ```

### **2.2 泛型类的类型参数**

- **泛型变量命名约定**：
  | 类型变量 | 含义 |
  | -------- | ---------------------- |
  | `T` | 通用类型 (Type) |
  | `E` | 集合元素类型 (Element) |
  | `K` | 键类型 (Key) |
  | `V` | 值类型 (Value) |

---

## **3. 泛型方法 (Generic Methods)**

### **3.1 泛型方法的定义**

- 泛型方法是在**方法级别**定义的，独立于类是否泛型。
- 语法：

  ```java
  public class ArrayUtil {
      public static <T> void printArray(T[] array) {
          for (T element : array) {
              System.out.print(element + " ");
          }
          System.out.println();
      }
  }
  ```

- 使用：

  ```java
  String[] words = {"Java", "Generics", "Example"};
  ArrayUtil.printArray(words);  // 输出: Java Generics Example
  ```

### **3.2 泛型方法的特点**

- 只在方法内部使用泛型类型。
- 类型推断：调用时无需显式指定类型，编译器会自动推断。

## **4. 类型参数的约束 (Constraining Type Variables)**

### **4.1 限制类型参数**

- 通过 `extends` 关键字，限制类型必须是某个类的子类或实现某个接口。
- **示例：限制类型必须实现 `Measurable` 接口**

  ```java
  public interface Measurable {
      double getMeasure();
  }

  public static <E extends Measurable> double average(ArrayList<E> objects) {
      if (objects.isEmpty()) return 0;
      double sum = 0;
      for (E obj : objects) {
          sum += obj.getMeasure();
      }
      return sum / objects.size();
  }
  ```

- **示例：限制类型必须实现 `Comparable` 接口**

  ```java
  public static <E extends Comparable<E>> E min(ArrayList<E> objects) {
      E smallest = objects.get(0);
      for (E obj : objects) {
          if (obj.compareTo(smallest) < 0) {
              smallest = obj;
          }
      }
      return smallest;
  }
  ```

## **5. 泛型与继承**

### **5.1 泛型和继承的区别**

- **错误示例：`ArrayList<SavingsAccount>` 不是 `ArrayList<BankAccount>` 的子类**

  ```java
  ArrayList<SavingsAccount> savingsAccounts = new ArrayList<>();
  ArrayList<BankAccount> bankAccounts = savingsAccounts;  // ❌ 编译错误
  ```

- **但数组可以向上转换**：

  ```java
  SavingsAccount[] savingsArray = new SavingsAccount[10];
  BankAccount[] bankArray = savingsArray;  // ✅ 允许
  ```

## **6. 通配符类型 (Wildcard Types)**

| **通配符**                            | **语法**      | **含义**          |
| ------------------------------------- | ------------- | ----------------- |
| **上界通配符 (Upper Bound Wildcard)** | `? extends B` | **B 或 B 的子类** |
| **下界通配符 (Lower Bound Wildcard)** | `? super B`   | **B 或 B 的父类** |
| **无界通配符 (Unbounded Wildcard)**   | `?`           | **任何类型**      |

### **6.1 上界通配符 `? extends B`**

- 适用于**只读数据**（Producer）。
- **示例**：`List<? extends Number>` 可存储 `Integer`、`Double` 等子类对象。

  ```java
  public void addAll(List<? extends Number> numbers) { ... }
  ```

### **6.2 下界通配符 `? super B`**

- 适用于**写入数据**（Consumer）。
- **示例**：`List<? super Integer>` 允许存储 `Integer` 及其父类 `Number`、`Object`。

  ```java
  public void addNumbers(List<? super Integer> list) {
      list.add(10); // ✅ 允许
  }
  ```

## **7. 类型擦除 (Type Erasure)**

### **7.1 什么是类型擦除？**

- **Java 泛型在运行时被擦除，转换为原始类型 (Raw Type)**。
- **示例：`Pair<T, S>` 变成 `Pair<Object, Object>`**

  ```java
  public class Pair {
      private Object first;
      private Object second;
      public Pair(Object firstElement, Object secondElement) { ... }
      public Object getFirst() { return first; }
  }
  ```

### **7.2 影响**

1. **泛型类型的构造受限**

   - **错误示例**：

     ```java
     public class Stack<E> {
         private E[] elements = new E[10];  // ❌ 编译错误
     }
     ```

   - **解决方案**：

     ```java
     private Object[] elements = new Object[10];
     ```

2. **无法创建泛型数组**

   - **示例：使用 `ArrayList<E>` 代替数组**

     ```java
     public class Stack<E> {
         private ArrayList<E> elements = new ArrayList<>();
     }
     ```

## **8. 复习总结**

- **泛型 (Generics)** 允许编写通用、类型安全的代码，提高代码复用性。
- **泛型类和泛型方法** 使用 **类型参数** (`<T>`) 定义不同类型的代码结构。
- **通配符 (`? extends T` 和 `? super T`)** 用于泛型方法，使其适应不同类型的参数。
- **类型擦除 (Type Erasure)** 使泛型在运行时转换为 `Object`，导致一些限制，如不能创建泛型数组。
