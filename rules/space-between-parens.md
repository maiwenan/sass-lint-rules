# 括号之间的空格

`space-between-parens` 规则会强制一个空格是否应该被包含在括号 (`()`) 里面第一个元素的前面和最后一个元素的后面。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `false`)

## 例子

设置为 `include: false` 时，下面的写法是被允许的。设置为 `include: true` 时，下面的写法是不被允许的。

```scss
@function foo($bar) {
  @return $bar;
}

@mixin bar($baz) {
  content: $baz;
}

.foo {
  @include bar('Hello');
  content: foo('bar');
  width: calc(100% - 10px);
}
```

设置为 `include: true` 时，下面的写法是被允许的。设置为 `include: false` 时，下面的写法是不被允许的。

```scss
@function foo( $bar ) {
  @return $bar;
}

@mixin bar($baz ) {
  content: $baz;
}

.foo {
  @include bar( 'Hello' );
  content: foo( 'bar');
  width: calc( 100% - 10px);
}
```
