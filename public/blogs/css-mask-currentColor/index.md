# mask遮罩配合currentColor实现hover图标变色技巧

想要使用 hover 改变图标颜色，可借助 mask 遮罩搭配 `background-color: currentColor` 实现，简洁高效且易维护：

将图标设置为 mask 的值，currentColor 会自动继承当前元素的 color 值（若自身未设置 color，则自动继承父元素的值）。此时只需为元素添加 hover 状态下的 color 变色样式，即可带动图标同步变色，无需单独修改图标本身的颜色属性。

## 代码示例

```html
<div class="icon" :style="{ '--bg': `url(${item.kingKongIcon})` }"></div>
```

```css
.icon {
  width: 50px;
  height: 20px;
  mask: var(--bg); /* 复合属性建议放最上方，避免覆盖后续配置 */
  mask-size: 100% 100%;
  mask-position: center;
  mask-repeat: no-repeat;
  background-color: currentColor;
}

&:hover {
  .icon {
    color: #316edb; /* hover时改变color，图标同步变色 */
  }
}
```

## 关键注意点

mask 是 CSS 复合属性，其默认的 `mask-repeat` 值为 `repeat`，多数场景下并非所需效果。因此建议将 mask 复合属性放在样式最上方，避免后续单独设置的 `mask-repeat: no-repeat` 被覆盖，确保图标显示正常。




