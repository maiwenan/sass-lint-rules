# 文件以新的一行结尾

`final-newline` 规则会强制文件是否应该以新的一行结尾。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `true`)

## 例子

设置 `include: true` 时，下面的写法是被允许的。设置 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'bar';
}
// 该注释下有新的空行

```

设置 `include: false` 时，下面的写法是被允许的。设置 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'bar';
}
// 该注释下没有新的空行
```
