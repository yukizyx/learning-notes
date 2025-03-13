## **1. Java 集合框架 (Collections Framework) 概述**

### **1.1 集合框架的作用**

- **Java 集合框架 (Collections Framework)** 提供了存储、管理和操作**对象**的通用架构。
- 主要包含：
  - **接口 (Interfaces)**：定义集合的通用操作，如 `List`、`Set`、`Queue`、`Map`。
  - **实现类 (Classes)**：提供不同的数据结构，如 `ArrayList`、`HashSet`、`LinkedList`。
  - **算法 (Algorithms)**：提供搜索、排序等操作，如 `Collections.sort()`。

### **1.2 Java 集合框架的优点**

✅ **统一 API 设计**：所有集合都实现 `Collection` 或 `Map` 接口。

✅ **提高开发效率**：程序员专注于使用集合，而不是底层数据结构实现。

✅ **高效的性能**：提供优化的数据结构和算法，如哈希表、二叉树等。

## **2. List 接口 (List Interface)**

### **2.1 List 主要特点**

- **有序 (Ordered)**：元素按插入顺序存储。
- **允许重复 (Duplicates Allowed)**：可以包含重复的元素。
- **索引访问 (Indexed Access)**：可通过索引 (`get(int index)`) 访问元素。
- **常见实现**：
  - `ArrayList`：动态数组，支持快速随机访问 (`O(1)`)，但插入/删除操作较慢 (`O(n)`)。
  - `LinkedList`：双向链表，插入/删除操作快 (`O(1)`)，但随机访问慢 (`O(n)`)。

### **2.2 List 使用示例**

```java
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
System.out.println(names.get(0)); // 输出：Alice
```

## **3. Set 接口 (Set Interface)**

### **3.1 Set 主要特点**

- **不允许重复元素 (No Duplicates Allowed)**。
- **无序存储 (Unordered Storage)**（`HashSet`），或**排序存储 (Sorted Order)**（`TreeSet`）。
- **常见实现**：
  - `HashSet`：基于哈希表，提供 `O(1)` 时间复杂度的插入、删除、查找操作。
  - `TreeSet`：基于**红黑树**，元素有序存储，操作复杂度为 `O(log n)`。

### **3.2 Set 使用示例**

```java
Set<String> uniqueNames = new HashSet<>();
uniqueNames.add("Alice");
uniqueNames.add("Bob");
uniqueNames.add("Alice");  // 不会添加重复元素
System.out.println(uniqueNames.size());  // 输出：
```

---

## **4. Queue 接口 (Queue Interface)**

### **4.1 Queue 主要特点**

- **FIFO (First-In-First-Out) 先进先出**，元素从队尾插入，从队首删除。
- **常见实现**：
  - `LinkedList`：实现队列操作（`add()`，`remove()`）。
  - `PriorityQueue`：元素按优先级排序（默认升序），用于任务调度等场景。

### **4.2 Queue 使用示例**

```java
Queue<String> queue = new LinkedList<>();
queue.add("Task 1");
queue.add("Task 2");
System.out.println(queue.remove());  // 输出：Task 1
```

## **5. Map 接口 (Map Interface)**

### **5.1 Map 主要特点**

- **键值对存储 (Key-Value Pairs)**，通过键访问值。
- **键唯一 (Unique Keys)**，值可以重复。
- **常见实现**：
  - `HashMap`：基于哈希表，提供 `O(1)` 的查找性能。
  - `TreeMap`：基于红黑树，键有序存储，操作复杂度 `O(log n)`。

### **5.2 Map 使用示例**

```java
java
复制编辑
Map<String, Integer> scores = new HashMap<>();
scores.put("Alice", 90);
scores.put("Bob", 85);
System.out.println(scores.get("Alice"));  // 输出：90
```

## **6. 迭代器 (Iterator)**

### **6.1 迭代器的作用**

- **用于遍历集合**，而无需知道底层数据结构。
- **主要方法**：
  - `hasNext()`：检查是否有下一个元素。
  - `next()`：获取下一个元素。
  - `remove()`：删除当前元素。

### **6.2 迭代器使用示例**

```java
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");

Iterator<String> iterator = names.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

## **7. Java 集合的排序与搜索**

### **7.1 排序 (Sorting)**

- `Collections.sort(List<T> list)`：按**自然顺序 (Comparable)** 排序。
- `Collections.sort(List<T> list, Comparator<T> comparator)`：按自定义顺序排序。

```java

List<Integer> numbers = new ArrayList<>(Arrays.asList(3, 1, 4, 2));
Collections.sort(numbers);  // 默认升序
System.out.println(numbers);  // 输出：[1, 2, 3, 4
```

### **7.2 搜索 (Searching)**

- **二分查找 (Binary Search)** 需要**排序的列表**：

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
int index = Collections.binarySearch(numbers, 3);
System.out.println(index);  // 输出：2
```

## **8. 选择合适的集合 (Choosing a Collection)**

✅ **如果需要存储** **唯一值**，选择 `Set` (如 `HashSet`、`TreeSet`)。

✅ **如果需要快速随机访问**，选择 `ArrayList`。

✅ **如果需要频繁插入/删除**，选择 `LinkedList`。

✅ **如果需要** **键值对存储**，选择 `Map` (如 `HashMap`、`TreeMap`)。

✅ **如果需要** **FIFO 队列**，选择 `Queue` (如 `LinkedList`、`PriorityQueue`)。

## **9. Java 集合框架总结**

| **集合类型** | **主要特点**       | **常见实现**                  |
| ------------ | ------------------ | ----------------------------- |
| `List`       | 有序，可重复       | `ArrayList`、`LinkedList`     |
| `Set`        | 无序，不可重复     | `HashSet`、`TreeSet`          |
| `Queue`      | 先进先出 (FIFO)    | `LinkedList`、`PriorityQueue` |
| `Map`        | 键值对存储，键唯一 | `HashMap`、`TreeMap`          |
