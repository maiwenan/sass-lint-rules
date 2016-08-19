# 0 开头的小数点

`leading-zero` 规则会强制小数点数值是否应该包含 0 作为开头。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `false`)

## Examples

设置为 `include: false` 时，下面的写法是被允许的。设置为 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  font-size: .5em;
}
```

设置为 `include: true` 时，下面的写法是被允许的。设置为 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  font-size: 0.5em;
}
```
