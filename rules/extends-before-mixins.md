# 在使用 `mixin` 前进行继承

`extends-before-mixins` 会强制在一组样式规则中，继承应该是要在使用 `mixin` 之前书写的。

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo {
  @extend %bar;
  @include baz;
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo {
  @include baz;
  @extend %bar;
}
```
