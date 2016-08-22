# 操作符中的空格

`space-around-operator` 规则会强制一个空格是否应该被包含在下面操作符的前面和后面:`+`, `-`, `/`, `*`, `%`, `<`, `>` `==`, `!=`, `<=` and `>=`。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `true`)

## 例子

设置为 `include: true` 时，下面的写法是被允许的。设置为 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  margin: 5px + 15px;
}

$foo: 1;
$bar: 3;

.foo {
  margin: $foo + $bar + 'px';
}

$foo: 1 + 1;
$bar: 2 - 1;

@if $foo == $bar {
  $baz: 1;
}

@if ($foo != $bar) {
  $baz: 1;
}
```

设置为 `include: false` 时，下面的写法是被允许的。设置为 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  margin: 5px+15px;
}

$foo: 1;
$bar: 3;

.foo {
  margin: $foo+$bar+'px';
}

$foo: 1+1;
$bar: 2-1;

@if $foo==$bar {
  $baz: 1;
}

@if ($foo!=$bar) {
  $baz: 1;
}
```
设置为 `include: true` 或者 `include: false` 时，多个空格在操作符的周围是不被允许的:

```scss
.foo {
  margin: 5px   +       15px;
}

$foo: 1      +1;
$bar: 2-     1;
```
