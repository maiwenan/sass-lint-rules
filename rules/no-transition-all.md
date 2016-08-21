# 禁止使用 `transition` 属性使用 `all` 作为值

`no-transition-all` 规则会强制 `all` 关键字是否能和 `transition` 属性或者 `transition-property` 属性一起使用。

## 例子

下面的写法是不被允许的:

```scss
.foo {
  transition: all 2s;
}

.bar {
  transition-property: all 2s;
}

.quz {
  -webkit-transition: all 2s, height 2s, background-color 2s, -webkit-transform 2s;
}
```
