## 配置 Web 应用

web 应用在设计上，无论是外观还是交互方面都更接近原生应用。例如，iOS 上会通过缩放来适应整个屏幕。你还可以进一步订制化，使用一些基于 iOS 的设置，在用户把应用添加到桌面时，让它看起来更像一个原生应用程序。

例如，为 web 应用设置一个桌面图标，设置 Safari 界面样式等。

### 设置图标

用户可以把你的 web 应用或者链接添加到桌面。这些用图标来表示的链接也叫 web 书签。

* 在根目录放置一个名为 apple-touch-icon.png 的 PNG 格式的图标文件，可以给整个网站设置图标
* 如果要为某个页面设置图标，可以在该页面添加一个 link 元素：

```html
<link rel="apple-touch-icon" href="/custom_icon.png" />
```

* 为了支持 iPhone 和 iPad 设备，可以为不同的分辨率设置不同的图标，添加 sizes 属性到每一个 link 元素：

```html
<link rel="apple-touch-icon" href="touch-icon-iphone.png">
<link rel="apple-touch-icon" sizes="152x152" href="touch-icon-ipad.png">
<link rel="apple-touch-icon" sizes="180x180" href="touch-icon-iphone-retina.png">
<link rel="apple-touch-icon" sizes="167x167" href="touch-icon-ipad-retina.png">
```

图标将优先使用最合适的尺寸。如果没有找到匹配的尺寸，将会使用比设备推荐尺寸大的最小尺寸的图标，否则，将会使用里面最大的尺寸。

假如没有指定 link 元素，会查找网站根目录带有 apple-touch-icon 前缀的文件。例如，设备的合适尺寸为 58 x 58，那么系统将会按照这个顺序来查找：

1. apple-touch-icon-80x80.png
2. apple-touch-icon.png

> iOS 7 的 Safari 不会给图标添加效果。旧版本的 Safari 不会给带有 -precomposed.png 后缀的图标文件添加效果。

### 设置启动图

在 iOS 上，类似原生应用，你可以设置一个启动图，在应用启动的时候会显示。这个在应用离线的时候显得特别有用。默认会使用应用启动的最后一刻的截图。设置另外的启动图，添加一个 link 元素：

```html
<link rel="apple-touch-startup-image" href="/launch.png" />
```

### 设置应用标题

在 iOS 上，你可以设置一个应用标题。默认使用 <title> 标签的内容。设置一个不同的标题，可以添加一个 meta 元素：

```html
<meta name="apple-mobile-web-app-title" content="AppTitle" />
```

### 隐藏 Safari 用户界面组件

在 iOS 上，作为优化 web 应用的一部分，使用独立模式将让你的应用更接近原生。使用独立模式，Safari 将不显示浏览器顶部的地址栏和底部的按钮，只保留一个状态栏在屏幕顶部。

设置 apple-mobile-we-app-capable 的 meta 标签为 yes 将开启独立模式。

```html
<meta name="apple-mobile-web-app-capable" content="yes">
```

通过 Javascript 的只读属性 window.navigator.standalone 来判断是否开启了独立模式。

### 修改状态栏样式

独立模式下，你可以修改屏幕顶部的状态栏样式。可以使用 status-bar-style 的 meta 标签来进行设置。

这个 meta 标签只在独立模式下有效。使用 apple-mobile-web-app-status-bar-style 设置状态栏的样式。举个例子，假如你想全屏显示，可以设置状态栏样式为 translucent。

下面的代码将设置状态栏颜色为黑色：

```html
<meta name="apple-mobile-web-app-status-bar-style" content="black">
```

### 跳转到其他原生应用

可以通过一个特殊的链接跳转到 iOS 上其他内建的原生应用。例如拨打电话、发送邮件和 iMessage，打开 YouTobe 视频软件等。拨打电话，你可以为 anchor 元素添加以下的链接：

```html
<a href="tel:1-408-555-5555">Call me</a>
```





