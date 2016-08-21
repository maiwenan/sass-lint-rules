# 禁止使用继承

`no-extends` 规则会强制不能使用继承。

## 例子

当启用时，下面的写法是不被允许的:

```scss
.foo {
  @extend %bar;
  @extend .bar;
  @extend #bar;
}
```
