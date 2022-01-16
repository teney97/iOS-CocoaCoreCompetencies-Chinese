## App ID

原文：[App ID](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/AppID.html#//apple_ref/doc/uid/TP40008195-CH64-SW1)

App ID 是一个由两部分组成的字符串，用于标识来自单个开发团队的一个或多个应用程序。该字符串由一个 *Team ID* 和一个 *Bundle ID search string* 组成，两个部分之间用句号 (`.`) 分隔。Team ID 是由 Apple 提供的，对于特定的开发团队来说是唯一的，而 Bundle ID search string 是由你提供的，用来匹配单个或一组应用程序的 Bundle ID。

![](https://gitee.com/junteng/images/raw/master/img/20220116033847.png)

有两种类型的 App ID：

* Explicit App ID，用于单个应用程序
* Wildcard App IDs，用于一组应用程序

---

### 一个 Explicit App ID 匹配单个应用

对于与应用程序匹配的 Explicit App ID，App ID 中的 Team ID 必须等于与应用程序关联的 Team ID，并且 Bundle ID search string 必须等于应用程序的 Bundle ID。Bundle ID 是标识单个应用程序的唯一标识符，其他团队无法使用。

### Wildcard App IDs 匹配多个应用

Wildcard App ID 包含一个星号 (`*`) 作为其 Bundle ID search string 的最后一部分。星号 (`*`) 替换 Bundle ID search string 中的部分或全部。

![](https://gitee.com/junteng/images/raw/master/img/20220116034454.png)

在将 Bundle ID search string 与 Bundle ID 匹配时，星号 (`*`) 被视为通配符（wildcard）。对于要匹配一组应用程序的 Wildcard App ID，Bundle ID 必须与 Bundle ID search string 中星号 (`*`) 前面的所有字符完全匹配。星号 (`*`) 匹配 Bundle ID 中的所有剩余字符。星号 (`*`) 必须与 Bundle ID 中的至少一个字符匹配。下表显示了 Bundle ID search string 以及一些匹配和不匹配的 Bundle ID。

| com.domain.*             |                                                              | (bundle id search string)                        |
| :----------------------- | :----------------------------------------------------------- | :----------------------------------------------- |
| com.domain.text          | ![](https://gitee.com/junteng/images/raw/master/img/20220116035216.png) | * matches text.                                  |
| com.domain.icon          | ![](https://gitee.com/junteng/images/raw/master/img/20220116035216.png) | * matches icon                                   |
| com.otherdomain.database | ![](https://gitee.com/junteng/images/raw/master/img/20220116035231.png) | The d in the pattern fails to find a match.      |
| com.domain               | ![](https://gitee.com/junteng/images/raw/master/img/20220116035231.png) | The . in the pattern fails to find a match.      |
| com.domain.              | ![](https://gitee.com/junteng/images/raw/master/img/20220116035231.png) | The * in the pattern fails to match a character. |

对于要匹配应用程序的 Wildcard App ID，Team ID 必须完全匹配，并且 Bundle ID 必须使用通配符匹配规则匹配 Bundle ID search string。

---

### 相关

#### 相关文章

None

#### 最终讨论

* *App Distribution Guide*