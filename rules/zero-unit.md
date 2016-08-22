# 值为 0 的单位

`zero-unit` 规则会强制长度为 `0` 是否应该不使用单位。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `false`)

## 例子

设置为 `include: false` 时，下面的写法是被允许的。设置为 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  margin: 0;
}

.bar {
  padding: 5px 0 0;
}
```

设置为 `include: true` 时，下面的写法是被允许的。设置为 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  margin: 0px;
}

.bar {
  padding: 5px 0px 0px;
}
```
