# 进制属性选择器

`no-attribute-selectors` 规则会对属性选择器的使用进行警告。

## 例子

当启用时，下面的写法是不被允许的:

```scss
[autoplay] {
  content: 'foo';
}

[lang=en] {
  content: 'bar';
}

[lang~=en-us] {
  content: 'baz';
}

[lang|=us] {
  content: 'qux';
}

[href^="#"] {
  content: 'norf';
}

[href$=".com"] {
  content: 'foo';
}

[href*=news] {
  content: 'bar';
}
```
