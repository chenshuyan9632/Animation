# CSS 动画

## 使用

    parcel index.html


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

transfrom 主要是控制元素变形，并没有一个时间控制的概念。主要是对元素进行移动、缩放、转动、拉长或拉伸，其提供了2D、3D转换。语法如下：

```css
  transform: translate(30%, -15%);
```

### transform 的属性

- matrix ：矩阵转换。
- translate : 移动元素。
- scale : 缩放元素。
- rotate : 旋转角度。
- skew : 倾斜转换。

！注：3d转换的属性名略有不同，但是含义相同。
  
## Animation

animation，相对于 transiton 实现了控制多个状态的变化。animation 的实现依赖 @keyframes 来定义动画效果，@keyframes 定义的规则可以用来控制动画过程中的各个状态的情况，语法大致如下：

```css
@keyframes paneA {
  0% {
    transform: translate(30%, -15%);
    opacity: 0;
  }
  25% {
    transform: translate(0%, 0%);
    opacity: 1;
  }
}
```

### animation 属性

- animation-name : 规定 @keyframes 动画的名称。
- animation-iteration-count ：规定动画被播放的次数。默认是 1。
- animation-direction ：规定动画是否在下一周期逆向地播放。默认是 "normal"。
- animation-play-state ： 规定动画是否正在运行或暂停。默认是 "running"。
- animation-fill-mode ：规定对象动画时间之外的状态。
- animation-duration、animaiton-delay、animation-timing-function: 与 transiton 的类似，分别为持续时间、延迟时间、变化估计算法。

可简写为：

```css
  animation: <duration> <timing-function> <delay> <iteration-count> <direction> <fill-mode> <play-state> <name>
```

#### display

如果一个元素的 display 设置为 none，那么在它或者它的子元素上的动画效果便会停止，而重新设置 display 为可见后，动画效果会重新重头开始执行。

#### 多个动画的顺序

animation-name 是可以指定多个动画效果的，所以会出现动画的一个顺序问题。后指定的动画会覆盖掉前边的：

```css
#colors {
  animation-name: red, green, blue; /* 假设这些 keyframe 都是修改 color 这个属性 */
  animation-duration: 5s, 4s, 3s;
}
```

### 参考

- http://www.w3school.com.cn/css3/index.asp
- https://segmentfault.com/a/1190000006699023
