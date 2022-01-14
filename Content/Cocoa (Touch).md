## Cocoa (Touch)

原文：[Cocoa (Touch)](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Cocoa.html#//apple_ref/doc/uid/TP40008195-CH9-SW1)

Cocoa 和 Cocoa Touch 分别是 OS X 和 iOS 的应用程序开发环境。Cocoa 和 Cocoa Touch 都包含 Objective-C 运行时和两个核心框架：

* Cocoa 包含 Foundation 和 AppKit 框架，用于开发在 OS X 上运行的应用程序
* Cocoa Touch 包含 Foundation 和 UIKit 框架，用于开发在 iOS 上运行的应用程序

> 注意：术语 “Cocoa” 用于泛指任何基于 Objective-C 运行时并从根类 `NSObject` 的类或者对象。当提到使用相应平台的任何编程接口的应用程序开发时，也使用术语 “Cocoa” 或 “Cocoa Touch”。

---

### 框架

Foundation 框架实现了根类 `NSObject`，它定义了基本的对象行为。它实现了表示基本类型（例如，字符串和数值）和集合（例如，数组和字典）的类。Foundation 还提供了用于国际化、对象持久性、文件管理和 XML 处理的工具。你可以使用它的类来访问底层的系统实体和服务，例如端口、线程、锁和进程。Foundation 基于 Core Foundation 框架，该框架发布了一个 procedural (ANSI C) interface。

你使用 AppKit 和 UIKit 框架来开发应用程序的用户界面。这两个框架在用途上是相同的，但是特定于一个平台。它们包括用于事件处理、绘图、图像处理、文本处理、排版和应用程序间数据传输的类。它们还包括用户界面元素，如 table views、sliders、buttons、text fields 和 alert dialogs。

### 语言

Objective-C 是开发 Cocoa 和 Cocoa Touch 应用程序的原生主要语言。但是，Cocoa 和 Cocoa Touch 应用程序的项目可能包含 C++ 和 ANSI C 代码。此外，你可以使用桥接到 Objective-C 运行时的脚本语言开发 Cocoa 应用程序，例如 PyObjC 和 RubyCocoa。

---

### 相关

#### 前提文章

None

#### 相关文章

- [Root class](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/RootClass.html#//apple_ref/doc/uid/TP40008195-CH46-SW1)
- [Objective-C](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/ObjectiveC.html#//apple_ref/doc/uid/TP40008195-CH43-SW1)[](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Enumeration.html#//apple_ref/doc/uid/TP40008195-CH17-SW1)

#### 最终讨论

None