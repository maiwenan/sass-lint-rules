# 每行只能有一个样式声明

`one-declaration-per-line` 规则会强制心得样式声明必须在心的一行开始。

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo {
  content: 'baz';
  content: 'qux';
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo {content: 'baz', content: 'qux'};

.foo {
  content: 'baz'; content: 'qux';
}
```
