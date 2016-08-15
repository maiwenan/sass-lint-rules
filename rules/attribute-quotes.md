# 属性值的引号

`attribute-quotes` 规则会强制在属性值中使用引号。

## 可选的配置参数

* `include`: `true`/`false` (默认为 `true`)

## 例子

### `include`

设置为 `include: true` 时，下面写法是被允许的。设置为 `include: false` 时，下面写法是不被允许的。

```scss

span[lang="pt"] {
	color: green;
}

span[lang~="en-us"] {
  color: blue;
}

span[class^="main"] {
  background-color: yellow;
}

a[href*="example"] {
  background-color: #CCCCCC;
}

input[type="email" i] {
  border-color: blue;
}
```

设置为 `include: false` 时，下面写法是被允许的。设置为 `include: true` 时，下面写法是不被允许的。
```scss

span[lang=pt] {
  color: green;
}

span[lang~=en-us] {
  color: blue;
}

span[class^=main] {
  background-color: yellow;
}

a[href*=example] {
  background-color: #CCCCCC;
}

input[type=email i] {
  border-color: blue;
}
```