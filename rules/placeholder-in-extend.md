# 继承中只能使用占位符

`placeholder-in-extend` 规则会强制在继承中只能包含占位符选择器。

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo {
  @extend %bar;
  @extend .baz%qux;
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo {
  @extend .bar;
  @extend #baz;
}
```
