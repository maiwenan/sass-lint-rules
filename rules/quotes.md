# 引号

`quotes` 规则会强制对所有字符串使用单引号 (`''`) 或者双引号 (`""`) 。

## 可选的配置参数

* `style`: `single`/`double` (默认为 `single`)

## 例子

设置为 `style:single` 时，下面的写法是被允许的。设置为 `style: double` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'bar';
}
```

设置为 `style:double` 时，下面的写法是被允许的。设置为 `style: single` 时，下面的写法是不被允许的。

```scss
.foo {
  content: "bar";
}
```
