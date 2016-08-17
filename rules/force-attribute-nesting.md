# 强制属性选择器嵌套

`force-attribute-nesting` 规则会强制属性选择器进行嵌套书写。

## 例子

当启用时，下面的写法是不被允许的:

```scss
input[type='radio'] {
  color: red;
}

a[target='_blank'] {
  content: '';
}

.form {
  .class input[type='text'] {
    padding: 0;
  }
}
```

当启用时，下面的写法是被允许的:

```scss
input {
  &[type='radio'] {
    color: red;
  }
}

a {
  &[target='_blank'] {
    content: '';
  }
}

.form {
  .class input {
    &[type='text'] {
      padding: 0;
    }
  }
}
```
