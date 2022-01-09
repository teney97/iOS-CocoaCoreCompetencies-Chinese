## KVC

原文：[Key-value coding](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/KeyValueCoding.html#//apple_ref/doc/uid/TP40008195-CH25-SW1)

键值编码（KVC）是一种使用字符串标识符间接访问对象属性和关系的机制。它支撑着 Cocoa 编程的几种特殊机制和技术，或与其存在关联。其中包括 Core Data、 application scriptability、the bindings technology、the language feature of declared properties 等（Scriptability 和 bindings 特定于 OS X 上的 Cocoa）。你还可以使用 KVC 来简化程序代码。

---

### 对象属性和 KVC

KVC 的核心是属性的一般概念。属性是指对象封装的状态单元。属性可以是以下两种通用类型之一：

* 一个特质（attribute）（例如：`name`、`title`、`subtotal`、或 `textColor`）
* 与其他对象的关系。关系可以是一对一（to-one relationship），也可以是一对多（to-many relationship）。一对多关系的值通常是 array 或 set，具体取决于关系是有序的还是无序的。

KVC 通过一个 key 来定位一个对象的属性，key 是一个字符串标识符。key 通常对应于对象定义的存取方法或实例变量的名称。key 必须符合某些约定：

*  必须采用 ASCII 编码
* 以小写字母开头
* 不能有空格

key path 是由一串由点分割的 keys 组成的字符串，用于指定要遍历的对象属性序列。序列中第一个 key 的属性相对于指定的对象（下图中的 `employee1`），后续的每个 key 都是相对于前一个属性的值进行计算的。

![](https://gitee.com/junteng/images/raw/master/img/20220109005854.png)

### 使类符合 KVC

`NSKeyValueCoding` 非正式协议使 KVC 变成可能。它的两个方法 `valueForKey:` 和 `setValue:forKey:` 特别重要，它们可以根据给定 key 获取和设置属性的值。`NSObject` 提供了这些方法的默认实现，如果一个类符合 KVC，它可以依赖这个实现。

如何使属性符合 KVC 取决于该属性是一个特质、一个关系（一对一或一对多）。对于特质和一对一关系，类必须按照给定的优先顺序实现以下的至少一个（key 指的是属性 key）：

1. 该类有一个名为 `key` 的已声明的属性
2. 它实现了名为 `key` 的存取方法，getter 为 `key`，setter 为 `setKey:`。（如果属性是布尔类型，则 getter 方法的形式为 `isKey`）
3. 它声明了一个 `key` 或 `_key` 形式的实例变量

实现符合 KVC 的一对多关系是一个更复杂的过程。请参阅明确描述 KVC 的文档，以了解这个过程是什么。

---

### 相关

#### 前提文章

* [Object modeling](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/ObjectModeling.html#//apple_ref/doc/uid/TP40008195-CH41-SW1)
* [Accessor method](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/AccessorMethod.html#//apple_ref/doc/uid/TP40008195-CH2-SW1)

#### 相关文章

- [Declared property](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/DeclaredProperty.html#//apple_ref/doc/uid/TP40008195-CH13-SW1)

#### 最终讨论

* *[Key-Value Coding Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/KeyValueCoding/index.html#//apple_ref/doc/uid/10000107i)*



 