# Java 文件与输入/输出流 (IO/NIO)

### 1. Java 文件与流的基本概念 (Files & Streams)

- 程序中的变量和数组是暂时存储，程序结束后数据会丢失
- 如果需要长期保存，必须使用文件 (files)
- Java 将文件视为字节 (byte) 或字符 (char) 流的序列

### 2. 文件路径与目录结构

- 文件系统是树状结构，包括
  - 文件 files
  - 目录 directories
- 当前工作目录可通过以下方式查看

```java
System.getProperty("user.dir");
Paths.get("").toAbsolutePath();
```

- Java 支持跨平台路径分隔符
  - Windows: `\\`
  - Linux/macOS: `/`
  - Java 中都支持，`\\` 需进行转义

### 3. 路径类型

| 路径类型               | 说明                             |
| ---------------------- | -------------------------------- |
| 相对路径 Relative Path | 相对于当前目录，易受目录变化影响 |
| 绝对路径 Absolute Path | 从系统根目录开始，稳定、跨环境   |

### 4. Java IO 结构: java.io 包

| 类型   | 抽象类                     | 用途                         |
| ------ | -------------------------- | ---------------------------- |
| 字节流 | InputStream / OutputStream | 处理二进制数据，如图片、音频 |
| 字符流 | Reader / Writer            | 处理文本数据                 |

#### 常用类:

- BufferedReader / BufferedWriter
- Scanner (input)
- Formatter / PrintWriter (output)
- InputStreamReader / OutputStreamWriter 字节流转字符流

### 5. File 类 (java.io.File)

- File 类用于 **查看文件属性**，而非读写

```java
file.isFile(), file.exists(), file.length()
file.canRead(), file.canWrite()
file.mkdir(), file.renameTo()
file.toURI(), file.getPath()
```

- 可以通过 `file.toPath()` 与 NIO 同步

### 6. NIO (java.nio.file 包)

| 类/ 接口        | 用途                     |
| --------------- | ------------------------ |
| Path            | 表示文件或目录路径       |
| Paths           | 创建 Path 实例的工具类   |
| Files           | 操作文件或目录的静态方法 |
| DirectoryStream | 用于遍历目录内容         |

#### Files 常用方法:

```java
Files.exists(path);
Files.copy(src, dest);
Files.delete(path);
```

### 7. 顺序文本文件 (Sequential Text Files)

- 以字符流格式保存，可被编辑器打开
- 通常按照 "记录字段顺序" 保存

#### 写入:

```java
Formatter out = new Formatter("clients.txt");
out.format("%s %d\n", name, age);
out.close();
```

#### 读取:

```java
Scanner in = new Scanner(new File("clients.txt"));
while (in.hasNext()) {
    String name = in.next();
    int age = in.nextInt();
}
in.close();
```

### 8. 文件异常处理

| 异常类型               | 解释                       |
| ---------------------- | -------------------------- |
| FileNotFoundException  | 文件不存在 / 无法创建文件  |
| SecurityException      | 无权写入文件               |
| NoSuchElementException | Scanner 读取数据时格式不符 |
| IllegalStateException  | 关闭后继续操作流           |

### 9. 文件更新与限制

- Java 中文本文件 **不支持原地更改**，如替换 "White" 为 "Worthington"
- 新内容长度不等于原文，会破坏文本结构
- 解决方案:
  - 读入全部，修改后重写全文件

### 10. Java 默认标准流

| 流         | 说明               |
| ---------- | ------------------ |
| System.in  | 标准输入（键盘）   |
| System.out | 标准输出（控制台） |
| System.err | 标准错误输出       |

- 可通过 `System.setIn()/setOut()/setErr()` 重定向

### 11. URI 与文件路径

- URI 是统一资源标识符，可表示本地路径

```java
file://C:/data.txt
file:/home/user/data.txt
```

- 可通过 `Paths.get(URI)` 创建 Path 对象

### 12. Java IO vs NIO 总结

| 对比项   | java.io          | java.nio               |
| -------- | ---------------- | ---------------------- |
| 类型     | 面向流           | 面向缓冲区             |
| 特点     | 简单，适合小文件 | 性能高，支持非阻塞 IO  |
| 文件类   | File             | Path, Files            |
| 适用场景 | 日常文本读写     | 大文件处理，环境规模化 |
