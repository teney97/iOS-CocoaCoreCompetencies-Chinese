## 属性列表 (Plist)

原文：[Property list](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/PropertyList.html#//apple_ref/doc/uid/TP40008195-CH44-SW1)

Plist 是对象层次结构的一种表示，这些对象可以存储在文件系统中，并在以后重新构建。Plist 为应用程序提供了一种轻量级和可移植的方式来存储少量数据。它们是由特定类型的对象组成的数据层次结构，它们实际上是一个对象图。Plist 很容易通过编程方式创建，甚至更容易序列化为持久的表示形式。应用程序可以稍后将静态表示读入内存，并重新创建对象的原始层次结构。Cocoa Foundation 和 Core Foundation 都有与 Plist 序列化和反序列化相关的 API。

---

### Plist 类型和对象

Plist 只包含某些类型的数据：dictionary、array、string、number（integer 和 float）、date、binary data 和 Boolean value。dictionary 和 array 是特殊类型，因为它们是集合；它们可以包含一种或多种数据类型，包括其它 dictionary 和 array。对象的这种分层嵌套创建了对象图。抽象数据类型有对应的 Foundation 类、Core Foundation 类型以及用于集合对象和值对象的 XML 元素，如下表所示：

| Abstract type        | Foundation framework class                                   | Core Foundation type                                         | XML element             |
| :------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :---------------------- |
| Array                | `NSArray`                                                    | `CFArrayRef`                                                 | `<array>`               |
| Dictionary           | `NSDictionary`                                               | `CFDictionaryRef`                                            | `<dict>`                |
| String               | `NSString`                                                   | `CFStringRef`                                                | `<string>`              |
| Data                 | `NSData`                                                     | `CFDataRef`                                                  | `<data>`                |
| Date                 | `NSDate`                                                     | `CFDateRef`                                                  | `<date>`                |
| Integer              | `NSNumber` (`intValue` 32-bit)<br>`NSNumber` (`integerValue` 64-bit) | `CFNumberRef` (`kCFNumberSInt32Type`)<br/>`CFNumberRef` (`kCFNumberSInt64Type`) | `<integer>`             |
| Floating-point value | `NSNumber` (`floatValue` 32-bit)<br/>`NSNumber` (`doubleValue` 64-bit) | `CFNumberRef` (`kCFNumberFloat32Type`)<br/>`CFNumberRef` (`kCFNumberFloat64Type`) | `<real>`                |
| Boolean              | `NSNumber` (`boolValue`)                                     | `CFBooleanRef`                                               | `<true/>` or `<false/>` |

这些类的实例统称为 Plist 对象。例如 `NSMutableDictionary` 实例是 Plist 对象，`NSNumber` 实例、`NSString` 实例等也是如此。要使 Plist 有效，对象图中的所有对象都必须是 Plist 对象。

### Plist 的最佳实践

你可以用 XML 和二进制格式编写 Plist。二进制格式比 XML 格式更紧凑，因此效率更高，在大多数情况下都推荐使用。但是，如果需要，你可以手动编辑 XML Plist。Plist 文件的文件扩展名为 `plist`。

你不应该使用 Plist 来存储大型、复杂的对象图，尤其是当对象具有可变的可变性设置时。并且你不能使用 Plist 来存储架构不支持的对象，例如 Model 对象。对于这些情况，请改用归档。虽然 Plist 可以包含 `NSData` 对象，但最好不要在 Plist 中使用 `NSData` 对象来保存大量的二进制数据。

### Plist 序列化

要序列化和反序列化 Plist，请调用 [NSPropertyListSerialization](https://developer.apple.com/documentation/foundation/nspropertylistserialization) 类的适当类方法，或者，如果使用 Core Foundation，则调用与不透明类型 [CFPropertyListRef](https://developer.apple.com/documentation/corefoundation/cfpropertylistref) 相关的函数。在 Cocoa 中，序列化的输出是 `NSData` 对象的形式。因此，你可以使用该类的方法（例如 [writeToFile:atomically:](https://developer.apple.com/library/archive/documentation/LegacyTechnologies/WebObjects/WebObjects_3.5/Reference/Frameworks/ObjC/Foundation/Classes/NSDataClassCluster/Description.html#//apple_ref/occ/instm/NSData/writeToFile:atomically:)）将数据写入文件系统，并使用适当的 `NSData` 类工厂内存将其读回内存。然后，当你反序列化它时，你可以为 Plist 指定可变性选项。

---

### 相关

#### 前提文章

- [Object graph](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/ObjectGraph.html#//apple_ref/doc/uid/TP40008195-CH54-SW1)
- [Collection](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Collection.html#//apple_ref/doc/uid/TP40008195-CH10-SW1)

#### 相关文章

- [Object archiving](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Archiving.html#//apple_ref/doc/uid/TP40008195-CH1-SW1)
- [Object mutability](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/ObjectMutability.html#//apple_ref/doc/uid/TP40008195-CH42-SW1)

#### 最终讨论

* *[Property List Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html#//apple_ref/doc/uid/10000048i)*

### 示例代码

- [People](https://developer.apple.com/library/archive/samplecode/SyncServices_People/Introduction/Intro.html#//apple_ref/doc/uid/DTS40009050)

