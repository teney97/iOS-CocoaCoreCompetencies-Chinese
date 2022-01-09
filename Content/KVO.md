## KVO

原文：[Key-value observing](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/KVO.html#//apple_ref/doc/uid/TP40008195-CH16-SW1)

键值观察（KVO）是一种机制，当另一个对象的属性发生变化时，可以直接通知一个对象。KVO 是 App 内聚性的一个重要因素。它是遵循 Model-View-Controller 设计模式设计的 App 中对象之间的一种通信模式。例如，你可以使用它来同步 `Model 对象` 与 `View 和 Controller 层中的对象` 的状态。通常，`Controller 对象` 观察 `Model 对象`，`View 对象` 观察 `Controller 对象`  或  `Model 对象`。

> 注意：虽然 UIKit framework 的类一般不支持 KVO，但你仍然可以在自定义对象中实现它，包括自定义视图。

![](https://gitee.com/junteng/images/raw/master/img/20220109061947.png)

使用 KVO，一个对象可以观察另一个对象任何属性，包括简单特质（simple attributes）、一对一关系（to-one relationships）和一对多关系（to-many relationships）。对象可以查出属性的 new 值和 old 值是什么。一对多关系的观察者不仅被告知所做更改的类型，还被告知哪些对象参与了更改。

作为一种通知机制，KVO 与 [NSNotification](https://developer.apple.com/documentation/foundation/nsnotification)  和 [NSNotificationCenter](https://developer.apple.com/library/archive/documentation/LegacyTechnologies/WebObjects/WebObjects_3.5/Reference/Frameworks/ObjC/Foundation/Classes/NSNotificationCenter/Description.html#//apple_ref/occ/cl/NSNotificationCenter) 类提供的机制相似，但也有显著差异。当属性值发生变化时，KVO 通知不是向所有已注册为观察者的对象广播通知的中心对象，而是直接发送给观察者对象。

---

### 使用 KVO

根类 [NSObject](https://developer.apple.com/library/archive/documentation/LegacyTechnologies/WebObjects/WebObjects_3.5/Reference/Frameworks/ObjC/Foundation/Classes/NSObject/Description.html#//apple_ref/occ/cl/NSObject) 提供了 KVO 的基本实现，你应该很少需要覆写它。因此，所有 Cocoa 对象本质上都支持 KVO。要接收一个属性的 KVO 通知，你必须执行以下操作：

* 你必须确保被观察的类对于你要观察的属性是符合 KVO 的。

  符合 KVO 要求被观察对象的类也符合 KVC，并允许属性的自动观察者通知或实现属性的手动 KVO。

* 你需要调用  `addObserver:forKeyPath:options:context:` 方法，为被观察对象的属性添加一个观察者。

* 在观察者对象中，实现 `observeValueForKeyPath:ofObject:change:context:` 方法。当被观察对象的属性值发生变化时此方法会被调用。

### KVO 是绑定的一个组成部分（OS X）

Cocoa binding 是一种 OS X 技术，它允许你保持 Model 层与 View 层的值同步，而无需编写大量的“粘合代码”。通过 Interface Builder inspector，你可以在视图的属性和一段数据之间建立中介连接，“binding”它们，以便其中一个的更改反应在另一个中。KVO 连同 key-value encoding 和 key-value binding，都是对 Cocoa binding 有用的技术。 

---

### 相关

#### 前提文章

* [Key-value coding](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/KeyValueCoding.html#//apple_ref/doc/uid/TP40008195-CH25-SW1)

#### 相关文章

- [Model-View-Controller](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html#//apple_ref/doc/uid/TP40008195-CH32-SW1)
- [Dynamic binding](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/DynamicBinding.html#//apple_ref/doc/uid/TP40008195-CH15-SW1)

#### 最终讨论

* *[Key-Value Observing Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/KeyValueObserving/KeyValueObserving.html#//apple_ref/doc/uid/10000177i)*

#### 示例代码

- [SourceView: Using NSOutlineView with NSTreeController](https://developer.apple.com/library/archive/samplecode/SourceView/Introduction/Intro.html#//apple_ref/doc/uid/DTS10004441)
- [BindingsJoystick](https://developer.apple.com/library/archive/samplecode/BindingsJoystick/Introduction/Intro.html#//apple_ref/doc/uid/DTS10003684)

