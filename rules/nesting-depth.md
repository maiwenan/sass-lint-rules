# 嵌套深度

`nesting-depth` 规则会限制一个选择器能嵌套的最大深度（数量）。

## 可选的配置参数

* `max-depth`: number (默认为 `2`)

## 例子

当启用时（假设设置为 `max-depth: 2`），最深层的元素 (`&:hover` and `&--modifier`) 的深度为 2 。任何更深层次嵌套的选择器都是不被允许的:

```scss
.foo {
  .baz {
    &:hover {
      // Deepest Nest Allowed
    }
  }
}

.block {
  &__element {
    &--modifier {
      // Deepest Nest Allowed
    }
  }
}
```
