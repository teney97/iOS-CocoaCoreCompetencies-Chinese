## MVC

原文：[Model-View-Controller](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html#//apple_ref/doc/uid/TP40008195-CH32-SW1)

Model-View-Controller (MVC) 设计模式为应用程序中的对象分配了三种角色：Model、View、Controller。该模式不仅定义了对象在应用程序中扮演的角色，还定义了对象之间通信的方式。这三种类型的对象都通过抽象边界与其他类型的对象分隔开来，并通过这些边界与其他类型的对象通信。应用程序中某种 MVC 类型的对象集合有时被称为一个层 —— 例如 Model 层。

MVC 是 Cocoa 应用程序良好设计的核心。采用这种模式的好处很多。这让对象往往更易于重用，并且它们的接口往往被更好地定义。具有 MVC 设计的应用程序也比其他应用程序更容易扩展。此外，许多 Cocoa 技术和架构都是基于 MVC 的，并要求你的自定义对象扮演 MVC 的角色之一。

![](https://gitee.com/junteng/images/raw/master/img/20220114212040.png)

---

### Model

Model 对象封装了特定的数据，并定义了操作和处理该数据的逻辑和计算。例如，Model 对象可能代表游戏中的角色或通讯录中的联系人。一个 Model 对象可以与其他 Model 对象具有一对一或一对多的关系，因此有时应用程序的 Model 层实际上是一个或多个对象图。应用程序持久状态的大部分数据（无论该持久状态存储在文件还是数据库中），在数据加载到应用程序后，都应该驻留在 Model 对象中。因为 Model 对象表示与特定问题领域相关的东西，所以它们可以在类似的问题领域中重用。理想情况下，Model 对象应该与显示其数据的 View 对象没有明确的连接，并允许用户编辑数据，它不应该关心用户界面和表示问题。

**通信**：View 层中创建或修改数据的用户操作通过 Controller 对象进行通信，然后由 Controller 对象负责创建或更新 Model 对象。当 Model 对象发生变化时（例如，通过网络请求到新数据），它会通知 Controller 对象，Controller 对象会更新相应的 View 对象。

### View

View 对象是用户可以看到的对象。一个 View 对象知道如何绘制自己，并且能够响应用户的操作。View 对象的主要目的是显示来自 Model 对象的数据，并支持对数据的编辑。尽管如此，在 MVC 应用程序中，View 对象通常与 Model 对象解耦。

因为你通常重用和重新配置它们，所以 View 对象提供了应用程序之间的一致性。UIKit 和 AppKit 框架都提供了 View 类的集合，而 Interface Builder 在其库中提供了许多 View 对象。

**通信**：View 对象通过 Controller 对象了解 Model 数据的变化，并通过 Controller 对象将用户发起的更改（例如，在 textfield 中输入的文本）传达给 Model 对象。

### Controller

Controller 对象在一个或多个 View 对象和一个或多个 Model 对象之间充当中介。因此，Controller 对象是一个管道，View 对象通过它了解 Model 对象的变化，反之亦然。Controller 对象还可以执行设置和协调任务，并管理其他对象的生命周期。

**通信**：Controller 对象解释在 View 对象中进行的用户操作，并将新的或更改的数据传达给 Model 层。当 Model 对象发生变化时，Controller 对象会将新的 Model 数据传递给 View 对象，以便它们可以显示它。

---

### 相关

#### 前提文章

* [Message](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Message.html#//apple_ref/doc/uid/TP40008195-CH59-SW1)

#### 相关文章

- [Model object](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/ModelObject.html#//apple_ref/doc/uid/TP40008195-CH31-SW1)
- [Controller object](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/ControllerObject.html#//apple_ref/doc/uid/TP40008195-CH11-SW1)

#### 最终讨论

* [Model-View-Controller](https://developer.apple.com/library/archive/documentation/General/Conceptual/CocoaEncyclopedia/Model-View-Controller/Model-View-Controller.html#//apple_ref/doc/uid/TP40010810-CH14)















