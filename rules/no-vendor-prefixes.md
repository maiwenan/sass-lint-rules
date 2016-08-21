# 禁止浏览器前缀

`no-vendor-prefixes` 规则会强制禁止使用浏览器前缀。

默认情况下，下面列出的前缀都会被影响:
* webkit
* moz
* ms

## 可选的配置参数

* `additional-identifiers`: `[需要检测的额外的前缀组成的数组]` (默认为空数组 `[]`)
* `excluded-identifiers`: `[不需要检测的前缀组成的数组]` (默认为空数组 `[]`)
* `ignore-non-standard`: `true`:`false` (默认为 `false`)

## 例子

当启用时，下面的写法是不被允许的:
When enabled, the following are disallowed:

```scss
@-webkit-keyframes anim {
  0% { opacity: 0; }
}

.ms-block {
  -ms-hyphenate-limit-lines: no-limit;
}

::-moz-placeholder {
  content: '';
}

.foo {
  -webkit-transition: none;
}

.bar {
  position: -moz-sticky;
}
```

### 额外的标识符

当设置 `additional-identifiers` 包含一个自定义的前缀 `khtml` 时，如下面所示:

```yaml
no-vendor-prefixes:
  - 1
  -
    additional-identifiers:
      - khtml
```

下面的写法现在是不被允许的:

```scss
.baz {
  position: -khtml-sticky;
}
```

### 不包含的标识符

当设置 `excluded-identifiers` 包含现在不被允许的前缀值，如 `webkit` 和 `moz` 时，如下面所示:

```yaml
no-vendor-prefixes:
  - 1
  -
    excluded-identifiers:
      - webkit
      - moz
```

下面的写法现在是被允许的:

```scss
@-webkit-keyframes anim {
  0% { opacity: 0; }
}

::-moz-placeholder {
  content: '';
}

.foo {
  -webkit-transition: none;
}

.bar {
  position: -moz-sticky;
}
```

下面的写法依然是不被允许的:

```scss

.ms-block {
  -ms-hyphenate-limit-lines: no-limit;
}
```

### 忽略非标准的属性

`ignore-non-standard` 是一个允许你指定是只有标准的来自我们的[属性列表](https://github.com/sasstools/sass-lint/blob/master/data/properties.yml)的属性应该被这条规则影响到，或者是人和有前缀的属性或者元素都会被影响到。

当设置 `ignore-non-standard: false` 时，下面的写法是不被允许的。当设置 `ignore-non-standard: true` 时，下面的写法是被允许的:

```scss

html {
  -webkit-tap-highlight-color: $link-color-hover;
}

button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}

input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
```
