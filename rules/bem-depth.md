# BEM 深度

`bem-depth` 规则会强制一个 `BEM` 类能够包含多少个元素。

## 可选的配置参数

* `max-depth`: number (默认为 `1`)

## 例子

当设置该参数时(假设为 `max-depth: 1`)，下面的写法是不被允许的。

```scss

.block {
  &__element {
    &__subelement {
      // two elements
    }
  }
}

.block__element__subelement__subelement-two {
  // three elements
}
```