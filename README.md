## 配置视区

基于桌面设计的大多数 web 内容会在 iOS 的 Safari 上进行缩放显示。如果默认设置无效，可以通过修改视区的设置来调整。特别是你的网页需要适配 iOS 的情况下。视区的配置很简单，仅需要添加一行 HTML 代码，但是理解视区属性是如何影响网页在 iOS 上的显示就较为复杂。开始配置视区之前，你需要深度理解什么是可视区域和视区。

### 什么是视区？

桌面的视区和 iOS 上的视区稍微有点区别。

iOS 上的 Safari 没有窗口，滚动条或者改变大小的按钮。用户通过手指轻击来操作，通过两个手指来进行缩放操作，手势不适用于桌面端。因为交互方式的不同，桌面端和 iOS 端是不一样的。注意，这些视区之间的不同可能会影响一些 HTML 和 CSS 指令的使用。

#### Safari 桌面端视区

用户可以调整视区来调整窗口的大小。如果网页大于视区会出现滚动条。当视区改变了大小，Safari 会改变文档的布局，例如，会改变文字的宽度去适应。如果网页小于视区，会填充空白来适配视区的尺寸。

#### Safari iOS 视区

iOS 上，视区是决定内容如何布局和文字从何换行的区域。视区可以大于或者小于可视区域。

当用户平移网页，灰条会出现在右边和底部作为可视化反馈来告诉用户可视区域和视区之间的区别（类似桌面端的滚动条）。使用手势，用户可以缩放视区而不是尺寸。不一样的地方的是当用户改变方向的时候，Safari 会调整视区的宽高从而影响网页的布局。

通过设置视区的尺寸或者其他属性来改善网页在 iOS 的首屏展示。

### 视区默认设置

对于大多数的网页，iOS 会合理地设置视区的尺寸和缩放。默认宽是980像素，但是，这些默认值不一定适合，特别是对于一些特殊的设备。

### 使用视区 meta 标签

可以通过视区 meta 标签改善 web 内容的显示。一般使用视区 meta 标签来设置视区的宽度和初始缩放比。例如，网页内容比980像素要窄，你可以设置视区的宽度来适配。对于 iPhone 或者 iPod 这类触控设置，可以设置宽度为设备宽度。

因为 iOS 运行在不同分辨率的设置上，你可以使用数值常量来代表某一类设备。使用 device-width 作为设备的宽度，device-height 作为高度。

你不需要设置每一个属性。你只需要设置一部分，iOS 会推断出其他值。例如，你设置缩放比为1.0，Safari 会假设 device-width 为宽度，device-height 为高度。所以，如果你想设置980像素的宽度和1.0的初始缩放比，那么只需要设置这两个属性。

例如，设置视区宽度为设备宽度，添加如下代码：

```html
<meta name="viewport" content="width=device-width">
```

设置缩放比为1.0，添加如下代码：

```html
<meta name="viewport" content="initial-scale=1.0">
```

### 改变视区宽高

一般设置视区的宽度来匹配网页。这是你可以做的最重要的优化，确保完好的首屏显示。

网页的大部分内容都可以在980像素的可视区域展示。

如果网页比默认宽要窄，可以设置视区宽度为你网页的宽度。

```html
<meta name="viewport" content="width=590">
```

### Safari 是如何推断宽高和缩放比的

如果你只设置了一些属性，Safari 会推断出其他属性来让网页内容适配可视区域。例如，只设置初始缩放比，宽高可以推断出来。只设置宽度，那么高度和初始缩放比是推断的。如果推断值不合适会设置视区属性。

iOS 可以推断宽高和初始缩放比，当用户改变方向，视区会调整尺寸。例如，当用户通过旋转设备改变方向，视区宽度会变化。这是唯一的一种情况，视区会改变尺寸从而印象布局。

### web 应用视区设置

如果你的 web 应用基于 iOS 设计，建议的尺寸是可视区域的尺寸。苹果建议设置宽度为 device-width 而缩放比为1.0，那么改变方向，视区就不会改变大小。

设置视区宽度是首要任务，当你设计 web 应用，这样可以避免用户使用你的 web 应用之前需要先进行缩放。

你可能不希望用户进行缩放操作，可以添加如下设置来关闭用户缩放：

```html
<meta name = "viewport" content = "user-scalable=no, width=device-width">
```

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

设置 apple-mobile-web-app-capable 的 meta 标签为 yes 将开启独立模式。

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





