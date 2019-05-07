# CSS 动画

## 简介

近期在支持其他项目的动画动效开发中，发现 css 动画属性基本忘记得七七八八八了。翻阅网上资料复习，发现动画的几个属性十分容易混淆，难以记住，为此做个记录以便区分。主要涉及 **transform**、 **transition** 、**animation** 几个属性，下面我们一一详细讲述其含义及作用。此次开发的效果图录制成 GIF 如下。

![Img](./doc/index.gif)

不得不说我们设计小姐姐真是强大，设计出来的图就是那么好看（五体投地的佩服。欢迎大家窥视我方小姐姐们的设计作品！ **[meetyou_ued](https://myued.zcool.com.cn/)**

## 易混淆的属性

| 属性              | 含义                                                                     |
| ----------------- | ------------------------------------------------------------------------ |
| animation（动画） | 用于设置六个动画属性，是一个简写属性                                     |
| transtion（过渡） | 当元素从一种样式变换为另一种样式时为元素添加效果，与 animation 类似      |
| transform（变形） | 向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜 |
| translate（移动） | transform 的一个属性（移动）。与上述几个属性长的比较相似，特意拿出来区分         |

## Transtion

transtion 是在样式变化时为其添加一个过渡的动画效果，通常情况下，CSS 属性变化是立即生效的，在极短的时间内替换为另一种样式。大部分情况下如果不增加过渡效果的话，会显得特别的突兀。实例代码如下：

``` SCSS
.el-button {
  width: 320px;
  height: 36px;
  border: none;
  color: #fafafa;
  border-radius: 3px;
  // hover状态下更改的有 background、box-shadow
  transition: all .5s; 
  background: rgba(245, 245, 245, 1);
  box-shadow: 0 8px 15px rgba(255, 116, 185, 0.25);
  &:hover {
    box-shadow: 0 8px 15px rgba(255, 116, 185, 0.25),
      0 8px 15px rgba(255, 116, 185, 0.25);
    background-image: -webkit-linear-gradient(
      180deg,
      rgb(199, 43, 255) 0%,
      rgb(254, 95, 201) 100%
    );
  }
}
```

### transiton 属性

transiton 有四个属性：

- transition-property : 规定应用过渡的 CSS 属性的名称。
- transition-duration : 定义过渡效果花费的时间。默认是 0。
- transition-timing-function : 规定过渡效果的时间曲线。默认是 "ease"。
- transition-delay : 规定过渡效果何时开始。默认是 0。

可简写为：

```css
  transition: <property> <duration> <timing-function> <delay>  
```

#### all

transition-property 有个 all 的属性值，它对应选择器下的元素的所有 CSS 属性生效，无论在哪里声明的 CSS 规则，并不局限于在同个代码块下。

不同属性对应不同的效果，all必须放在最前面：

```css
.demo {
  transition-property: all, border-radius, opacity;
  transition-duration: 1s, 2s, 3s;
  /* 当这样使用时，确保 all 在第一个，因为如果 all 在后边的话，它的规则会覆盖掉前边的属性 */
}
```

！注：关于 transition-timing-function 的各个算法的变化曲线可使用 chrome 开发者工具查看。

## Transform

## Animation
