## Nib 文件

原文：[Nib file](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/NibFile.html#//apple_ref/doc/uid/TP40008195-CH34-SW1)

nib 文件是一种特殊类型的资源文件，用于存储 iOS 和 Mac 应用程序的用户界面。nib 文件是一个 Interface Builder 文档。你可以使用 Interface Builder 来设计应用程序的可视部分（例如 windows 和 views），有时也可以配置非可视对象，例如你的应用程序使用 controller 对象来管理 windows 和 views。实际上，当你编辑 Interface Builder 文档时，你会创建一个对象图，然后在保存文件时将其归档。加载文件时，对象图是解档的。

nib 文件，和产生的对象图，可能包含占位符对象。这些对象用于引用文档之外的对象，但这些对象可能引用了文档中的对象，或者文档中的对象可能引用了这些对象。一个特殊的占位符是文件的所有者。

在运行时，使用 `loadNibNamed:owner:` 方法或其变体来加载 nib 文件。文件所由者是 nib 文件中作为该方法的 owner 参数传递的对象的占位符。在运行时加载文件时，在 Interface Builder 的 nib 文件中与文件所有者建立的任何连接都会重新建立。

iOS 使用 nib 作为支持 storyboards（故事板，iOS 用户界面设计布局格式）的实现细节。故事板允许您在一个画布上设计和可视化应用程序的整个用户界面。对于 iOS 开发人员，推荐使用故事板来设计用户界面。

---

### 相关

#### 前提文章

* [Object archiving](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Archiving.html#//apple_ref/doc/uid/TP40008195-CH1-SW1)
* [Object graph](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/ObjectGraph.html#//apple_ref/doc/uid/TP40008195-CH54-SW1)

#### 相关文章

- [Model-View-Controller](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html#//apple_ref/doc/uid/TP40008195-CH32-SW1)
- [Storyboard](https://developer.apple.com/library/archive/documentation/General/Conceptual/Devpedia-CocoaApp/Storyboard.html#//apple_ref/doc/uid/TP40009071-CH99)

#### 最终讨论

* [Nib Files](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/LoadingResources/CocoaNibs/CocoaNibs.html#//apple_ref/doc/uid/10000051i-CH4)

