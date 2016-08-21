# 禁止全体选择器 (*)

`no-universal-selectors` 规则会对 `*` （全体的）选择器的使用进行警告。

## 例子

当启用时，下面的写法是不被允许的:

```scss
* {
  content: 'foo';
}

* [lang^=en] {
  content: 'bar';
}

*.warning {
  content: 'baz';
}

*#maincontent {
  content: 'qux';
}

*:before,
*:after {
  content: 'norf';
}
```
