# 禁止小数点最后的 0

`no-trailing-zero` 规则会强制小数点最后不能有 0 .

## 例子

当启用时，下面的写法是不被允许的:

```scss
.foo {
  margin: 1.500rem;
}

.foo {
  margin: .500rem;
}

.foo {
  margin: 0.2500rem;
}

.foo {
  margin: 4.0rem;
}
```
