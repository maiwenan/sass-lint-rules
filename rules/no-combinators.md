# 进制关系选择器

`no-combinators` 规则会对关系选择器的使用进行警告。

## 例子

当启用时，下面的写法是不被允许的:

```scss
.foo > .bar {
  content: 'foo';
}

.foo ~ .bar {
  content: 'bar';
}

.foo + .bar {
  content: 'baz';
}

.foo .bar {
  content: 'qux';
}
```
