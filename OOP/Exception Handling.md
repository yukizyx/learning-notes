# Java Exception Handling JAVA 异常处理机制

### 1. 异常处理简介 (Introduction to Exception Handling)

- 异常 (有问题时产生的一个对象)，用于处理程序运行时可能发生的错误。
- 通过异常处理，程序在遇到问题后可继续执行，而不是立即结束。

### 2. 何时使用异常处理

#### 适合

- 同步错误：数组越界、数值超级、除代为零、无效的参数

#### 不适合

- 异步事件：网络接口、磁盘 IO、鼠标/键盘操作

### 3. Java 异常关键字

| 关键字    | 作用                                                  |
| --------- | ----------------------------------------------------- |
| `try`     | 展示有可能报错的代码块，后必需跟随 `catch`，`finally` |
| `catch`   | 用于捕获异常，必须继 `try` 后                         |
| `finally` | 无论是否发生异常都会执行                              |
| `throw`   | 手动抛出异常                                          |
| `throws`  | 声明方法可能抛出异常，不是抛出异常                    |

### 4. Java 异常类结构

```
Object
 └── Throwable
     ├── Exception
     │    ├── IOException (checked)
     │    └── RuntimeException (unchecked)
     └── Error (系统级自动处理错误)
```

### 5. 异常类型

| 类型                | 特性                     | 示例                                      |
| ------------------- | ------------------------ | ----------------------------------------- |
| Checked Exception   | 编译时必须处理           | IOException, SQLException                 |
| Unchecked Exception | 程序员本身错误，不必声明 | NullPointerException, ArithmeticException |
| Error               | 系统级不可恢复错误       | OutOfMemoryError                          |

### 6. 抛出异常 / 捕获异常

#### 抛出:

```java
if (amount > balance) {
    throw new IllegalArgumentException("Amount exceeds balance");
}
```

#### 捕获:

```java
try {
    Scanner in = new Scanner(new File("data.txt"));
    int number = Integer.parseInt(in.next());
} catch (FileNotFoundException e) {
    e.printStackTrace();
} catch (NumberFormatException e) {
    System.out.println(e.getMessage());
}
```

#### 多异常同时捕获:

```java
catch (IOException | NumberFormatException e) {
    e.printStackTrace();
}
```

### 7. throws 声明 & 异常传播

```java
public void readData(String filename) throws FileNotFoundException {
    Scanner in = new Scanner(new File(filename));
}
```

- 这个方法未处理异常，把异常传给调用者处理

### 8. try-with-resources 自动资源关闭

- 适合需要 `close()` 的资源，如 PrintWriter, Scanner

```java
try (PrintWriter out = new PrintWriter("data.txt")) {
    out.println("Hello");
}
```

- 自动调用 `close()`，无论是否抛出异常

### 9. finally 代码块

- 无论 try 里是否抛异常，`finally` 中的代码都会执行
- 用于释放资源（文件，网络连接等）

### 10. 自定义异常类

```java
public class InsufficientFundsException extends IllegalArgumentException {
    public InsufficientFundsException() {}
    public InsufficientFundsException(String message) {
        super(message);
    }
}
```

### 11. 常见异常

| 异常                           | 解释                        |
| ------------------------------ | --------------------------- |
| ArrayIndexOutOfBoundsException | 访问数组超范图索引          |
| NullPointerException           | 对象为 null 时调用方法/属性 |
| ClassCastException             | 无法完成的类型转换          |
| InputMismatchException         | Scanner 读取的数据格式不符  |
| ArithmeticException            | 数学错误，如 1/0            |

### 12. 堆栈跟踪 (Stack Trace)

- `printStackTrace()` 显示异常给出错误时的方法调用链
- `getMessage()` 显示异常描述
- 用于调试和日志输出

### 13. 堆栈回滚 & 异常传播

- 如果异常未在当前方法中被捕获，则会继续上传给调用方法
- 并释放本地变量进行堆回滚
- 也可以重抛异常 (`throw e`) 上传处理

### 14. 链式异常 (Chained Exceptions)

- 在 catch 中抛出新异常时，之前异常信息会丢失
- Java 支持链式异常：

```java
Throwable getCause();
```

- 用于保存原始异常信息，便于调试
