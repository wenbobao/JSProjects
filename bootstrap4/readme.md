禁用缩放功能，用户只能滚动屏幕，让你的网站看上去更像原生应用的感觉。

```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```

## 布局容器

Bootstrap 需要为页面内容和栅格系统包裹一个 .container 容器。

`.container`类用于固定宽度并支持响应式布局的容器。

```
<div class="container">
  ...
</div>
```

`.container-fluid` 类用于 100% 宽度，占据全部视口（viewport）的容器。

```
<div class="container-fluid">
  ...
</div>
```

## 网格系统

* .col- 针对所有设备
* .col-sm- 平板 - 屏幕宽度等于或大于 576px
* .col-md- 桌面显示器 - 屏幕宽度等于或大于 768px)
* .col-lg- 大桌面显示器 - 屏幕宽度等于或大于 992px)
* .col-xl- 超大桌面显示器 - 屏幕宽度等于或大于 1200px)

列偏移 `offset-md-4`

## 文字排版

Bootstrap4 默认`font-size`为16px, `line-height`为1.5, 默认的 `font-family` 为 "Helvetica Neue", Helvetica, Arial, sans-serif。

<p> 元素 margin-top: 0 、 margin-bottom: 1rem (16px)。