# **Java Swing**

## **1. Java Swing 概述**

### **1.1 什么是 Swing？**

- **Swing** 是 Java 提供的 **GUI (Graphical User Interface)** 框架，允许开发者构建**跨平台的窗口应用程序**。
- 它是 **Java Foundation Classes (JFC)** 的一部分，作为 **AWT (Abstract Window Toolkit)** 的改进版本。

### **1.2 Swing 的主要特点**

✅ **轻量级 (Lightweight)**：不依赖操作系统的 GUI 组件，全部由 Java 代码实现。

✅ **丰富的控件 (Rich Controls)**：提供 `JButton`、`JLabel`、`JTextField`、`JTable` 等多种 UI 组件。

✅ **高度可定制 (Highly Customizable)**：可以自由更改组件外观 (`Look and Feel`)。

✅ **MVC 设计模式**：采用 **Model-View-Controller** 结构，实现 UI 和数据的分离。

## **2. GUI 布局管理 (Layout Management)**

### **2.1 什么是布局管理器？**

- 布局管理器 (`Layout Manager`) 负责自动排列 Swing 组件，使其适应不同窗口大小。
- Java 提供多种布局管理器，如：
  - **`BorderLayout`**：适用于 **五个区域布局** (`NORTH`, `SOUTH`, `EAST`, `WEST`, `CENTER`)。
  - **`GridLayout`**：网格布局，适用于 **等大小组件**。
  - **`FlowLayout`**：按组件添加顺序排列，默认用于 `JPanel`。
  - **`BoxLayout`**：垂直/水平对齐组件，适用于 **表单布局**。

### **2.2 `BorderLayout` 示例**

```java
JPanel panel = new JPanel();
panel.setLayout(new BorderLayout());
panel.add(new JButton("North"), BorderLayout.NORTH);
panel.add(new JButton("Center"), BorderLayout.CENTER);
```

### **2.3 `GridLayout` 示例**

```java
JPanel panel = new JPanel();
panel.setLayout(new GridLayout(2, 3)); // 2 行 3 列
panel.add(new JButton("1"));
panel.add(new JButton("2"));
panel.add(new JButton("3"));
panel.add(new JButton("4"));
panel.add(new JButton("5"));
panel.add(new JButton("6"));
```

## **3. 核心 Swing 组件**

### **3.1 `JFrame` 和 `JPanel`**

- `JFrame`：主窗口，可包含 `JPanel` 作为子容器。
- `JPanel`：用于 **组织多个组件**。

**示例**：

```java
JFrame frame = new JFrame("My Window");
JPanel panel = new JPanel();
panel.add(new JButton("Click Me"));
frame.add(panel);
frame.setSize(400, 300);
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
frame.setVisible(true)
```

### **3.2 `JLabel` 和 `JButton`**

- `JLabel` 用于显示文本或图片。
- `JButton` 用于创建 **按钮**，并可添加 **事件监听器** 处理点击事件。

**示例**：

```java
JLabel label = new JLabel("Hello, World!");
JButton button = new JButton("Click Me");
button.addActionListener(e -> label.setText("Button Clicked!"));
```

### **3.3 `JTextField` 和 `JTextArea`**

- `JTextField`：**单行输入框**。
- `JTextArea`：**多行文本输入框**。

**示例**：

```java
JTextField textField = new JTextField(20); // 20 个字符宽度
JTextArea textArea = new JTextArea(5, 20); // 5 行 20 列
textArea.setEditable(false); // 只读模式
```

### **3.4 `JCheckBox` 和 `JRadioButton`**

- `JCheckBox`：**多选框**（可以同时选中多个）。
- `JRadioButton`：**单选框**（只能选中一个，需要 `ButtonGroup` ）。

**示例**：

```java
JCheckBox checkBox1 = new JCheckBox("Bold");
JCheckBox checkBox2 = new JCheckBox("Italic");

JRadioButton smallButton = new JRadioButton("Small");
JRadioButton largeButton = new JRadioButton("Large");
ButtonGroup group = new ButtonGroup();
group.add(smallButton);
group.add(largeButton);
```

### **3.5 `JComboBox`（下拉菜单）**

- 适用于 **选择多个选项之一**。

**示例**：

```java
JComboBox<String> comboBox = new JComboBox<>();
comboBox.addItem("Option 1");
comboBox.addItem("Option 2");
comboBox.addItem("Option 3");
```

## **4. 事件处理 (Event Handling)**

### **4.1 监听用户输入**

- Java 使用 **`ActionListener`** 处理按钮点击事件。
- `getText()` 方法用于获取文本输入框内容。

**示例**：

```java
JTextField textField = new JTextField(10);
JButton button = new JButton("Submit");
button.addActionListener(e -> {
    String input = textField.getText();
    System.out.println("User input: " + input);
});
```

## **5. 进阶 UI 组件**

### **5.1 `JScrollPane`（滚动面板）**

- **适用于 `JTextArea`、`JList` 等超出窗口大小的内容。**

**示例**：

```java
JTextArea textArea = new JTextArea(10, 30);
JScrollPane scrollPane = new JScrollPane(textArea);
```

### **5.2 `JMenuBar`（菜单栏）**

- **用于创建应用程序菜单（文件、编辑等）。**

**示例**：

```java
JMenuBar menuBar = new JMenuBar();
JMenu fileMenu = new JMenu("File");
JMenuItem exitItem = new JMenuItem("Exit");
exitItem.addActionListener(e -> System.exit(0));

fileMenu.add(exitItem);
menuBar.add(fileMenu);
```

### **5.3 `JSlider`（滑动条）**

- **用于调整数值（如音量、颜色选择）。**

**示例**：

```java
JSlider slider = new JSlider(0, 100, 50); // 最小 0，最大 100，默认 50
```

## **6. Java Swing 编程最佳实践**

✅ **使用 `SwingUtilities.invokeLater()` 进行 UI 更新，避免主线程阻塞。**

✅ **优先使用 `JPanel` 组织组件，提高代码可读性。**

✅ **避免使用 `setBounds()` 进行手动布局，应使用 `LayoutManager`。**

✅ **使用 `JScrollPane` 处理超出窗口大小的内容，避免 UI 显示问题。**

## **7. Java Swing 复习总结**

| **组件类型**    | **描述**      | **示例组件**                           |
| --------------- | ------------- | -------------------------------------- |
| **窗口**        | 主应用窗口    | `JFrame`                               |
| **容器**        | 组织组件      | `JPanel`                               |
| **标签**        | 显示文本/图片 | `JLabel`                               |
| **输入框**      | 文本输入      | `JTextField`, `JTextArea`              |
| **按钮**        | 交互操作      | `JButton`, `JCheckBox`, `JRadioButton` |
| **菜单**        | 菜单项        | `JMenuBar`, `JMenu`, `JMenuItem`       |
| **列表 & 选择** | 选择选项      | `JComboBox`, `JList`                   |
| **滚动条**      | 处理超大内容  | `JScrollPane`                          |
| **滑块**        | 数值调整      | `JSlider`                              |
