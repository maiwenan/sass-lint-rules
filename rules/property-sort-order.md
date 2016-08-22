# 属性排序顺序

`property-sort-order` 规则会强制样式声明要按顺序书写。

## 可选的配置参数

* `order`: `'alphabetical'`, [`'concentric'`](http://rhodesmill.org/brandon/2011/concentric-css/), [`'recess'`](http://twitter.github.io/recess/), [`'smacss'`](http://smacss.com/book/formatting), or `[属性组成的数组]` (默认为 `alphabetical`. 未知的属性是按照字母排序的)
* `ignore-custom-properties`: `true`/`false` (默认为 `false`)

属性顺序: https://github.com/sasstools/sass-lint/tree/develop/lib/config/property-sort-orders

## 例子

当启用时，（假设设置为 `order: alphabetical`），下面的写法是被允许的:
When enabled (assuming `order: alphabetical`), the following are allowed:

```scss
.foo {
  content: 'baz';
  height: 100vh;
  width: 100vw;
}
```

当启用时，（假设设置为 `order: alphabetical`），下面的写法是不被允许的:

```scss
.foo {
  width: 100vw;
  height: 100vh;
  content: 'baz';
}
```

### 自定义排序顺序

你拥有创建你自己的排序顺序的选择。这些自定义的排序指定在你的 `.sass-lit.yml` 文件如下所示:

```yaml
property-sort-order:
  - 1
  -
    order:
      - border
      - display
      - color
```

当自定义的排序像上面那样被指定时，下面的写法是被允许的:

```scss
.foo {
  border: 1px solid blue;
  display: block;
  color: red;
}
```

当自定义的排序像上面那样被指定时，下面的写法是不被允许的:

```scss
.foo {
  display: block;
  color: red;
  border: 1px solid blue;
}
```

### 忽略自定义属性

当设置 `ignore-custom-properties: false` （假设 `order: 'alphabetical'`），下面的写法是被允许的。

```scss
.foo {
  border: 1px solid blue;
  color: red;
  composes: heading;
  display: block;
}
```

当设置 `ignore-custom-properties: false` （假设 `order: 'alphabetical'`），下面的写法是不被允许的。

```scss
.foo {
  composes: heading; // not in alphabetical order
  border: 1px solid blue;
  color: red;
  display: block;
}
```

当设置 `ignore-custom-properties: true` （假设 `order: 'alphabetical'`），下面的写法是被允许的。

```scss
.foo {
  composes: heading; // 自定义属性被忽略掉
  border: 1px solid blue;
  color: red;
  display: block;
}
```
