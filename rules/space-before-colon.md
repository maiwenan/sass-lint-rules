# 冒号前面的空格

`space-before-colon` 规则会强制一个空格是否应该被包含在一个冒号 (`:`) 的前面。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `false`)

## 例子

设置为 `include: false` 时，下面的写法是被允许的。设置为 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'bar';
}
```

设置为 `include: true` 时，下面的写法是被允许的。设置为 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  content :'bar';
}
```
