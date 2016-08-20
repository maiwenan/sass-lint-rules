# 禁止颜色值关键字

`no-color-keywords` 规则会强制使用十六进制的颜色值而不是颜色的字面值。

## 例子

当启用时，下面的写法是被允许的:

```scss
$new-red: #ff0000;

.foo {
  color: #ff0000;
}

```

当启用时，下面的写法是不被允许的:

```scss
$new-red: red;

.foo {
  color: red;
}
```
