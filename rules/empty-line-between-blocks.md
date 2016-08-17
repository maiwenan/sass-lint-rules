# 代码块之间的空白行

`empty-line-between-blocks` 规则会强制嵌套代码块是否应该包含一行在上一个非注释声明之间空白行。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `true`)
* `allow-single-line-rulesets`: `true`/`false` (默认为 `true`)

## 例子

### `include`

设置 `include: true` 时，下面的写法是被允许的。设置 `include: false` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'foo';

  .bar {
    content: 'bar';

    // Waldo
    &--baz {
      content: 'baz';
    }
  }
}
```

设置 `include: false` 时，下面的写法是被允许的。设置 `include: true` 时，下面的写法是不被允许的。

```scss
.foo {
  content: 'foo';
  .bar {
    content: 'bar';
    // Waldo
    &--baz {
      content: 'baz';
    }
  }
}
```

### `allow-single-line-rulesets`

设置 `allow-single-line-rulesets: true` 时，下面的写法是被允许的。设置 `allow-single-line-rulesets: false` 时，下面的写法是不被允许的。

```scss
.foo { content: 'foo'; }
.bar { content: 'bar'; }
.baz { content: 'baz'; }
```
