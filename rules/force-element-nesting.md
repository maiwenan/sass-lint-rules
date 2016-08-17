# 强制元素选择器嵌套

`force-element-nesting` 规则会强制元素选择器进行嵌套书写。

## 例子

当启用时，下面的写法是不被允许的:

```scss
div p {
  content: '';
}

.parent {
  &__child h1 {
    content: '';
  }
}

a[target="_blank"] span {
  content: '';
}
```

当启用时，下面的写法是被允许的:

```scss
div {
  p {
    content: '';
  }
}

.parent {
  &__child {
    h1 {
      content: '';
    }
  }
}

a[target="_blank"] {
  span {
    content: '';
  }
}
```
