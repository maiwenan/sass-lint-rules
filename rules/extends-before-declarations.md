# 在声明前进行继承

`extends-before-declarations` 规则会强制在一组样式规则中，继承应该是要在声明之前书写的
Rule `extends-before-declarations` will enforce that extends should be written before declarations in a ruleset.

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo {
  @extend %bar;
  content: 'baz';
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo {
  content: 'baz';
  @extend %bar;
}
```
