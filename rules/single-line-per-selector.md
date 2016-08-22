# 每个选择器单独成行

`single-line-per-selector` 规则会强制选择器是否应该被放置在新的一行。

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo,
.bar {
  content: 'baz';
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo, .bar {
  content: 'baz';
}
```
