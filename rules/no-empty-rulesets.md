# 禁止空白的样式规则集

`no-empty-rulesets` 规则会禁止空白的样式规则集。

## 例子

当启用的时，下面的写法是不被允许的:

```scss
.foo {

}

.bar {
  content: 'baz';

  .qux {}
}

.waldo {}
```
