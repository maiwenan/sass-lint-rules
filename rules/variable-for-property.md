# 为属性使用变量

`variable-for-property` 规则会强制对指定的属性要使用变量作为值。
默认情况下是没有指定的属性，除了下面列出来的预留的词组，他们总是处于白名单中。
* inherit
* initial
* transparent
* none
* currentColor

使用 `!important` 标识符时也总是例外的。

## 可选的配置参数

* `properties`: `[一组属性名称组成的数组]` (默认为空白数组 `[]`)

你可以传递一组你希望强制使用变量作为值的属性

```yaml

variable-for-property:
  - 1
  -
    'properties':
    - 'margin'
    - 'content'
```

## 例子

默认情况下， `properties` 时一个空数组，因此没有属性是被强制要使用变量作为属性的。

当 `properties` 包含上面例子那一节所示的属性时，下面的写法是不被允许的:

```scss
.bar {
  content: ' ';
  margin: 0;

  &__element {
    margin: 0;
  }
}

@mixin red() {
  margin: 0;
}
```

当 `properties` 包含上面例子那一节所示的属性时，下面的写法是被允许的:

```scss
.foo {
  content: $content;
  margin: $margin;

  &__element {
    margin: $margin;
  }
}

@mixin blue() {
  margin: $margin;
}

```

`!important` 标识符会被任何 lint 警告排除开。

例如如果 `properties` 包含了 `color` 这个属性，下面的写法是不被允许的:

```scss
.foo {
  color: red !important;
}
```

下面的写法是被允许的:

```scss
.foo {
  color: $red-var !important;
}
```
