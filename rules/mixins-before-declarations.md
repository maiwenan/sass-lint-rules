# 在声明样式属性前使用 mixin

`mixins-before-declarations` 规则会强制 mixin 应该在声明一组样式规则前使用。

## 可选的配置参数

* `exclude`: `['breakpoint', 'mq']` (一组不在这个规则约定下的 mixin 组成的数组)

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo {
  @include bar;
  content: 'baz';

  @include breakpoint(500px) {
    content: 'qux';
  }

  @include mq(500px) {
    content: 'qux';
  }
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo {
  content: 'baz';
  @include baz;
}
```
