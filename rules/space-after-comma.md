# 逗号后面的空格

`space-after-bang` 规则会强制一个空格是否应该被包含在一个逗号 (`,`) 后面。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `true`)

## 例子

设置为 `include: true` 时，下面的写法是被允许的。设置为 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  @include baz('foo', 'bar');

  box-shadow: 1px 1px black, 1px 1px black;
}
```

设置为 `include: false` 时，下面的写法是被允许的。设置为 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  @include baz('foo','bar');

  box-shadow: 1px 1px black,1px 1px black;
}
```
