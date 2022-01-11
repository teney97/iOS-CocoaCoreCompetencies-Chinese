## Block 对象

原文：[Block object](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Block.html#//apple_ref/doc/uid/TP40008195-CH3-SW1)

Block 对象是一个 C 级别的语法和运行时特性，它允许你编写函数表达式，这些函数表达式可以作为参数传递、可选地存储并由多个线程使用。函数表达式可以引用并且可以保留对局部变量的访问。在其他语言和环境中，Block 对象有时也称为 closure（闭包）或 lambda。当你想要创建可以像值一样传递的工作单元（即代码段）时，你可以使用 Block。Block 提供了更灵活的编程和更强大的功能。例如，你可以使用它们来编写回调或对集合中的所有元素执行操作。

---

### 声明 Block

在许多情况下，你使用的 Block 是 inline 的，因此你不需要声明它们。声明 Block 的语法类似于函数指针的标准语法，不同之处在于你使用插入符号 (`^`)  而不是星号指针 (`*`) 。例如，下面声明了一个变量 `aBlock`，它引用了一个需要三个参数并返回一个 `float` 值的块：

```objectivec
float (^aBlock)(const int*, int, float);
```

### 创建 Block

你可以使用插入符号 (`^`) 来指示 Block 表达式的开始，并使用分号（`;`）来指示 Block 表达式的结束。以下示例声明了一个简单的 Block 并将其分配给先前声明的 Block 变量 (`oneFrom`)：

```objectivec
int (^oneFrom)(int);
 
oneFrom = ^(int anInt) {
    return anInt - 1;
};
```

需要结束分号（`;`）作为标准 C 行尾标记。

如果你没有显示声明一个 Block 表达式的返回值，它可以从 Block 的内容中自动推断出来。

### Block - 可变变量

你可以将 `__block` 修饰符修饰 Block 所在作用域的局部变量，以表示此类变量通过引用在 Block 中提供，因此是可变的。同一作用域内的 Block 共享 `__block` 变量。当你需要在 Block 中修改局部变量时，你需要使用 `__block` 修饰符。

### 使用 Block

如果将 Block 声明为变量，则可以像使用函数一样使用它。以下示例将打印 9 作为输出。

```objectivec
printf("%d\n", oneFrom(10));
```

通常，你将 Block 作为参数传递给函数或方法，在这些情况下，你通常会创建 inline Block。

以下示例通过遍历判断 `NSSet` 对象是否包含由局部变量 `string` 指定的单词，如果包含，则将另一个局部变量  `found` 的值设置为 YES 并停止遍历。在这个例子中，`found` 被声明为一个 `__block` 变量。

```objectivec
__block BOOL found = NO;
NSSet *aSet = [NSSet setWithObjects: @"Alpha", @"Beta", @"Gamma", @"X", nil];
NSString *string = @"gamma";
 
[aSet enumerateObjectsUsingBlock:^(id obj, BOOL *stop) {
    if ([obj localizedCaseInsensitiveCompare:string] == NSOrderedSame) {
        *stop = YES;
        found = YES;
    }
}];
 
// At this point, found == YES
```

在此示例中，该 Block 包含在方法的参数列表中。该 Block 还使用栈局部变量。

### 比较操作

在 Cocoa 环境中对 Block 执行的更常见的操作之一是比较两个对象，例如，对 array 的内容进行排序。Objective-C 运行时定义了一个 Block 类型 `NSComparator`，用于这些比较。

---

### 相关

#### 前提文章

* [Message](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Message.html#//apple_ref/doc/uid/TP40008195-CH59-SW1)

#### 相关文章

- [Enumeration](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Enumeration.html#//apple_ref/doc/uid/TP40008195-CH17-SW1)

#### 最终讨论

* [Working with Blocks](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/WorkingwithBlocks/WorkingwithBlocks.html#//apple_ref/doc/uid/TP40011210-CH8)
