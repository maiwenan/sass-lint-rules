# 禁止行尾的空格

`no-trailing-whitespace` 规则会强制行尾不能有空格。

## 例子

当启用时，下面的写法是不被允许的 (\s 表示空格或 tab):

```scss
.foo {\s
  margin: 1.5rem;
}

.foo {
  margin: .5rem;\s
}

.foo {
  margin: .4rem;
}\s
```
