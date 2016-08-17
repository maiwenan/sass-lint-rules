# 空白的参数列表

当声明或者调用一个 `mixin` 的时候，如果没有定义任何参数或者没有使用任何参数，`empty-args` 规则会强制是否包含括号。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `false`)

## 例子

设置 `include: false` 时，下面的写法是被允许的。设置 `include: true` 时，下面的写法是不被允许的。

```scss
@mixin bar {
  padding: 10px;
}

.bar {
  @include bar;
}
```

设置 `include: true` 时，下面的写法是被允许的。设置 `include: false` 时，下面的写法是不被允许的。

```scss
@mixin foo() {
  padding: 10px;
}

.foo {
  @include foo();
}
```