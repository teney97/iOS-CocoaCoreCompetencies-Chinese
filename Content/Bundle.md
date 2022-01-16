## Bundle

原文：[Bundle](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Bundle.html#//apple_ref/doc/uid/TP40008195-CH4-SW1)

Bundle 是文件系统中的一个目录，它将可执行代码和相关资源（例如图像和声音）组合在一个地方。在 iOS 和 OS X 中，应用程序、框架、插件和其他类型的软件都是 Bundle。Bundle 是一个具有标准化层次结构的目录，其中包含可执行代码和该代码使用的资源。Foundation 和 Core Foundation 提供了用于在 Bundle 中定位和加载代码和资源的工具。

> **注意** ：在 iOS 上，应用程序是第三方开发人员唯一可以创建的 Bundle 类型。

Bundle 给用户和开发者带来了一些好处。它们使安装或重新安装应用程序或其他软件变得简单，只需将其从一个位置移动到另一个位置。Bundle 也是国际化的一个重要因素。你将本地化资源存储在一个 Bundle 的特别命名的子目录中；程序化工具在与用户语言偏好相对应的位置寻找本地化资源。

---

### Bundle 的结构与内容

一个 Bundle 可以包含可执行代码、图像、声音、nib 文件、私有框架和库、插件、可加载 Bundle 或任何其他类型的代码或资源。它还包含一个称为信息属性列表（`Info.plist`）的运行时配置文件。每一项在 Bundle 结构中都有其适当的位置。图像、声音和 nib 文件等资源存放在 `Resources` 子目录中。它们可以是本地化的或非本地化的。本地化文件（包括字符串文件，它们是本地化字符串的集合）被放在 `Resources` 的子目录中，该子目录扩展名为 `lproj`，名称对应于一种语言，可能还对应于区域设置。 

![](https://gitee.com/junteng/images/raw/master/img/20220116172556.png)

### 访问 Bundle 资源

每个应用程序都有一个 main bundle，它包含应用程序代码。当用户启动应用程序时，应用程序会在 main bundle 中找到它立即需要的代码和资源，并将它们加载到内存中。然后，应用程序可以根据需要从 main bundle 或  subordinate bundles 中动态（和惰性地）加载代码和资源。

[NSBundle](https://developer.apple.com/library/archive/documentation/LegacyTechnologies/WebObjects/WebObjects_3.5/Reference/Frameworks/ObjC/Foundation/Classes/NSBundle/Description.html#//apple_ref/occ/cl/NSBundle) 类，以及 [Core Foundation](https://developer.apple.com/documentation/corefoundation/cfbundle) 为 C 代码提供的 `CFBundleRef` 类型提供了在 Bundle 中定位资源的方法。在 Objective-C 中，你首先必须获得一个 `NSBundle` 实例，它与物理 Bundle 相对应。要获取应用程序的 main bundle，调用类方法 [mainBundle](https://developer.apple.com/library/archive/documentation/LegacyTechnologies/WebObjects/WebObjects_3.5/Reference/Frameworks/ObjC/Foundation/Classes/NSBundle/Description.html#//apple_ref/occ/clm/NSBundle/mainBundle)。其他 `NSBundle` 方法在给定文件名、扩展名和（可选的）Bundle 子目录时返回 Bundle 资源的路径。获得资源的路径后，可以使用适当的类将其加载到内存中。

### 可加载的 Bundle

与应用程序 Bundle 一样，Loadable Bundle 打包可执行代码和相关资源，但你在运行时显式加载这些 Bundle。你可以使用 Loadable Bundle 来设计高度模块化、可定制和可扩展的应用程序。每个 Loadable Bundle 都有一个主类（principal class），它是 Bundle 的入口点；当你加载 Bundle 时，你必须向 `NSBundle` 请求 principal class 并使用返回的 `Class` 对象来创建该类的实例。

---

### 相关

#### 前提文章

* [Message](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Message.html#//apple_ref/doc/uid/TP40008195-CH59-SW1)

#### 相关文章

- [Property list](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/PropertyList.html#//apple_ref/doc/uid/TP40008195-CH44-SW1)
- [Nib file](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/NibFile.html#//apple_ref/doc/uid/TP40008195-CH34-SW1)

#### 最终讨论

* [About Bundles](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/AboutBundles/AboutBundles.html#//apple_ref/doc/uid/10000123i-CH100)

