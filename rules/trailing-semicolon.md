# 行尾的分号

`trailing-semicolon` 规则会强制在一个样式块中样式声明的最后是否应该包含一个分号 (`;`) (`.sass` 语法除外)。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `true`)

## 例子

设置为 `include: true` 时，下面的写法是被允许的。设置为 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'bar';
  content: 'baz';

  .waldo {
    content: 'where';
  }
}
```

设置为 `include: false` 时，下面的写法是被允许的。设置为 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'bar';
  content: 'baz'

  .waldo {
    content: 'where'
  }
}
```
