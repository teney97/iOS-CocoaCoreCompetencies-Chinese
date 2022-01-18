## 信息属性列表 (Info.plist)

原文：[Information property list](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/InfoPlist.html#//apple_ref/doc/uid/TP40008195-CH61-SW1)

信息属性列表是结构化文本，用于指定应用程序或其他捆绑可执行文件的配置详细信息。操作系统在运行时从信息属性列表中提取数据，并以适当的方式处理它。例如，当它们（操作系统）在主屏幕或 Finder 中列出应用程序时，iOS 和 OS X（分别）会从已安装应用程序的信息属性列表中获取这些名称。

信息属性列表的内容以一种特殊形式的 XML 构成，其中根节点始终是一个字典。字典包含一系列键值对或属性。

![](https://gitee.com/junteng/images/raw/master/img/20220114124922.png)

这是一个键值对示例：

```xml
<key>CFBundleDisplayName</key>
<string>Mail</string>
```

信息属性列表中指定的属性包括 bundle display name、bundle identifier、bundle icon、bundle version、supported platforms 和 document types 等等。

信息属性列表文件的命名必须为 `Info.plist`，注意大小写。文件中的文本采用 Unicode UTF-8 编码。当你构建一个应用程序或其他 bundle 时，该文件被放在 bundle 中的某个位置。

当你使用 Xcode（主要的开发应用程序）为一个应用程序或其他 bundle 创建一个项目时，Xcode 会在项目的 Resources 文件夹下创建一个名为 `ProjectName-Info.plist` 的文件。（当你构建你的项目时，就会将这个文件复制到 bundle 中，并命名为 `Info.plist`。）Xcode 为你在 `ProjectName-Info.plist` 中配置了一些属性，但你经常需要指定额外的属性。你可以在 Xcode 的编辑器中直接选择文件来编辑信息属性列表，还可以在 target inspector 的 Properties 面板中编辑一些属性。

---

### 相关

#### 前提文章

* [Property list](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/PropertyList.html#//apple_ref/doc/uid/TP40008195-CH44-SW1)
* [Bundle](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Bundle.html#//apple_ref/doc/uid/TP40008195-CH4-SW1)

#### 相关文章

None

#### 最终讨论

* *[Information Property List Key Reference](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009247)*

