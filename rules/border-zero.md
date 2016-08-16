# 零宽度边框

在指定 `border` 的值为零时，`border-zero` 规则会强制要么使用 `0` ，要么使用 `none`

## 可选的配置参数

* `convention`: `'0'`/`'none'` (默认为 ``)

## 例子

设置为 `convention: '0'` 时，下面写法是被允许的。设置为 `convention: 'none'` 时，下面写法是不被允许的。

```scss
.foo {
  border: 0;
}

.bar {
  border-right: 0;
}
```

设置为 `convention: 'none'` 时，下面写法是被允许的。设置为 `convention: '0'` 时，下面写法是不被允许的。

```scss
.foo {
  border: none;
}

.bar {
  border-left: none;
}
```