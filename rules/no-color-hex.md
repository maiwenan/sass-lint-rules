# 禁止使用十六进制的颜色值

`no-color-hex` 规则会强制禁止使用十六进制的颜色值。

## 例子

当启用时，下面的写法是不被允许的:

```scss
$foo-color: #456;

.bar {
  background: linear-gradient(top, #3ff, #ddd);
}

.baz {
  color: #fff;
}
```

当启用时，下面的写法是被允许的:

```scss
$foo-color: red;

.bar {
  background: linear-gradient(top, blue, green);
}

.baz {
  color: white;
}
```
