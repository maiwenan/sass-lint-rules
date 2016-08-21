# 禁止限定元素

`no-qualifying-elements` 规则会强制选择器不能有限定元素（qualifying elements）。

## 可选的配置参数

* `allow-element-with-attribute`: `true`/`false` (默认为 `false`)
* `allow-element-with-class`: `true`/`false` (默认为 `false`)
* `allow-element-with-id`: `true`/`false` (默认为 `false`)

## 例子

默认的情况下，下面的写法是不被允许的:

```scss
div.foo {
  content: 'foo';
}

ul#foo {
  content: 'foo';
}

input[type='email'] {
  content: 'foo';
}
```

### `allow-element-with-attribute`

当设置 `allow-element-with-attribute: true` 时，下面的写法是被允许的。当设置 `allow-element-with-attribute: false` 时，下面的写法是不被允许的。

```scss
input[type='email'] {
  content: 'foo';
}

a[href] {
  content: 'foo';
}
```

### `allow-element-with-class`

当设置 `allow-element-with-class: true` 时，下面的写法是被允许的。当设置 `allow-element-with-class: true` 时，下面的写法是不被允许的。

```scss
div.foo {
  content: 'foo';
}

h1.bar {
  content: 'foo';
}
```

### `allow-element-with-id`

当设置 `allow-element-with-id: true` 时，下面的写法是被允许的。当设置 `allow-element-with-id: true` 时，下面的写法是不被允许的。

```scss
ul#foo {
  content: 'foo';
}

p#bar {
  content: 'foo';
}
```
