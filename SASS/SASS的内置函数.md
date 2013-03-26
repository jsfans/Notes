# SASS 的内置函数
------

SASS 提供了一系列的内置函数以便于代码的阅读和对其进行维护。

这些内置函数在 SASS 运行的时候作为一个模块引入，可以被 SassScript 上下文自由调用，如下代码会调用函数 `Sass::Script::Functions#hsl` 并返回一个颜色值赋给变量 `$color`：

	$color: hsl(120deg, 100%, 50%);

如果想了解内置函数的实现，可以在 sass 的安装目录中找到 functions.rb 查看：

C:\Ruby192\lib\ruby\gems\1.9.1\gems\sass-3.2.3\lib\sass\script\functions.rb。

下面就来介绍一下这些内置函数。

## RGB 函数

### rgb($red, $green, $blue)

返回一个[SassScript颜色对象][SASS Color Object]，该对象由一个红绿蓝色值的有序三元组转换而成，内部以 RGBA 表现。

> 一个颜色的 alpha 值一定会被储存，默认值为1。alpha 通道相对独立于颜色本身的 RGB 或 HSL 表现。只对 alpha 值做修改并不影响缓存的 RGB 或 HSL 的值

#### 接受参数：

*   (Number) $red - 数字 [0~255 | 0%~100%]
*   (Number) $green - 数字 [0~255 | 0%~100%]
*   (Number) $blue - 数字 [0~255 | 0%~100%]

#### 示例：

	$red: rgb(255, 0, 0); // 纯红
	$green: rgb(0, 100%, 0); // 纯绿

### rgba($red, $green, $blue, $alpha)

### rgba($color, $alpha)

### red($color)

### green($color)

### blue($color)

### mix($color-1, $color-2, [$weight])

## HSL 函数

### hsl($hue, $saturation, $lightness)

### hsla($hue, $saturation, $lightness, $alpha)

### hue($color)

## 透明度函数
## 其他颜色函数
## 字符串函数
## 数字函数
## 列表函数
## 内置工具函数
## 其他函数

官方链接：[Sass::Script::Functions][SASS Functions]

[SASS Functions]: http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html
[SASS Color Object]: http://sass-lang.com/docs/yardoc/Sass/Script/Color.html