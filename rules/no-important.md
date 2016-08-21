# 禁止使用 `!important`

`no-important` 规则会强制禁止使用 `important` 声明。

## 例子

当启用时，下面的写法是不被允许的:

```scss
.foo {
  content: 'bar' !important;
}
```
